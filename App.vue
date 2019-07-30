<template>
    <div id="app">
        <div class="header">
            <br />
            <br />
            <br />
            <h1>Fábio Dias</h1>
            <h2>Full Stack Developer</h2>
            <br />
            <br />
            <br />
            <img src="profile.jpg" class="profile" />
        </div>
        <div class="contact columns-2">
            <div class="text-right">fabio@octopuz.com.br</div>
            <div>+55 51 98466.3791</div>
        </div>

        <div class="columns-2">
            <div class="text-right">
                <strong>Born</strong>: July 6, 1985 (age 34)
            </div>
            <div>
                <i class="fas fa-map-marker-alt"></i> Viamão / RS, Brazil.
            </div>
        </div>
        <div class="columns-2">
            <div class="text-right">
                <h3>Education</h3>
            </div>
            <div>
                Escola Superior Aberta do Brasil
                <br />Informartion Systems
            </div>
        </div>
        <div class="columns-2">
            <div class="text-right">
                <h3>Social</h3>
            </div>
            <div>
                <i class="fab fa-linkedin"></i> /in/fabio-dias
                <br />
                <i class="fab fa-github"></i> /diasfs
            </div>
        </div>
        <div class="columns-2">
            <div class="text-right">
                <h3>About</h3>
            </div>
            <div>
                I work as a full stack web developer since 2009, having developed countless websites, systems and applications in this period.
                <br />
                <br />I developed my own CMS, which has been used and improved since 2012. Today I have been looking for time to rewrite it in a more modern way.
            </div>
        </div>
        <div class="columns-2">
            <div class="text-right">
                <h3>Expertise</h3>
            </div>
            <div>
                PHP, NodeJs, Javascript, Vue, Nuxt jQuery, Express.js, Mysql, MongoDb, Firebase,
                GraphQL, HTML 5, Twig, Nunjucks, Backbone.js, Less, CSS, Cordova, Webpack, Parcel,
                Rollup, Git, Linux, Bash, Apache.
            </div>
        </div>
        <div class="columns-2">
            <div class="text-right">
                <h3>Experience</h3>
            </div>
            <div>
                <strong>Full Stack Web Developer</strong>
                <br />Studio GT, Jun 2009 - Until today
                <br />
                <br />Development of websites, e-commerce, systems and mobile apps.
            </div>
        </div>
        <div class="page-break"></div>
        <div v-for="(pp, i) in projects" :key="i">
            <center style="padding: 1em;padding-top: 4em;">
                <h3>Projects</h3>
            </center>
            <div class="columns-2 projects">
                <div v-for="project in pp" :key="project.id">
                    <strong>{{ project.titulo }}</strong>
                    <br />
                    {{ project.inicio }} - {{ project.termino }}
                    <br />
                    Technologies: {{ project.tecnologias.join(', ') }}
                    <br />
                    Responsibilities: {{ project.responsabilidades }}
                </div>
            </div>
            <div class="page-break"></div>
        </div>
        <div v-for="(clientes,index) in sites" :key="index">
            <div class="portfolio-header">
                <h2>Portfolio</h2>
            </div>
            <div class="portfolio">
                <a :href="site.link" v-for="site in clientes" :key="site.link" target="_blank">
                    <picture>
                        <img :src="site.img" alt />
                    </picture>
                    <h3>
                        {{ site.title }}
                        <i class="fas fa-link"></i>
                    </h3>
                    <p>{{ site.tags }}</p>
                </a>
            </div>
        </div>
    </div>
</template>
<script>
import moment from "moment";
import Projects from "./projects";

