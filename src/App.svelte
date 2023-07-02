<script>
    import golangImg from "./assets/golang.png";
    import kotlinImg from "./assets/kotlin.png";
    import flutterImg from "./assets/flutter.png";
    import vueImg from "./assets/vue.png";
    import androidImg from "./assets/android.png";
    import jsImg from "./assets/js.png";
    import reactImg from "./assets/react.png";
    import gitImg from "./assets/git.png";
    import djangoImg from "./assets/django.png";
    import pythonImg from "./assets/python.png";
    import dockerImg from "./assets/docker.webp";
    import cleanArchImg from "./assets/clean-architecture.png";
    import unitTestImg from "./assets/unit-test.png";
    import postgresImg from "./assets/postgres.png";
    import scrumImg from "./assets/scrum.svg";

    import moment from "moment";

    const exp = [
        {
            company: "Stone Co.",
            role: "Software Engineer (Go)",
            site: "https://www.stone.com.br/",
            start: new Date("2021-06"),
            tech: [
                "golang",
                "git",
                "docker",
                "clean archtecture",
                "unit testing",
                "postgres",
                "scrum",
            ],
            description: `I went through a brief period of training with the Go language, focusing on the technologies and methodologies used in the team, such as Go, Docker, Postgres, REST, gRPC, logging, Standard Language Libraries, Clean Architecture, Open-Api with Swagger and Clean Code . I work on front api projects, with apis that aims to solve problems from different clients such as logging, FAQs and translations. I also participate in one of the insurance APIs.`,
        },
        {
            company: "GreenMile",
            role: "Android Developer",
            site: "https://www.linkedin.com/company/greenmile/",
            start: new Date("2021-4"),
            end: new Date("2021-05"),
            tech: ["kotlin", "git"],
            description:
                "Short project creating an integration SDK for Android",
        },
        {
            company: "WDA",
            role: "Software Dev",
            site: "https://www.linkedin.com/company/wda-tecnologia-&-inova%C3%A7%C3%A3o/",
            start: new Date("2020-10"),
            end: new Date("2021-03"),
            tech: ["flutter", "vue", "js", "docker", "git"],
            description: `App development using Flutter and MobX. Frontend Web Development using Vue and Vuex. I worked with Flutter, Vue, Flux Architecture, Docker, Gitlab-CI and Heroku. Make decisions on the methodology used to solve problems, such as design patterns and data persistence technologies. Space to share knowledge, like when I gave a lecture on Nielsen Heuristics and Devops.`,
        },
        {
            company: "GreenMile",
            role: "React Developer",
            site: "https://www.linkedin.com/company/greenmile/",
            start: new Date("2020-04"),
            end: new Date("2020-09"),
            tech: ["js", "react", "git", "unit testing"],
            description: `App development using Cordova, React, React Hooks, Redux, and Jest. I really enjoyed being part of an experienced team, who taught me a lot, such as refactoring and leadership techniques. I really enjoyed React Hooks, Redux, and doing unit tests. My greatest pride was convincing the leadership that we needed a new dev stack, testing Flutter and React Native.`,
        },
        {
            company: "MercadApp",
            role: "Android Developer",
            site: "https://mercadapp.com.br/",
            start: new Date("2020-01"),
            end: new Date("2020-03"),
            tech: ["android", "kotlin", "git", "scrum"],
            description: `App Development using Kotlin and Android JetPack. Worked as a duo, with a lot of cooperation and learning. We used a lot of good technologies and patterns that came with Jetpack and Kotlin which were great, especially Kotlin (one of the best languages ​​to use OOP in my opinion) and the design patterns that came with JetPack (like MVVM and Observable).`,
        },
        {
            company: "NASH IFCE",
            role: "Android Developer",
            site: "https://ifce.edu.br/fortaleza/laboratorios/fotos/nash.jpg/view",
            start: new Date("2019-06"),
            end: new Date("2020-01"),
            tech: ["android", "kotlin", "git"],
            description: `Android Developer with Kotlin and Android JetPack. Mobile Developer with Flutter. I worked on 3 projects (Foitop, Ortopex and PBL) which gave me a lot of room to study. The best part was having a team that was like family. I studied and worked with native Android (Kotlin and JetPack), Flutter and Ionic. I found myself as a developer there, as someone who works in a team, who studies hard and struggles to solve problems.`,
        },
        {
            company: "LDS IFCE",
            role: "Backend Developer",
            site: "https://lds.inf.br/",
            start: new Date("2019-07"),
            end: new Date("2019-11"),
            tech: ["django", "python", "docker", "git", "postgres", "scrum"],
        },
        {
            company: "NASH IFCE",
            role: "React Developer",
            site: "https://ifce.edu.br/fortaleza/laboratorios/fotos/nash.jpg/view",
            start: new Date("2018-10"),
            end: new Date("2018-12"),
            tech: ["react", "js", "git"],
        },
        {
            company: "Freelance - 2Go!",
            role: "Fullstack Developer",
            site: "https://2gobranding.com.br/",
            start: new Date("2018-8"),
            end: new Date("2018-12"),
            tech: ["django", "python", "git", "postgres"],
            description: `System for scheduling and managing medical appointments. This was the first time I had to think about almost everything from a product to a client, from UX and design to code and hosting.`,
        },
    ];

    let knowledge = {
        golang: { img: golangImg, pref: "is fav.", kind: "language" },
        kotlin: { img: kotlinImg, pref: "can do", kind: "language" },
        js: { img: jsImg, pref: "can do", kind: "language" },
        python: { img: pythonImg, pref: "can do", kind: "language" },
        django: { img: djangoImg, pref: "can do", kind: "framework" },
        react: { img: reactImg, pref: "can do", kind: "framework" },
        flutter: { img: flutterImg, pref: "can do", kind: "platform" },
        vue: { img: vueImg, pref: "can do", kind: "framework" },
        android: { img: androidImg, pref: "can do", kind: "platform" },
        git: { img: gitImg, pref: "is fav.", kind: "tool" },
        docker: { img: dockerImg, pref: "is fav.", kind: "tool" },
        postgres: { img: postgresImg, pref: "is fav.", kind: "tool" },
        "clean archtecture": {
            img: cleanArchImg,
            pref: "is fav.",
            kind: "concept",
        },
        "unit testing": { img: unitTestImg, pref: "is fav.", kind: "concept" },
        scrum: { img: scrumImg, pref: "is fav.", kind: "concept" },
    };

    exp.forEach((e) => {
        const end = e.end ? e.end : new Date();
        const duration = end.getTime() - e.start.getTime();

        e.tech.forEach((t) => {
            if (
                knowledge[t].lastTime == undefined ||
                knowledge[t].lastTime < end
            ) {
                knowledge[t].lastTime = end;
                knowledge[t].lastExp = e.company;
            }

            if (knowledge[t].time === undefined) {
                knowledge[t].time = duration;
            } else {
                knowledge[t].time += duration;
            }
        });
    });

    function getKind(kind) {
        return Object.entries(knowledge)
            .filter((e) => e[1].kind == kind)
            .sort((a, b) => a[1].time - b[1].time)
            .reverse();
    }

    const techSections = [
        { title: "Languages", kind: "language" },
        { title: "Frameworks", kind: "framework" },
        { title: "Concepts", kind: "concept" },
        { title: "Tools", kind: "tool" },
    ];