export default {
    data() {
        return {
            Projects,
            Sites: [
                /*
                {
                    title: "Studio GT",
                    link: "https://www.studiogt.com.br",
                    img: imgs["www.studiogt.com.br"],
                    tags: "PHP, MySQL, Vue, NodeJs, GraphQL, Twig"
                },
                {
                    title: "Imobiliária São Luiz",
                    link: "https://www.saoluiz.imb.br",
                    img: imgs["www.saoluiz.imb.br"],
                    tags:
                        "PHP, MySQL, Oracle, GraphQL, Rest, XML, jQuery, Twig, Vue"
                },
                {
                    title: "Imobiliária Vila Rica",
                    link: "https://www.vilarica.com.br",
                    img: imgs["www.vilarica.com.br"],
                    tags:
                        "PHP, MySQL, Oracle, GraphQL, Rest, XML, jQuery, Twig, Vue"
                },
                {
                    title: "amamae",
                    link: "https://www.amamae.com.br",
                    img: imgs["www.amamae.com.br"],
                    tags: "PHP, MySQL, jQuery, Twig"
                },
                {
                    title: "Cidepe",
                    link: "https://www.cidepe.com.br",
                    img: imgs["www.cidepe.com.br"],
                    tags: "PHP, MySQL, jQuery, XML, Twig"
                },
                {
                    title: "GNC Cinemas",
                    link: "https://www.gnccinemas.com.br",
                    img: imgs["www.gnccinemas.com.br"],
                    tags: "PHP, MySQL, jQuery, XML, Twig"
                },
                {
                    title: "Vira Lua",
                    link: "https://www.viralua.com.br",
                    img: imgs["www.viralua.com.br"],
                    tags: "PHP, MySQL, jQuery, Twig, Soap, Rest"
                },
                {
                    title: "Mengue Imóveis",
                    link: "https://www.mengueimoveis.com.br",
                    img: imgs["www.mengueimoveis.com.br"],
                    tags: "PHP, MySQL, jQuery, Rest, Twig"
                },
                {
                    title: "Onyx Lorenzoni",
                    link: "http://www.onyxlorenzoni.com.br",
                    img: imgs["www.onyxlorenzoni.com.br"],
                    tags: "PHP, MySQL, jQuery, Twig"
                },
                {
                    title: "Patins Rye",
                    link: "https://www.patinsrye.com.br",
                    img: imgs["www.patinsrye.com.br"],
                    tags: "PHP, MySQL, jQuery, Twig, Soap, Rest"
                },
                {
                    title: "Pousada Pinhão e Poesia",
                    link: "https://www.pousadapinhaoepoesia.com.br",
                    img: imgs["www.pousadapinhaoepoesia.com.br"],
                    tags: "PHP, MySQL, jQuery, Twig"
                },
                {
                    title: "Radimagem",
                    link: "https://www.radimagem.com.br",
                    img: imgs["www.radimagem.com.br"],
                    tags: "PHP, MySQL, jQuery, Twig"
                },

                {
                    title: "Serzzare",
                    link: "https://www.serzzare.com.br",
                    img: imgs["www.serzzare.com.br"],
                    tags:
                        "PHP, MySQL, jQuery, Twig, Soap, Rest, Vue, SVG, Backbone.js"
                },
                {
                    title: "Somax",
                    link: "https://www.somaxonline.com.br",
                    img: imgs["www.somaxonline.com.br"],
                    tags: "PHP, MySQL, jQuery, Twig, Soap, Rest"
                },
                {
                    title: "ST Produções",
                    link: "https://www.stproducoes.com.br",
                    img: imgs["www.stproducoes.com.br"],
                    tags: "PHP, MySQL, jQuery, Twig, Soap, Rest"
                },
                {
                    title: "Vértice Iluminação",
                    link: "http://www.verticeiluminacao.com.br",
                    img: imgs["www.verticeiluminacao.com.br"],
                    tags: "PHP, MySQL, jQuery, Twig"
                }
                */
            ]
        };
    },
    computed: {
        sites() {
            let Sites = this.Sites;
            let sites = [];
            for (let i = 0; i < Sites.length; i += 6) {
                sites.push(Sites.slice(i, i + 6));
            }
            return sites;
        },
        projects() {
            let Projects = [...this.Projects].map((project, id) => {
                let p = { ...project };
                p.id = id;
                p.inicio = moment(project.inicio).format("MMMM Do YYYY");
                p.termino = moment(project.termino).format("MMMM Do YYYY");
                return p;
            });

            let projects = [];
            for (let i = 0; i < Projects.length; i += 10) {
                projects.push(Projects.slice(i, i + 10));
            }
            console.log(projects);
            return projects;
        }
    }
};
</script>