</script>

<main class="container">
    <section id="presentation">
        <h1>Hello!</h1>
        <div class="title-separator" />
        <p>
            I'm a programmer with six years of experience, three of them
            professional. I have resilience and ease of learning as qualities,
            which allow me to adapt to different languages and tools. I
            currently work for Stone Co., a fintech company, using Golang. In
            this work, I faced several challenges, such as:
        </p>
        <ul>
            <li>
                Migration of deploy system to helm tool, which allowed me to
                automate and standardize software delivery processes in
                different environments.
            </li>
            <li>
                Implementation of server side events, which allowed me to create
                bidirectional communication between the server and the client,
                improving the user experience.
            </li>
            <li>
                Development of use cases with grpc support, which made me learn
                about a modern and efficient protocol for communication between
                services, using binary buffers and streaming.
            </li>
            <li>
                Research on BFF (Backend for Frontend) implementation
                strategies, which led me to study architectures that separate
                backend responsibilities according to frontend needs, increasing
                performance and scalability.
            </li>
        </ul>
        <p>
            Before working at Stone Co., I was a programmer at GreenMile, a
            lastmile logistics software company that serves customers such as
            Coca-Cola and Pepsi distributors. At this company, I developed
            solutions that optimized the transport and delivery of products from
            the two largest beverage companies in the world. For that, I used
            technologies like React, Redux and Kotlin.
        </p>
        <p>
            In addition, I have a good sense of humor, I like to work in a team
            and I am continually looking for ways to improve the quality of
            deliveries. I believe that humor is an important tool for dealing
            with stress and creating a more productive and enjoyable work
            environment. I also value teamwork, as I know it is essential for
            the success of any project. I always try to learn from my colleagues
            and share my knowledge. Finally, I have a mindset of continuous
            improvement, always trying to update myself on news in the area and
            apply the best solutions for each problem.
        </p>
    </section>
    <section id="tech">
        <h1>Tech</h1>
        <div class="title-separator" />
        {#each techSections as ts}
            <h2>{ts.title}</h2>
            <div class="cards-row">
                {#each getKind(ts.kind) as [name, t]}
                    <div class="card">
                        <img alt="{name} logo" src={t.img} />
                        <div class="card-content">
                            <p>name: <i>{name}</i></p>
                            <p>
                                time: <i>{moment.duration(t.time).humanize()}</i
                                >
                            </p>
                            <p>last: <i>{t.lastExp}</i></p>
                            <p>pref: <i>{t.pref}</i></p>
                        </div>
                    </div>
                {/each}
            </div>
        {/each}
    </section>
    <section id="expirience">
        <h1>Expirience</h1>
        <div class="title-separator" />
        <div class="expirience-grid">
            {#each exp as e}
                <div>
                    <h2>
                        <a href={e.site}>{e.company}</a> - {e.role}
                    </h2>
                    <h4>
                        {moment(e.start).format("MMM YYYY")} ~ {e.end
                            ? moment(e.end).format("MMM YYYY")
                            : "Today"}
                    </h4>
                    <p>{e.description ? e.description : ""}</p>
                    <h5>Skills:</h5>
                    <ul>
                        {#each e.tech as t}
                            <li>{t}</li>
                        {/each}
                    </ul>
                </div>
            {/each}
        </div>
    </section>
    <section id="education">
        <h1>Education</h1>
        <div class="title-separator" />
        <h2>Computer Engineering - <a href="https://ifce.edu.br/">IFCE</a></h2>
        <h4>2017 ~ 2024</h4>
        <p>
            Computer engineering is a course that deals with the design,
            implementation, and management of information systems of both
            software and hardware processes. Computer engineers work with all
            aspects of computer operating systems, from software to robotics.
            Computer engineering majors coursework is calculus, physics,
            programming, data structures, object oriented programming, algorithms, computer systems
            engineering, computer architecture and design of operating systems.
        </p>
    </section>
</main>

<style>
    .expirience-grid {
        display: grid;
        grid-template-columns: 1fr 1fr;
        column-gap: 1rem;
        row-gap: 1rem;
    }
    .expirience-grid > div > h5 {
        margin-bottom: 0;
    }
    .expirience-grid > div > ul {
        margin-top: 0.5rem;
        padding-left: 1.5rem;
    }
</style>
