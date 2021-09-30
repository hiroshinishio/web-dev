# 【保存版】WEBアプリ開発における基礎～最新 <!-- omit in toc -->

## 1.  はじめに

WEBアプリケーションの構成や技術選定を考えるにあたって調べた専門用語やトレンドをメモしました。色んな書籍やブログをサーフィンして調べたまとめ記事です。かなりコピペもしているので、その際は出典としてURLを貼るようにしてます。

WEB系の知識が0の状態からまとめたので、すごく基本的なことから最新のトレンドまで雑多に入ってます。なるべく、上から読んでいけば一通りわかるようになってます。間違ってる箇所等あればご指摘いただけると幸いです。

対象者は下記のような方を想定してます。

- ノンエンジニアのITコンサルやSEだけど、開発のこと知りたい！
- フルスタックではないエンジニアなので、横の知識が足りない！
- エンジニアだけど歴が浅いので、体系だって知識をつけたい！
- SaaSで起業するぞ！と思ったけど、開発のこと知らない！
- 社内で偉くなったので細かい知識はいらないけど、評価はしないといけない！
- とにかく横文字が多すぎて苦痛、概要だけでも拾いたい！
- WEBのすべてを知りたい・・・（知らないことがあるなんて嫌だ）

では、長いですがどうぞ。

- [1.  はじめに](#1--はじめに)
- [2.  Internet](#2--internet)
  - [2.1. Internet Protocol Suite](#21-internet-protocol-suite)
    - [2.1.1. Application Layer](#211-application-layer)
    - [2.1.2. Transport Layer](#212-transport-layer)
    - [2.1.3. Internet Layer](#213-internet-layer)
    - [2.1.4. Network Interface Layer](#214-network-interface-layer)
  - [2.2. HTTP (HyperText Transfer Protocol)](#22-http-hypertext-transfer-protocol)
    - [2.2.1. HTTP/0.9](#221-http09)
    - [2.2.2. HTTP/1.0](#222-http10)
    - [2.2.3. HTTP/1.1](#223-http11)
    - [2.2.4. HTTP/2](#224-http2)
    - [2.2.5. HTTP/3](#225-http3)
  - [2.3. HTTPS (HTTP over SSL/TLS)](#23-https-http-over-ssltls)
  - [2.4. Cookie (HTTP Cookie)](#24-cookie-http-cookie)
  - [2.5. Third Party Cookie](#25-third-party-cookie)
  - [2.6. Cache File](#26-cache-file)
  - [2.7. TCP (Transmission Control Protocol)](#27-tcp-transmission-control-protocol)
  - [2.8. SSL/TLS Handshake](#28-ssltls-handshake)
  - [2.9. URL (a Uniform Resource Locator)](#29-url-a-uniform-resource-locator)
  - [2.10. ISP (Internet Service Provider)](#210-isp-internet-service-provider)
  - [2.11. SEO (Search Engine Optimization)](#211-seo-search-engine-optimization)
  - [2.12. gRPC (Remote Procedure Call)](#212-grpc-remote-procedure-call)
  - [2.13. Semantic WEB](#213-semantic-web)
    - [2.13.1. RDF (Resource Description Framework)](#2131-rdf-resource-description-framework)
    - [2.13.2. OWL (The W3C Web Ontology Language)](#2132-owl-the-w3c-web-ontology-language)
  - [2.14. Web Socket](#214-web-socket)
- [3. Browser](#3-browser)
  - [3.1. Browserの種類](#31-browserの種類)
    - [3.1.1. Chrome](#311-chrome)
    - [3.1.2. Safari](#312-safari)
    - [3.1.3. Firefox](#313-firefox)
    - [3.1.4. Edge](#314-edge)
    - [3.1.5. Sidekick](#315-sidekick)
  - [3.2. Rendering Engine](#32-rendering-engine)
    - [3.2.1. Webkit](#321-webkit)
    - [3.2.2. Blink](#322-blink)
  - [3.3. JavaScript Engine](#33-javascript-engine)
    - [3.3.1. V8](#331-v8)
  - [3.4. Critical Rendering Path](#34-critical-rendering-path)
    - [3.4.1. Object Modelの構築](#341-object-modelの構築)
    - [3.4.2. Rendering Tree の構築](#342-rendering-tree-の構築)
    - [3.4.3. Rendering Tree のレイアウト](#343-rendering-tree-のレイアウト)
    - [3.4.4. Rendering Tree の描画](#344-rendering-tree-の描画)
- [4. DNS (Domain Name System)](#4-dns-domain-name-system)
  - [4.1. Registry（レジストリ）](#41-registryレジストリ)
  - [4.2. Registrar（レジストラ）](#42-registrarレジストラ)
- [5. WEB Server](#5-web-server)
  - [5.1. WEB Server のタイプ](#51-web-server-のタイプ)
    - [5.1.1. Prefork](#511-prefork)
    - [5.1.2. Event Driven](#512-event-driven)
    - [5.1.3. Worker](#513-worker)
  - [5.2. WEB Server Middlewares](#52-web-server-middlewares)
    - [5.2.1. Apache HTTP Server](#521-apache-http-server)
    - [5.2.2. nginx](#522-nginx)
    - [5.2.3. Cloudflare](#523-cloudflare)
    - [5.2.4. LiteSpeed](#524-litespeed)
    - [5.2.5. Microsoft IIS (Internet Information Service)](#525-microsoft-iis-internet-information-service)
  - [5.3. WEB Server Software の利用シェア](#53-web-server-software-の利用シェア)
  - [5.4. Static Content（静的コンテンツ）](#54-static-content静的コンテンツ)
  - [5.5. CDN (Contents Delivery Network)](#55-cdn-contents-delivery-network)
  - [5.6. CDN 事業者](#56-cdn-事業者)
  - [5.7. CDN で使用されている技術](#57-cdn-で使用されている技術)
  - [5.8. Dynamic Content（動的コンテンツ）](#58-dynamic-content動的コンテンツ)
  - [5.9. CGI (Common Gateway Interface)](#59-cgi-common-gateway-interface)
  - [5.10. WSGI (Web Server Gateway Interface)](#510-wsgi-web-server-gateway-interface)
    - [5.10.1. Libraries / Frameworks for WSGI](#5101-libraries--frameworks-for-wsgi)
  - [5.11. Rack / PSGI (Perl Web Server Gateway Interface)](#511-rack--psgi-perl-web-server-gateway-interface)
- [6. AP Server (Application Server)](#6-ap-server-application-server)
  - [6.1. Tomcat](#61-tomcat)
  - [6.2. JBOSS](#62-jboss)
  - [6.3. Microsoft IIS](#63-microsoft-iis)
- [7. HTML and CSS](#7-html-and-css)
  - [7.1. HTML (HyperText Markup Language)](#71-html-hypertext-markup-language)
  - [7.2. DOM (Document Object Model)](#72-dom-document-object-model)
  - [7.3. OGP (Open Graph Protocol)](#73-ogp-open-graph-protocol)
  - [7.4. CSS (Cascading Style Sheets)](#74-css-cascading-style-sheets)
  - [7.5. Alt CSS (Alternative CSS)](#75-alt-css-alternative-css)
  - [7.6. CSS Frameworks](#76-css-frameworks)
    - [7.6.1. Bootstrap](#761-bootstrap)
    - [7.6.2. Tailwind CSS](#762-tailwind-css)
    - [7.6.3. Materialize CSS](#763-materialize-css)
    - [7.6.4. Foundation](#764-foundation)
    - [7.6.5. Reactstrap](#765-reactstrap)
    - [7.6.6. Material UI](#766-material-ui)
    - [7.6.7. Chakra UI](#767-chakra-ui)
    - [7.6.8. Other CSS Frameworks](#768-other-css-frameworks)
  - [7.7. Post CSS](#77-post-css)
    - [7.7.1. Post CSS Tools](#771-post-css-tools)
  - [7.8. CSS in JS](#78-css-in-js)
    - [7.8.1. CSS in JS の主なライブラリ](#781-css-in-js-の主なライブラリ)
  - [7.9. CSS Architecture](#79-css-architecture)
    - [7.9.1. BEM (Block, Element, Modifier)](#791-bem-block-element-modifier)
  - [7.10. WEB Font](#710-web-font)
    - [7.10.1. Font Awesome](#7101-font-awesome)
  - [7.11. Image Files](#711-image-files)
    - [7.11.1. SVG (Scalable Vector Graphics)](#7111-svg-scalable-vector-graphics)
  - [7.12. Responsive Design](#712-responsive-design)
    - [7.12.1. Meta Viewport Tag](#7121-meta-viewport-tag)
    - [7.12.2. Media Query](#7122-media-query)
  - [7.13. User Interface Design](#713-user-interface-design)
    - [7.13.1. Skeuomorphism Design](#7131-skeuomorphism-design)
    - [7.13.2. Flat Design](#7132-flat-design)
    - [7.13.3. Material Design](#7133-material-design)
  - [7.14. CMS (Contents Management System)](#714-cms-contents-management-system)
    - [7.14.1. WordPress](#7141-wordpress)
    - [7.14.2. Drupal](#7142-drupal)
  - [7.15. Headless CMS](#715-headless-cms)
    - [7.15.1. Contentful](#7151-contentful)
    - [7.15.2. MicroCMS](#7152-microcms)
- [8.  JavaScript](#8--javascript)
  - [8.1. ECMA Script](#81-ecma-script)
    - [8.1.1. Prototype-based VS Class-based](#811-prototype-based-vs-class-based)
  - [8.2. Alt JS / JavaScript Flavors](#82-alt-js--javascript-flavors)
    - [8.2.1. CoffeeScript](#821-coffeescript)
    - [8.2.2. TypeScript](#822-typescript)
    - [8.2.3. JavaScript Flavors の利用率](#823-javascript-flavors-の利用率)
  - [8.3. Front-End JS Frameworks](#83-front-end-js-frameworks)
    - [8.3.1. React](#831-react)
    - [8.3.2. Vue.js](#832-vuejs)
    - [8.3.3. Svelte](#833-svelte)
    - [8.3.4. Angular](#834-angular)
    - [8.3.5. Front-End JS Frameworks の利用率や満足度](#835-front-end-js-frameworks-の利用率や満足度)
    - [8.3.6. Other Alt JS](#836-other-alt-js)
  - [8.4. Runtime for JavaScript (and TypeScript)](#84-runtime-for-javascript-and-typescript)
    - [8.4.1. Node.js](#841-nodejs)
    - [8.4.2. Deno（ディーノ）](#842-denoディーノ)
    - [8.4.3. npm (Node Package Manager)](#843-npm-node-package-manager)
  - [8.5. Back-End JS Frameworks](#85-back-end-js-frameworks)
    - [8.5.1. Express.js](#851-expressjs)
    - [8.5.2. Next.js](#852-nextjs)
    - [8.5.3. Nuxt.js](#853-nuxtjs)
    - [8.5.4. Sapper](#854-sapper)
    - [8.5.5. SvelteKit](#855-sveltekit)
    - [8.5.6. Blitz.js](#856-blitzjs)
  - [8.6. Build Tool / Bandler for Alt JS](#86-build-tool--bandler-for-alt-js)
    - [8.6.1. Webpack](#861-webpack)
    - [8.6.2. Rollup.js](#862-rollupjs)
    - [8.6.3. Vite](#863-vite)
    - [8.6.4. Stencil.js](#864-stenciljs)
  - [8.7. Transcompiler for Alt JS](#87-transcompiler-for-alt-js)
    - [8.7.1. Babel.js](#871-babeljs)
  - [8.8. CLI for Alt JS (a Command-Line Interface)](#88-cli-for-alt-js-a-command-line-interface)
  - [8.9. State Container for JS](#89-state-container-for-js)
    - [8.9.1. Redux](#891-redux)
    - [8.9.2. Flux](#892-flux)
    - [8.9.3. MobX](#893-mobx)
    - [8.9.4. Jotai](#894-jotai)
    - [8.9.5. Vuex](#895-vuex)
  - [8.10. Virtual DOM](#810-virtual-dom)
    - [8.10.1. Shadow DOM](#8101-shadow-dom)
  - [8.11. Source Map](#811-source-map)
  - [8.12. Data Format](#812-data-format)
    - [8.12.1. JSON (JavaScript Object Notation)](#8121-json-javascript-object-notation)
    - [8.12.2. XML (Extensible Markup Language)](#8122-xml-extensible-markup-language)
    - [8.12.3. BSON (Binary JSON)](#8123-bson-binary-json)
    - [8.12.4. YAML (YAML Ain't Markup Language)](#8124-yaml-yaml-aint-markup-language)
  - [8.13. Ajax (Asynchronous JavaScript and XML)](#813-ajax-asynchronous-javascript-and-xml)
    - [8.13.1. Google による Ajax の先行事例](#8131-google-による-ajax-の先行事例)
  - [8.14. Animation](#814-animation)
    - [8.14.1. GSAP (GreenSock Animation Platform)](#8141-gsap-greensock-animation-platform)
  - [8.15. その他の JavaScript / React の概念や機能](#815-その他の-javascript--react-の概念や機能)
    - [8.15.1. Event Bubbling](#8151-event-bubbling)
    - [8.15.2. Scope](#8152-scope)
    - [8.15.3. Strict Mode](#8153-strict-mode)
    - [8.15.4. Fast Refresh](#8154-fast-refresh)
    - [8.15.5. JSX](#8155-jsx)
- [9. WASM (Web Assembly)](#9-wasm-web-assembly)
  - [9.1. WASMはどのくらい速いのか](#91-wasmはどのくらい速いのか)
  - [9.2. Rust](#92-rust)
  - [9.3. WASI (WebAssembly System Interface)](#93-wasi-webassembly-system-interface)
  - [9.4. WASM Runtime](#94-wasm-runtime)
  - [9.5. Rust Web Frameworks](#95-rust-web-frameworks)
    - [9.5.1. Rocket](#951-rocket)
    - [9.5.2. Actix-web](#952-actix-web)
    - [9.5.3. Warp](#953-warp)
    - [9.5.4. Tide](#954-tide)
    - [9.5.5. Gotham](#955-gotham)
- [10.  Server Side Script](#10--server-side-script)
  - [10.1. Python Frameworks](#101-python-frameworks)
    - [10.1.1. Flask](#1011-flask)
    - [10.1.2. Django](#1012-django)
    - [10.1.3. Fast API](#1013-fast-api)
    - [10.1.4. Tornado](#1014-tornado)
    - [10.1.5. Web2py](#1015-web2py)
    - [10.1.6. Pyramid](#1016-pyramid)
    - [10.1.7. Mako](#1017-mako)
  - [10.2. PHP Frameworks](#102-php-frameworks)
    - [10.2.1. Laravel](#1021-laravel)
    - [10.2.2. Symfony](#1022-symfony)
  - [10.3. Java Frameworks](#103-java-frameworks)
    - [10.3.1. Spring](#1031-spring)
  - [10.4. Async Technologies for Python / Django](#104-async-technologies-for-python--django)
    - [10.4.1. ASGI (Asynchronous Server Gateway Interface)](#1041-asgi-asynchronous-server-gateway-interface)
    - [10.4.2. AnyIO](#1042-anyio)
    - [10.4.3. asgiref](#1043-asgiref)
    - [10.4.4. asyncio](#1044-asyncio)
    - [10.4.5. Channels](#1045-channels)
    - [10.4.6. Curio](#1046-curio)
    - [10.4.7. Daphne](#1047-daphne)
    - [10.4.8. Quart](#1048-quart)
    - [10.4.9. Responder](#1049-responder)
    - [10.4.10. Sanic](#10410-sanic)
    - [10.4.11. Starlette](#10411-starlette)
    - [10.4.12. trio](#10412-trio)
    - [10.4.13. Uvicorn](#10413-uvicorn)
    - [10.4.14. Hypercorn](#10414-hypercorn)
- [11. Web API (Application Programming Interface)](#11-web-api-application-programming-interface)
  - [11.1. RESTful API](#111-restful-api)
    - [11.1.1. RESTful API のデータ例](#1111-restful-api-のデータ例)
    - [11.1.2. Postman](#1112-postman)
  - [11.2. GraphQL](#112-graphql)
    - [11.2.1. GraphQL のデータ例](#1121-graphql-のデータ例)
    - [11.2.2. Hasura](#1122-hasura)
    - [11.2.3. Apollo GraphQL](#1123-apollo-graphql)
  - [11.3. Webhook](#113-webhook)
- [12. WEB Application](#12-web-application)
  - [12.1. SPA (Single Page Application)](#121-spa-single-page-application)
    - [12.1.1. SPA と SEO](#1211-spa-と-seo)
  - [12.2. SSR (Server-Side Rendering)](#122-ssr-server-side-rendering)
  - [12.3. SSG (Static Site Generator)](#123-ssg-static-site-generator)
    - [12.3.1. Hugo](#1231-hugo)
    - [12.3.2. Jekyll](#1232-jekyll)
    - [12.3.3. ASP.NET](#1233-aspnet)
    - [12.3.4. ASP.NET Core](#1234-aspnet-core)
    - [12.3.5. Gatsby.js](#1235-gatsbyjs)
  - [12.4. PWA (Progressive Web Apps)](#124-pwa-progressive-web-apps)
  - [12.5. Hybrid Application](#125-hybrid-application)
  - [12.6. Hybrid App Frameworks](#126-hybrid-app-frameworks)
    - [12.6.1. React Native](#1261-react-native)
    - [12.6.2. Flutter](#1262-flutter)
    - [12.6.3. Ionic](#1263-ionic)
    - [12.6.4. DART](#1264-dart)
  - [12.7. RIA (Rich Internet Application)](#127-ria-rich-internet-application)
  - [12.8. BFF (Backends For Frontend)](#128-bff-backends-for-frontend)
    - [12.8.1. BFF のメリット](#1281-bff-のメリット)
    - [12.8.2. BFF のデメリット](#1282-bff-のデメリット)
  - [12.9. Microservices](#129-microservices)
    - [12.9.1. Istio](#1291-istio)
  - [12.10. MVC (Model-View-Controller)](#1210-mvc-model-view-controller)
  - [12.11. MVVM (Model-View-ViewModel)](#1211-mvvm-model-view-viewmodel)
    - [12.11.1. Model](#12111-model)
    - [12.11.2. View](#12112-view)
    - [12.11.3. ViewModel](#12113-viewmodel)
  - [12.12. Accessibility (a11y)](#1212-accessibility-a11y)
- [13.  RDBMS (Relational DataBase Management System)](#13--rdbms-relational-database-management-system)
  - [13.1. RDBMSの種類](#131-rdbmsの種類)
  - [13.2. DBの冗長化](#132-dbの冗長化)
  - [13.3. Query Cache](#133-query-cache)
  - [13.4. ORM (Object-Relational Mapper)](#134-orm-object-relational-mapper)
  - [13.5. SQL Antipatterns](#135-sql-antipatterns)
    - [13.5.1. MENTOR Your Indexes](#1351-mentor-your-indexes)
  - [13.6. Dump](#136-dump)
  - [13.7. ERD (Entity Relationship Diagram)](#137-erd-entity-relationship-diagram)
    - [13.7.1. Conceptual Data Model](#1371-conceptual-data-model)
    - [13.7.2. Logical Data Model](#1372-logical-data-model)
    - [13.7.3. Physical Data Model](#1373-physical-data-model)
  - [13.8. EERD (Enhanced / Extended ERD)](#138-eerd-enhanced--extended-erd)
  - [13.9. Drawing Tools](#139-drawing-tools)
    - [13.9.1. Draw.io](#1391-drawio)
    - [13.9.2. Lucidchart](#1392-lucidchart)
    - [13.9.3. Cacoo](#1393-cacoo)
- [14.  NoSQL DB (Not Only SQL DataBase)](#14--nosql-db-not-only-sql-database)
  - [14.1. NoSQL DB の種類](#141-nosql-db-の種類)
  - [14.2. KVS (Key-Value Store)](#142-kvs-key-value-store)
    - [14.2.1. Redis](#1421-redis)
    - [14.2.2. Memcached](#1422-memcached)
  - [14.3. Column-Oriented DB（カラム指向DB）](#143-column-oriented-dbカラム指向db)
    - [14.3.1. Apache Cassandra](#1431-apache-cassandra)
  - [14.4. Document-Oriented DB（ドキュメント指向DB）](#144-document-oriented-dbドキュメント指向db)
    - [14.4.1. MongoDB](#1441-mongodb)
    - [14.4.2. Robomongo](#1442-robomongo)
    - [14.4.3. Apache Couch DB](#1443-apache-couch-db)
    - [14.4.4. Realm](#1444-realm)
    - [14.4.5. Firestore](#1445-firestore)
  - [14.5. Multi-Model DB](#145-multi-model-db)
    - [14.5.1. ArangoDB](#1451-arangodb)
    - [14.5.2. Azure Cosmos DB](#1452-azure-cosmos-db)
    - [14.5.3. CrateIO](#1453-crateio)
    - [14.5.4. MarkLogic](#1454-marklogic)
    - [14.5.5. OrientDB](#1455-orientdb)
    - [14.5.6. Virtuoso](#1456-virtuoso)
    - [14.5.7. Fauna DB](#1457-fauna-db)
- [15. Version Control System](#15-version-control-system)
  - [15.1. GitHub](#151-github)
    - [15.1.1. GitHub Actions](#1511-github-actions)
    - [15.1.2. GitHub Webhooks](#1512-github-webhooks)
    - [15.1.3. GitHub Marketplace](#1513-github-marketplace)
    - [15.1.4. GitHub Enterprise](#1514-github-enterprise)
    - [15.1.5. GitHub Copilot](#1515-github-copilot)
  - [15.2. Git Command](#152-git-command)
- [16. CI/CD (Continuous Integration and Continuous Delivery)](#16-cicd-continuous-integration-and-continuous-delivery)
  - [16.1. CI/CD Tools](#161-cicd-tools)
    - [16.1.1. CircleCI](#1611-circleci)
    - [16.1.2. Travis CI](#1612-travis-ci)
    - [16.1.3. Jenkins](#1613-jenkins)
    - [16.1.4. GitHub Actions](#1614-github-actions)
    - [16.1.5. Other CI/CD](#1615-other-cicd)
  - [16.2. DevOps (Software Development and IT Operations)](#162-devops-software-development-and-it-operations)
  - [16.3. SRE (Site Reliability Engineering)](#163-sre-site-reliability-engineering)
- [17. Text Editor](#17-text-editor)
  - [17.1. VSCode (Visual Studio Code)](#171-vscode-visual-studio-code)
    - [17.1.1. VSCode Extensions](#1711-vscode-extensions)
  - [17.2. Atom](#172-atom)
  - [17.3. Eclipse IDE](#173-eclipse-ide)
  - [17.4. Web Storm](#174-web-storm)
- [18. Static Code Analysis](#18-static-code-analysis)
  - [18.1. Coding Standards for C](#181-coding-standards-for-c)
    - [18.1.1. MISRA-C](#1811-misra-c)
    - [18.1.2. CERT-C](#1812-cert-c)
    - [18.1.3. Coding Standards for JS](#1813-coding-standards-for-js)
- [19. Code Formatter](#19-code-formatter)
  - [19.1. Code Formatter のサービス例](#191-code-formatter-のサービス例)
    - [19.1.1. Prettier (for JS)](#1911-prettier-for-js)
    - [19.1.2. autopep8 (for Python)](#1912-autopep8-for-python)
    - [19.1.3. Black (for Python)](#1913-black-for-python)
    - [19.1.4. isort (for Python)](#1914-isort-for-python)
    - [19.1.5. YAPF (for Python)](#1915-yapf-for-python)
- [20.  Code Linter](#20--code-linter)
  - [20.1. Code Linter for JS](#201-code-linter-for-js)
    - [20.1.1. ESLint](#2011-eslint)
    - [20.1.2. JSHint](#2012-jshint)
    - [20.1.3. JSLint](#2013-jslint)
  - [20.2. Code Linter for CSS](#202-code-linter-for-css)
    - [20.2.1. Stylelint](#2021-stylelint)
  - [20.3. Code Linter for Java](#203-code-linter-for-java)
    - [20.3.1. SpotBugs](#2031-spotbugs)
  - [20.4. Code Linter for Multi-Languages](#204-code-linter-for-multi-languages)
    - [20.4.1. Coverity](#2041-coverity)
- [21. Test Frameworks](#21-test-frameworks)
  - [21.1. Test Frameworks for JS](#211-test-frameworks-for-js)
    - [21.1.1. Jest](#2111-jest)
    - [21.1.2. Mocha](#2112-mocha)
    - [21.1.3. Selenium](#2113-selenium)
- [22. Development Methods](#22-development-methods)
  - [22.1. Waterfall](#221-waterfall)
  - [22.2. Prototype](#222-prototype)
  - [22.3. Agile](#223-agile)
  - [22.4. Spiral](#224-spiral)
  - [22.5. Other Development Methods](#225-other-development-methods)
    - [22.5.1. DRY (Don’t Repeat Your Self)](#2251-dry-dont-repeat-your-self)
    - [22.5.2. OAOO (Once And Only Once)](#2252-oaoo-once-and-only-once)
    - [22.5.3. SOLID](#2253-solid)
    - [22.5.4. KISS (Keep It Simple, Stupid)](#2254-kiss-keep-it-simple-stupid)
    - [22.5.5. YAGNI (You Aren't Going to Need it.)](#2255-yagni-you-arent-going-to-need-it)
- [23. Agile Development Practices](#23-agile-development-practices)
  - [23.1. TDD (Test Driven Development)](#231-tdd-test-driven-development)
  - [23.2. BDD (Behavior Driven Development)](#232-bdd-behavior-driven-development)
    - [23.2.1. BDD Tools and Frameworks](#2321-bdd-tools-and-frameworks)
  - [23.3. DDD (Domain Driven Design)](#233-ddd-domain-driven-design)
  - [23.4. ATDD (Acceptance Test Driven Development)](#234-atdd-acceptance-test-driven-development)
    - [23.4.1. ATDD Tools and Frameworks](#2341-atdd-tools-and-frameworks)
  - [23.5. ADD (Attribute Driven Design)](#235-add-attribute-driven-design)
  - [23.6. FDD (Feature Driven Development)](#236-fdd-feature-driven-development)
  - [23.7. MDD (Model Driven Development)](#237-mdd-model-driven-development)
  - [23.8. UCDD (Use Case Driven Development)](#238-ucdd-use-case-driven-development)
  - [23.9. PDD (Proof Driven Development)](#239-pdd-proof-driven-development)
- [24. Testing Pyramid](#24-testing-pyramid)
  - [24.1. Unit Test](#241-unit-test)
    - [24.1.1. White-Box Testing](#2411-white-box-testing)
    - [24.1.2. Automated Testing](#2412-automated-testing)
    - [24.1.3. Coding Coverage](#2413-coding-coverage)
  - [24.2. Integration Test](#242-integration-test)
  - [24.3. E2E Test (End to End Test)](#243-e2e-test-end-to-end-test)
    - [24.3.1. Black-Box Testing](#2431-black-box-testing)
    - [24.3.2. E2E Test Frameworks](#2432-e2e-test-frameworks)
    - [24.3.3. E2E Test の不安定さ](#2433-e2e-test-の不安定さ)
  - [24.4. Feedback Cycle](#244-feedback-cycle)
- [25. Infrastructure](#25-infrastructure)
  - [25.1. AWS Service](#251-aws-service)
  - [25.2. AWSの各種用語](#252-awsの各種用語)
    - [25.2.1. VPC (Virtual Private Cloud)](#2521-vpc-virtual-private-cloud)
    - [25.2.2. Internet Gateway](#2522-internet-gateway)
    - [25.2.3. Virtual Private Gateway](#2523-virtual-private-gateway)
    - [25.2.4. NAT Gateway (a Network Address Translation Gateway)](#2524-nat-gateway-a-network-address-translation-gateway)
    - [25.2.5. Subnet](#2525-subnet)
    - [25.2.6. Route Table](#2526-route-table)
    - [25.2.7. Amazon Route 53](#2527-amazon-route-53)
    - [25.2.8. Amazon S3 (Amazon Simple Storage Service)](#2528-amazon-s3-amazon-simple-storage-service)
    - [25.2.9. Amazon EFS (Amazon Elastic File System)](#2529-amazon-efs-amazon-elastic-file-system)
    - [25.2.10. Amazon EBS (Amazon Elastic Block Store)](#25210-amazon-ebs-amazon-elastic-block-store)
    - [25.2.11. Amazon ECS (Amazon Elastic Container Service)](#25211-amazon-ecs-amazon-elastic-container-service)
    - [25.2.12. Amazon ElastiCache](#25212-amazon-elasticache)
    - [25.2.13. Amazon DynamoDB](#25213-amazon-dynamodb)
    - [25.2.14. Amazon API Gateway](#25214-amazon-api-gateway)
    - [25.2.15. AWS Lambda](#25215-aws-lambda)
    - [25.2.16. Amazon CloudFront](#25216-amazon-cloudfront)
    - [25.2.17. AWS Certificate Manager](#25217-aws-certificate-manager)
    - [25.2.18. Amazon Cognito](#25218-amazon-cognito)
    - [25.2.19. AWS Fargate](#25219-aws-fargate)
    - [25.2.20. Amazon Aurora](#25220-amazon-aurora)
    - [25.2.21. Amazon Kinesis Data Firehose](#25221-amazon-kinesis-data-firehose)
  - [25.3. Managed Services](#253-managed-services)
  - [25.4. Load Balancer](#254-load-balancer)
    - [25.4.1. LBの負荷分散方法](#2541-lbの負荷分散方法)
- [26. Serverless Hosting Service](#26-serverless-hosting-service)
  - [26.1. Firebase](#261-firebase)
    - [26.1.1. Firebase Hosting](#2611-firebase-hosting)
    - [26.1.2. Firestore](#2612-firestore)
    - [26.1.3. Firebase Authentication](#2613-firebase-authentication)
    - [Firebase のその他の機能](#firebase-のその他の機能)
  - [26.2. Netlify](#262-netlify)
  - [26.3. Vercel](#263-vercel)
  - [26.4. Heroku](#264-heroku)
  - [26.5. Supabase](#265-supabase)
  - [26.6. Gatsby Cloud](#266-gatsby-cloud)
- [27. Infrastructure Monitoring](#27-infrastructure-monitoring)
  - [27.1. Monitoring の種類](#271-monitoring-の種類)
    - [27.1.1. 死活監視](#2711-死活監視)
    - [27.1.2. リソース監視](#2712-リソース監視)
    - [27.1.3. 接続監視](#2713-接続監視)
    - [27.1.4. ログ監視](#2714-ログ監視)
    - [27.1.5. プロセス/サービス監視](#2715-プロセスサービス監視)
  - [27.2. 監視サービス](#272-監視サービス)
    - [27.2.1. Amazon CloudWatch](#2721-amazon-cloudwatch)
    - [27.2.2. Datadog](#2722-datadog)
    - [27.2.3. Mackerel](#2723-mackerel)
    - [27.2.4. Prometheus](#2724-prometheus)
    - [27.2.5. Zabbix](#2725-zabbix)
    - [27.2.6. Sentry](#2726-sentry)
    - [27.2.7. New Relic](#2727-new-relic)
- [28. Virtualization vs Containerization](#28-virtualization-vs-containerization)
  - [28.1. Virtualization](#281-virtualization)
    - [28.1.1. VirtualBox](#2811-virtualbox)
    - [28.1.2. VMware](#2812-vmware)
    - [28.1.3. AWS EC2](#2813-aws-ec2)
  - [28.2. Containerization](#282-containerization)
    - [28.2.1. Docker](#2821-docker)
    - [28.2.2. Kubernetes (K8s)](#2822-kubernetes-k8s)
    - [28.2.3. Micro Kubernetes (Micro K8s)](#2823-micro-kubernetes-micro-k8s)
    - [28.2.4. Lightweight Kubernetes (K3s)](#2824-lightweight-kubernetes-k3s)
- [29. IaC (Infrastructure as Code)](#29-iac-infrastructure-as-code)
  - [29.1. Terraform](#291-terraform)
  - [29.2. Ansible](#292-ansible)
  - [29.3. Chef](#293-chef)
- [30. Security](#30-security)
  - [30.1. Security Risks](#301-security-risks)
    - [30.1.1. Password Cracking](#3011-password-cracking)
    - [30.1.2. DOS Attack (Denial of Service)](#3012-dos-attack-denial-of-service)
    - [30.1.3. DDOS Attack (Distributed DOS)](#3013-ddos-attack-distributed-dos)
    - [30.1.4. Session Hijacking](#3014-session-hijacking)
    - [30.1.5. Directory Traversal](#3015-directory-traversal)
    - [30.1.6. XSS (Cross Site Scripting)](#3016-xss-cross-site-scripting)
    - [30.1.7. CSRF (Cross Site Request Forgeries)](#3017-csrf-cross-site-request-forgeries)
    - [30.1.8. SQL Injection](#3018-sql-injection)
  - [30.2. Security Policies](#302-security-policies)
    - [30.2.1. Same-Origin Policy](#3021-same-origin-policy)
    - [30.2.2. CORS (Cross-Origin Resource Sharing)](#3022-cors-cross-origin-resource-sharing)
  - [30.3. WAF (Web Application Firewall)](#303-waf-web-application-firewall)
  - [30.4. 不正アクセスを防ぐ仕組み](#304-不正アクセスを防ぐ仕組み)
  - [30.5. PKA (Public Key Authentication)](#305-pka-public-key-authentication)
  - [30.6. Authentication](#306-authentication)
    - [30.6.1. Open ID](#3061-open-id)
  - [30.7. Authorization](#307-authorization)
    - [30.7.1. OAuth (Open Authorization)](#3071-oauth-open-authorization)
    - [30.7.2. Open ID Connect](#3072-open-id-connect)
    - [30.7.3. JWT (JSON Web Tokens)](#3073-jwt-json-web-tokens)
    - [30.7.4. Auth0](#3074-auth0)
  - [30.8. Pen Test (Penetration Testing)](#308-pen-test-penetration-testing)
  - [30.9. Pen Test Tools](#309-pen-test-tools)
    - [30.9.1. Kali Linux](#3091-kali-linux)
    - [30.9.2. NMAP (Network Mapper)](#3092-nmap-network-mapper)
    - [30.9.3. Metasploit](#3093-metasploit)
    - [30.9.4. Wireshark](#3094-wireshark)
    - [30.9.5. Burp Suite](#3095-burp-suite)
    - [30.9.6. OWASP ZAP (Zed Attack Proxy)](#3096-owasp-zap-zed-attack-proxy)
- [31. Log運用](#31-log運用)
- [32. Performance](#32-performance)
  - [32.1. Performance 計測ツール](#321-performance-計測ツール)
    - [32.1.1. Google Lighthouse](#3211-google-lighthouse)
- [33. Payment](#33-payment)
  - [33.1. Payment Services](#331-payment-services)
    - [33.1.1. Stripe](#3311-stripe)
    - [33.1.2. Square](#3312-square)
    - [33.1.3. PayPal](#3313-paypal)
- [34. まとめ](#34-まとめ)

## 2.  Internet

### 2.1. Internet Protocol Suite

インターネットを含む多くのコンピュータネットワークにおいて、標準的に利用されている通信プロトコルのセットである。TCP/IP（Transmission Control Protocol /Internet Protocol ）とも呼ばれる。階層とそれぞれの階層で使用される主なプロトコルは、下記。

#### 2.1.1. Application Layer

トランスポート層までのネットワーク層を使って、どのような用途として使用するのかを決めるレイヤー。主なプロトコルは、HTTP、DNS、SMTP。

#### 2.1.2. Transport Layer

インターネット層のプロトコルが提供する機能を、より便利に使える機能（パケットのエラー処理や複数コネクションの管理等）として提供するレイヤー。主なプロトコルは、TCP、UDP、QUIC。

- TCP：　コネクション型のプロトコル。欠損パケットの再送処理や、パケットの到着順番の保証などの機能を提供するので高信頼だが、速度的なデメリットがある。暗号化通信をサポートしていない
- UDP：　コネクションレス型のプロトコル。信頼性が落ちる代わりに速度が速い。動画や音声のストリーミングに向いている。暗号化通信をサポートしていない
- QUIC：　UDPの上位レイヤーで、高速なのに高信頼。暗号化通信（TLS）も統合されている。TLSは Transport Layer Security の略。2012年にGoogleが開発

#### 2.1.3. Internet Layer

複数機器を経由した通信をするレイヤー。主なプロトコルは、IPv4、IPv6。IPv6が最新で、Googleによると33％程度が既にIPv6

#### 2.1.4. Network Interface Layer

同じネットワーク内にある機器とデータ通信するレイヤー。主なプロトコルは、Ethernet（有線LANの技術の総称）、Wi-Fi（無線）

<https://www.amazon.co.jp/dp/B092Q8SKDB/ref=cm_sw_r_tw_dp_KGFK4GJ0GF6ARKB15YHT?_encoding=UTF8&psc=1>
<https://www.amazon.co.jp/gp/product/B06XNMMC9S/ref=ppx_yo_dt_b_d_asin_title_o03?ie=UTF8&psc=1>

### 2.2. HTTP (HyperText Transfer Protocol)

HTTPはWEBでクライアントとサーバーが通信するときに使用されるアプリケーション層のプロトコル。そのプロトコルに則った通信。HTMLなどのテキストデータだけでなく、JSONなどのデータや、バイナリデータの転送も出来る

#### 2.2.1. HTTP/0.9

1991年から。もうほとんど使われてない

#### 2.2.2. HTTP/1.0

1996年から。もうほとんど使われてない

#### 2.2.3. HTTP/1.1

1999年から。まだ現在の主流のプロトコル。これ以降、HTTP Keep Aliveが適用されて、HTTPリクエストごとにTCPコネクションを確立せずに維持できるようになった。1つのHTML内に複数画像ある場合などに有効。HTTPパイプラインも適用されて、リクエストに対するレスポンスを待たずに次のリクエストが出来るようになった

#### 2.2.4. HTTP/2

2015年から。HTTP/1.1と後方互換性がある。ヘッダの圧縮や、パイプラインと呼ばれる通信の多重化技術が使われており、HTTP/1.1よりも高速。Googleが考案したSPDY（スピーディ）というプロトコルがベース。TCPコネクションにストリームという仮想的な複数の通信経路が導入され、リクエスト順にレスポンスしないといけなかったHTTPパイプラインが改良され順不同に返せるようになった。HTTP通信もテキストからバイナリに変わった。ヘッダー圧縮というヘッダーを差分だけ送るHPACK圧縮方式も追加。サーバープッシュというHTML内に画像があれば、それがリクエストされてなくてもサーバー側で判断してついでに送る技術も追加

#### 2.2.5. HTTP/3

これまでのバージョンではトランスポート層のプロトコルはTCPだったが、今回からQUICを使用。HTTP/2よりも高速

<https://www.amazon.co.jp/dp/B092Q8SKDB/ref=cm_sw_r_tw_dp_KGFK4GJ0GF6ARKB15YHT?_encoding=UTF8&psc=1>
<https://www.amazon.co.jp/gp/product/B06XNMMC9S/ref=ppx_yo_dt_b_d_asin_title_o03?ie=UTF8&psc=1>

### 2.3. HTTPS (HTTP over SSL/TLS)

暗号化方式であるSSL (Secure Sockets Layer) やTLS (Transport Layer Security) を利用したHTTP。SSLはバージョン3からTLSと改名されたがまだSSLの言葉が慣習的に残っている。やってくれることは

- 通信データの暗号化による盗聴防止。通信前に鍵の交換や暗号化方式の確認がなされる
- 送受信時のハッシュ比較による改ざん防止
- SSLサーバー証明書による、なりすまし防止。証明書にはランクがあり、EVが一番高く、緑の鍵マーク🔑が出る

HTTPSでないサイトは検索に優先順位が落ちるとされている。

### 2.4. Cookie (HTTP Cookie)

HTTPはステートレスな通信なので、状態管理はCookieで行う。

- WEBサーバーはレスポンスを返すときに、Cookieの値も返す
- クライアントはこのCookieの値も保存する
- 次のリクエスト時には保存してるCookieのデータをすべてWEBサーバーに送信する

そのため、Cookieにたくさんの値を保存しすぎると、通信効率が悪くなるので、Cookieには最低限の識別子のようなデータだけを記録し、状態管理の機能自体はWEBサーバー側に持つことが多い。有効期限がないCookieはブラウザが閉じられると削除される。こういうCookieをセッションCookieという。

<https://www.amazon.co.jp/dp/B092Q8SKDB/ref=cm_sw_r_tw_dp_KGFK4GJ0GF6ARKB15YHT?_encoding=UTF8&psc=1>
<https://www.amazon.co.jp/gp/product/B06XNMMC9S/ref=ppx_yo_dt_b_d_asin_title_o03?ie=UTF8&psc=1>

### 2.5. Third Party Cookie

通常のCookieはファーストパーティCookieと分類され、WEBサイト自体が発行する。

対して、サードパーティcookieとは、「ユーザーが訪問しているWebサイトとは、異なるドメイン（ホスト）」から発行されるcookieのこと。例えば、とあるWebサイトに訪れた時に、訪問したドメインからcookie（ファーストパーティーcookie）が発行されるだけでなく、サイト内に広告バナーが設置されている場合には、広告配信サーバーからもcookie（サードパーティcookie）が発行されます。リターゲティング広告（追跡型広告）では、このサードパーティcookieを利用し、ユーザーを判別。特定のユーザーのWebサイト上の行動から、ユーザーの属性や興味・関心度の高い広告を配信しています。

プライバシーの問題から、禁止される方向である。

<https://moltsinc.co.jp/data-strategy/9987/>
<https://japan.cnet.com/article/35156564/>

### 2.6. Cache File

同一コンテンツを何度も送信するのを避ける機能。キャッシュファイルは、例えばWindowsだと、だいたい下記パスにある。ブラウザが持ってるといっても、具体的にはCドライブのブラウザのディレクトリにある。

> C:\Users\%USERNAME%\AppData\Local\Google\Chrome\User Data\Default\Cache

キャッシュファイルにはいくつかの種類が実はある。

- Cache：　画像や CSS などの一般的なキャッシュ
- Code Cache：　JavaScript などのキャッシュ

前回送信したコンテンツであるかどうかを判定する方法は主に2つある

- 最終更新時間
- ユニークな識別子（ETag）

ETagの方が最終更新日よりも厳密に管理できる。例えば、同じURLで、日英で内容を出しわけたい際などに有効。ETag自体は、後述するWEBサーバーのミドルウェア（Apacheなど）が生成してくれるようです。

<https://www.tipsfound.com/chrome/01001>
<https://developer.mozilla.org/ja/docs/Web/HTTP/Headers/ETag>
<https://blog.redbox.ne.jp/http-header-tuning.html>
<https://www.amazon.co.jp/gp/product/B06XNMMC9S/ref=ppx_yo_dt_b_d_asin_title_o03?ie=UTF8&psc=1>

### 2.7. TCP (Transmission Control Protocol)

HTTP通信をカプセル化したトランスポート層でのプロトコルに則った通信。コネクションの確率は次の3段階を経る

- クライアントからの接続要求：　SYN（Synchronize）パケットというデータを送る
- サーバーからクライアントに対して確認応答・接続要求：　確認応答がACK（Acknowledgement）パケット。同時に接続要求もするのでSYNパケットも送る
- クライアントからサーバーに対して確認応答：　クライアントからACKパケットを送ってコネクション確立

<https://www.amazon.co.jp/dp/B092Q8SKDB/ref=cm_sw_r_tw_dp_KGFK4GJ0GF6ARKB15YHT?_encoding=UTF8&psc=1>
<https://www.amazon.co.jp/gp/product/B06XNMMC9S/ref=ppx_yo_dt_b_d_asin_title_o03?ie=UTF8&psc=1>

### 2.8. SSL/TLS Handshake

暗号化通信の手順。

1. ブラウザから利用可能な暗号化方式の提示。サーバーがどれにするか回答
2. サーバーからSSL証明書を送信
3. ブラウザから鍵を送信
4. ブラウザから暗号化方式の確認。サーバーから確認回答

で暗号化通信が開始する。

<https://www.amazon.co.jp/gp/product/B06XNMMC9S/ref=ppx_yo_dt_b_d_asin_title_o03?ie=UTF8&psc=1>

### 2.9. URL (a Uniform Resource Locator)

図の下に記載の参考サイトより。パスはファイル名を含めたパスで、「.html」などが来ます。「.jsp」はjavaコードが含まれたHTMLファイルの拡張子です。引数はパラメータとも呼ばれ、&区切りで複数つく場合があります。

![URLの説明](2021-09-27-17-11-07.png)
<https://rainbow-engine.com/basic-domain-url/>

### 2.10. ISP (Internet Service Provider)

国内だと、NTTコミュニケーションズや、ソフトバンクなど。海外だとVerizonやAT＆Tなどのこと。ISPは階層構造をとっていて、非常に規模が大きく最上位に位置するISPがTier1です。Tier1以外のISPも相互に接続されていて、最終的にはどこかのTier1のISPにつながっています。つまり、インターネット上のすべてのISPはTier1を経由してどこかでつながっています。

![ISPの概念図](2021-09-27-17-13-59.png)

同Tier内では、ピアー（peer）と呼ばれる、無料での情報やり取りができますが、Tierが違うとトランジット（transit）と呼ばれる、上位Tierに使用料を払うことで経路情報をもらう接続が適用されます。

- Tier 1：　AT&T、Verizon、NTTコミュニケーションズ（米Verioを買収してTier1昇格）、ソフトバンク（米Sprintを買収してTier1昇格）。
- Tier 2：　日本だとOCN、KDDI、IIJなど（調べてもはっきりしない）

<https://www.soumu.go.jp/main_content/000577920.pdf>
<https://www.m2ri.jp/release/detail.html?id=424>
<https://www.n-study.com/internetworking-overview/internet-overview/>
<https://www.geekpage.jp/blog/?id=2012/10/16/1>
<https://kaiteki-netlife.com/ocn_reason/>

### 2.11. SEO (Search Engine Optimization)

Googlebotなど検索エンジンはクローラーと呼ぶ、インターネット上を徘徊するボットを動かしている。これらがサイトやページの評価を行い、検索キーワードに対するページのランキングが作られ、それが表示されている。

昔はそれこそ、大量にキーワードを含ませたり、そしたらGoogle側がそれを見破るようになったりと、イタチごっこ感もあった。Google検索の仕様変更をペンギンアップデートなどと呼んでいた（今も呼んでいるかもしれない）

基本的には小手先のテクニックではなく、そもそもユーザーにとって価値のあるサイトを真正面から作ることが一番順位をあげるコツであるという感覚。実際Googleもそういってますね。詳しくはGoogleの公式サイトにガイドが載っているので、これを見るのがいいでしょう。公式以外にも簡単にチェックできそうな記事も載せてます。

<https://developers.google.com/search/docs/beginner/seo-starter-guide>
<https://satori.marketing/marketing-blog/seo/seo-measures/>
<https://www.irep.co.jp/knowledge/blog/detail/id=45926/>
<https://prtimes.jp/main/html/rd/p/000000087.000035376.html>

### 2.12. gRPC (Remote Procedure Call)

Googleが自社サービス向けに開発して使用していたものをオープンソース化した技術で、さまざまな大規模サービスでの利用実績がある。

元々RPCという言葉はあり、これはいわゆる「クライアント−サーバー」型の通信プロトコルであり、サーバー上で実装されている関数（Procedure、プロシージャ）をクライアントからの呼び出しに応じて実行する技術である。上で紹介したHTTPベースのXML RPCや、JSON RPCなどがある。

これらは基本的にテキストベースで情報をやり取りするためデータの転送効率が悪く、またバイナリデータを扱いにくいという問題があった。また、HTTP/HTTPSを使用しているため比較的長い期間で散発的にデータをやり取りしにくかったり、転送効率の面でもオーバーヘッドが存在したりする。こういった問題を解決するために考案されたのがgRPC。現在はLinux Foundation傘下のCloud Native Computing Foundation（CNCF）によって開発が進められている。

余談なんですが、gが何を示すのかは結構調べましたが、謎です（Globalのgか、もしくはGoogleのgだと思うが）

<https://grpc.io/about/>
<https://grpc.io/docs/what-is-grpc/introduction/>
<https://knowledge.sakura.ad.jp/24059/>
<https://qiita.com/oohira/items/63b5ccb2bf1a913659d6>

### 2.13. Semantic WEB

現在のWWW（World Wide Web）は単にデータの集合であり人間がデータを解釈して初めて意味のある情報となるが，セマンティック・ウェブ（Semantic Web）はウェブページにメタデータを付加することでコンピュータが意味情報を解釈・処理することを目指す枠組み。

たとえば，「源氏物語の作者は紫式部である」という情報を自然言語で表すと「紫式部が源氏物語を書いた」「源氏物語は紫式部によって作られた」などさまざまな表現があり，これらが同一の意味を表していることをコンピュータは理解できない。いっぽう，RDFは＜主語，述語，目的語＞の3つ組でさまざまな関係を表す。たとえば上の例は＜源氏物語，作者，紫式部＞と表現する

WEB DEVELOPER Roadmap 2021だと、Learn anytime扱いとなっている。

<https://roadmap.sh/frontend>
<https://www.s.u-tokyo.ac.jp/ja/story/newsletter/keywords/17/05.html>

#### 2.13.1. RDF (Resource Description Framework)

メタ情報/メタデータを表記するための汎用的な手法を定めたデータ形式の一つ。Webサイトの更新情報を配信するRSSの原型になった仕様としてよく知られる。

<https://e-words.jp/w/RDF.html>
<https://www.w3.org/RDF/>

#### 2.13.2. OWL (The W3C Web Ontology Language)

物事、物事のグループ、物事間の関係についての豊かで複雑な知識を表現するために設計されたセマンティック・ウェブ言語。

OWLウェブ・オントロジー言語は、人間に対して単に情報を提示するのではなく、情報の内容を処理する必要のあるアプリケーションが利用できるように設計されています。OWLは、形式意味論（formal semantics）を用いて語彙を補足して提供することによって、XML、RDF、および、RDFスキーマ (RDF-S) のサポートよりもウェブ・コンテンツに対する機械解釈可能性の実現をより容易にします。OWLには、OWL Lite、OWL DL、OWL Fullの順でより表現力を持つ3つのサブ言語（sub language）が存在しています。

<https://www.w3.org/OWL/>
<http://www.asahi-net.or.jp/~ax2s-kmtn/internet/rec-owl-features-20040210.html>

### 2.14. Web Socket

Webにおいて双方向通信を低コストで行うための仕組み。プロトコルの一種。下記のようなHTTPの課題を解決するために生まれた

- 1つのコネクションで1つのリクエストしか送ることができない
- リクエストはクライアントからしか送ることができない。つまり、サーバーから通信を始めることができない

例えばFacebookのチャットアプリみたいに多数のクライアントが一つのページにアクセスしてて誰かがメッセージを投稿するとそれをその他のユーザーに通知したい場合があって、そういった時に双方向通信の必要性が出てくる。

<https://en.wikipedia.org/wiki/WebSocket>
<https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API>
<https://qiita.com/south37/items/6f92d4268fe676347160>
<https://qiita.com/chihiro/items/9d280704c6eff8603389>

## 3. Browser

受け取ったHTMLファイルを解析するレンダリングエンジンが各ブラウザには内包されている。またJavaScriptはJavaScriptエンジンで動く。それらのエンジンが、ブラウザ間で異なるために同じHTMLやJavaScriptの内容でも表示や挙動が異なる場合がある。

![ブラウザの利用調査](2021-09-27-17-27-03.png)*Which browser(s) do you primarily work in during initial development?*

<https://2020.stateofjs.com/en-US/other-tools/>
<https://www.amazon.co.jp/dp/B092Q8SKDB/ref=cm_sw_r_tw_dp_FEV5Y74CDVTH1HD880NF>

### 3.1. Browserの種類

ここでは5種類くらいしか紹介しませんが、実は新興ブラウザもどんどん誕生しています。もうとっくに勝負は決したかと思っていましたが、決して聖域ではないわけですね。とはいえ調査結果にもある通り、基本はChromeです。

#### 3.1.1. Chrome

Google。一番使われている。他のブラウザでも検索エンジン自体は同じGoogleだったりする。

レンダリングエンジンは、Blink。C++で書かれた。Chromium projectで2013年に開発・公開。JavaScriptエンジンは、V8。

<https://www.chromium.org/blink>

#### 3.1.2. Safari

Apple。iPhoneやiPadのデバイスのことを考えると使われている。特に日本ではスマホなどのデバイスはほとんどAppleだからだ。レンダリングエンジンは、Webkit。JavaScriptエンジンは、JavaScriptCore

#### 3.1.3. Firefox

Mozilla。レンダリングエンジンは、Gecko。ブラウザと同じくMozillaなどが管理。JavaScriptエンジンは、SpiderMonkey。今までのクライアントさんでもデフォルトはFirefox、というのはたまにありました。MozillaのことはFirefoxでしか知らないかもしれませんが、実は色々やっていて、後で出てきます。

#### 3.1.4. Edge

Microsoft。長年使われたIEの後継。IEはもう紹介しないけどいいよね。Googleと同じで、レンダリングエンジンは、Blink。JavaScriptエンジンは、V8

#### 3.1.5. Sidekick

Chromeと同期できるChromeみたいなブラウザ。Chromeより早くて、広告ブロックもしてくれる。最近増えていて、アーリーアダプターを中心にTwitterで人気。ただちょうど好きになってきたころに、課金のお知らせが来る（それでもやめられない快適感なのですが）

### 3.2. Rendering Engine

各社で競い合ってるが、WebkitとBlinkをご紹介。ちなみに、レンダリングエンジンは必ずしもブラウザのみで利用されるとは限りません。たとえば、メールクライアントではHTMLメールの表示をサポートするために内部にレンダリングエンジンを組み込みます。

<https://www.amazon.co.jp/dp/B0728K5JZV/ref=cm_sw_r_cp_api_glt_3RHKAG3G6TKCWGBCSZ66?_encoding=UTF8&psc=1>

#### 3.2.1. Webkit

WebKitの源流は、1990年代後半にKDEがオープンソースとして開発を進めていたKHTML（KDE HTML）というWebレンダリングエンジンにある。当時NetscapeのGecko、MicrosoftのTrident（Internet Explorer）という形で2つのメジャーなレンダリングエンジンが存在したが、それとは独立する形で進んでいた。後に、AppleがKHTMLをForkする形で分岐し、大幅な改良を加える形で誕生したのがWebKitだ。

そして次に、GoogleがオープンソースプロジェクトとしてのWebKitに積極的に関わるようになり、2008年にはWebKitをベースにしたWebブラウザー「Chrome」の発表と、そのオープンソースプロジェクトである「Chromium」の立ち上げを行なった。しかし蜜月も束の間であった（Blinkに続く）

<https://ascii.jp/elem/000/000/778/778554/2/>

#### 3.2.2. Blink

Googleが開発、ChromeやEdgeで利用。もともとGoogleはAppleと同じWebkitを使っていたが、2013年GoogleがWebKitを離れて「Blink」への移行を表明。BlinkはWebKitのForkにあたるプロジェクト。これをずっと傍から見ていたMozillaの公式にBlinkの解説ページがあるのだから、面白い

<https://saneyukis.hatenablog.com/entry/2020/02/05/002818>
<https://ascii.jp/elem/000/000/778/778554/>
<https://developer.mozilla.org/ja/docs/Glossary/Blink>
<https://www.itmedia.co.jp/pcuser/articles/1812/09/news016.html>

### 3.3. JavaScript Engine

こちらも各社で競い合っているが、代表的なV8をご紹介。

#### 3.3.1. V8

V8は、C++で書かれたGoogleのオープンソースの高性能JavaScriptおよびWebAssemblyエンジンです。ChromeやNode.jsなどで使用されています。ECMAScriptとWebAssemblyを実装しており、Windows 7以降、macOS 10.12+、x64、IA-32、ARM、MIPSプロセッサを使用したLinuxシステムで動作します。V8はスタンドアロンで動作することも、C++アプリケーションに組み込むこともできます。また、V8 エンジンは、２つのコンポーネントで構成されています。

1. Memory Heap（メモリの割り当てなど）
2. Call Stack(コードを実行するためのスタック)

<https://v8.dev/>
<https://qiita.com/ryoya41/items/fd8e46702b0f4fbe1188>

### 3.4. Critical Rendering Path

HTML,CSS,Javascriptをどう処理して画面に表示するのか。HTML、CSS、JavaScript のバイトの受信から、これらをピクセルとしてレンダリングするために必要な処理までの中間段階で行われている内容のこと。

![Critical Rendering Pathのイメージ](2021-09-27-18-33-57.png)*Critical Rendering Pathのイメージ*

そのプロセスは下記の通り。

1. Object Model の構築
2. Rendering Tree の構築
3. Rendering Tree のレイアウト
4. Rendering Tree の描画

<https://developers.google.com/web/fundamentals/performance/critical-rendering-path>
<https://qiita.com/sasakiki/items/91dcc8b50d7a61ce98bc>

#### 3.4.1. Object Modelの構築

ブラウザはページを描画する前に、DOMとCSSOMツリーを構築する必要があります。このDOMとCSSOMツリーを構築する工程を指します。

> バイト→文字列→トークン→ノード→オブジェクトモデル(DOM/CSSOM)

という流れでオブジェクトモデルは構築されます。

1. ブラウザはディスクやネットワークからHTMLのバイトを読み取り、utf8などの文字コードに応じて`<html>`や`<head>`のような文字列に変換
2. 取得した文字列をトークンに変換
3. トークンは`<html>`や`<head>`といったオブジェクトに変換
4. 字句解析で作られたオブジェクトはオリジナルのマークアップの定義に基づいた親子関係をもつ木構造に整形

<https://developers.google.com/web/fundamentals/performance/critical-rendering-path>
<https://qiita.com/sasakiki/items/91dcc8b50d7a61ce98bc>

#### 3.4.2. Rendering Tree の構築

DOMツリーとCSSOMツリーを合成してレンダーツリーを生成。

<https://developers.google.com/web/fundamentals/performance/critical-rendering-path>
<https://qiita.com/sasakiki/items/91dcc8b50d7a61ce98bc>

#### 3.4.3. Rendering Tree のレイアウト

デバイスのviewport内でそれら要素の厳密な位置やサイズを算出するレイアウトの工程が行われます(リフローとも言われます)

ページ上での個々の要素の正確なサイズや位置を求めるために、レンダーツリーのルートからブラウザはトラバースします。

<https://developers.google.com/web/fundamentals/performance/critical-rendering-path>
<https://qiita.com/sasakiki/items/91dcc8b50d7a61ce98bc>

#### 3.4.4. Rendering Tree の描画

最後に、レイアウトプロセスで得ることができた個々の要素のサイズと位置情報を最終的な正確なピクセル値へと変えるペイント(又はラスタライゼイション)の行程が行われます。それぞれの工程の合計時間を最小化することでクリティカルレンダリングパスを最適化することができます。

<https://developers.google.com/web/fundamentals/performance/critical-rendering-path>
<https://qiita.com/sasakiki/items/91dcc8b50d7a61ce98bc>

## 4. DNS (Domain Name System)

- DNS Server：　WEBブラウザからホスト名を受け取り、IPアドレスを返すサーバー
- DNS Cache Server：　実際は毎回DNSサーバーが回答してるわけではなく、一定期間はDNSキャッシュサーバーに保持され、ここから回答している

<https://www.amazon.co.jp/gp/product/B06XNMMC9S/ref=ppx_yo_dt_b_d_asin_title_o03?ie=UTF8&psc=1>

### 4.1. Registry（レジストリ）

「.com」などのトップレベルドメインを管理している組織。例えば「.com」はVeriSignが管理している。テック系で増えている「.io」はnicが管理している

### 4.2. Registrar（レジストラ）

ドメインを登録する事業者。お名前.comや、ムームードメイン、Google Domainなどが該当する

<https://www.nadukete.net/domain-guide/setting/registry-registrar.html>
<https://jp.godaddy.com/help/what-is-the-difference-between-a-registry-registrar-and-registrant-8039>
<https://www.nic.io/>

## 5. WEB Server

WEBサーバーは複数クライアントからのリクエストに、同時並行的に応答しないといけない。複数リクエストの処理には2種類ある。ポート番号はhttpならば80。httpsならば443

<https://www.amazon.co.jp/dp/B092Q8SKDB/ref=cm_sw_r_tw_dp_KGFK4GJ0GF6ARKB15YHT?_encoding=UTF8&psc=1>
<https://www.amazon.co.jp/gp/product/B06XNMMC9S/ref=ppx_yo_dt_b_d_asin_title_o03?ie=UTF8&psc=1>
<https://milestone-of-se.nesuke.com/sv-basic/linux-basic/apache-mpm-prefork-worker-event/>

### 5.1. WEB Server のタイプ

#### 5.1.1. Prefork

Prefork型。OSは実行するプロセスを高速に切り替えることで、複数のプロセスが同時並行で実行されているかのようにふるまう。この仕組みを用いるのがPrefork型。代表的なものは、Apache HTTP Server。プロセスの数が多くなるとOSのプロセス切り替え処理の割合が増えてしまい、遅くなる。C10K（クライアント1万台）問題という。

fork とは Linux のシステムコールの 1 つで、プロセスから別のプロセスを呼び出すことです。(このケースでは、ある プロセス ID を持つ httpd が、別のプロセス ID となる httpd プロセスを生成することです。）

#### 5.1.2. Event Driven

イベント駆動型。1つのプロセスで複数のリクエストを処理できる。非同期I/O（Input/Output）を利用している。ネットワークやディスクとのデータのやりとりは、CPUから見ると低速で、待ち状態が発生する。その間に別の処理を実行するのが非同期I/O。代表的なものは、nginx（エンジンエックス）。

Apache でも設定を変更すれば、このモードに出来る。

#### 5.1.3. Worker

ベースはイベント駆動型と同じ。worker 方式では 1 つのプロセスが複数のスレッドを持ちます。これにより、少ないプロセス数で多くの仕事を同時実行できるようになります。このようなプロセスを『マルチスレッドプロセス』と呼びます。

Apache でも設定を変更すれば、このモードに出来る。

### 5.2. WEB Server Middlewares

WEBサーバーの役割を担うミドルウェアをメモしていく。

#### 5.2.1. Apache HTTP Server

非営利団体のApache Software Foundationが開発・管理している

#### 5.2.2. nginx

nginx社が提供しているフリーかつオープンなWebサーバ用のソフトウェア。元々ロシアで開発された。派生系も含めたグローバルシェアは2021年に合計50％を超えて、単独のnginxにおいても下記のグラフのようにApacheを超えた。とはいえ、日本やアメリカにおいてはApacheの方が依然シェアが高い。

nginxは他のWebサーバと組み合わせて使われることが多いとされている。特にNode.jsのフロントエンドサーバとして使われることが多く、Node.jsを使っているWebサイトの53.3%がNginxを使用していると報告されている。

WebサーバとAPサーバを同一サーバに集約し、コストを抑えたいという場合は、WebサーバとしてNginx採用は最適とは言えない。NginxはApacheに比べ、Webアプリケーションでよく用いられるPHPやPerl、CGIなどで実装される動的コンテンツのようなCPUを使った処理が得意ではない。

<https://news.mynavi.jp/article/20210507-1884013/>
<https://www.sbbit.jp/article/cont1/65256>

#### 5.2.3. Cloudflare

NASDAQ上場企業のCloudflare社が提供するWEBサーバー。<https://www.cloudflare.com/ja-jp/>

#### 5.2.4. LiteSpeed

第4位のWEBサーバー。<https://www.litespeedtech.com/>

#### 5.2.5. Microsoft IIS (Internet Information Service)

Microsoftが開発・管理している

### 5.3. WEB Server Software の利用シェア

２大巨頭はNginxとApache。2021年7月はNginx、Cloudflare Server、LiteSpeedがシェアを増やし、Apacheがシェアを減らした。ApacheとMicrosoft-IISがシェアを減らし、Nginx、Cloudflare Server、LiteSpeedがシェアを増やすというのがここ数年の傾向となっている。ただし、増減のペースはほぼ一定で、数年間という比較的長いスパンでシェアの推移が起こっている。

![Usage of Web Servers](2021-09-27-18-38-11.png)
<https://news.livedoor.com/article/detail/20472752/>

### 5.4. Static Content（静的コンテンツ）

ヘルプページなど、最初から配信するコンテンツの中身が変わらないもの。この特性を生かして、効率よく配信するためのシステムをCDN（Contents Delivery Network）という。

### 5.5. CDN (Contents Delivery Network)

コンテンツキャッシュサーバーの役割も果たす。CDNを提供する事業者やクラウドサービスはいくつかある。CDNを実現する、つまり同一のコンテンツを多くのサーバでミラーする手段としては、単純なDNSラウンドロビンから、P2P、地理情報を加味した複雑な配信技術までさまざまなものがあり、研究、実用化がなされている。(左) 単一のサーバーによる配信　(右) CDNによる配信

![CDNの概念図](2021-09-27-18-51-32.png)

### 5.6. CDN 事業者

主なCDN事業者は、下記。世界的には上位3社による寡占が進んでいるらしい。日本語サイトではAmazon CloudFrontが2018年頃からここ数年1位。

- Akamai：　NASDAQ上場のCDN事業者
- Fastly：　NYSE上場のCDN事業者
- CloudFlare：　NYSE上場のCDN事業者（WEBサーバーも提供してる）
- AWS CloudFront　など

[https://ja.wikipedia.org/wiki/コンテンツデリバリネットワーク](https://ja.wikipedia.org/wiki/%E3%82%B3%E3%83%B3%E3%83%86%E3%83%B3%E3%83%84%E3%83%87%E3%83%AA%E3%83%90%E3%83%AA%E3%83%8D%E3%83%83%E3%83%88%E3%83%AF%E3%83%BC%E3%82%AF)

### 5.7. CDN で使用されている技術

- DNS ラウンドロビン：　一つのドメイン名に複数のIPアドレスを割り当てる負荷分散技術の一つ
- P2P：　複数のコンピューター間で通信を行う際のアーキテクチャのひとつで、対等の者（Peer、ピア）同士が通信をすることを特徴とする通信方式

[https://ja.wikipedia.org/wiki/DNSラウンドロビン](https://ja.wikipedia.org/wiki/DNS%E3%83%A9%E3%82%A6%E3%83%B3%E3%83%89%E3%83%AD%E3%83%93%E3%83%B3)
<https://ja.wikipedia.org/wiki/Peer_to_Peer>

### 5.8. Dynamic Content（動的コンテンツ）

動的に中身の変わるコンテンツ。WEBサーバー側で動的な処理を入れる方法は2つ。

- WEBサーバー自体に動的な処理を入れる。代表的なものはSSI（Server Side Includes）。現在はほとんど使われていない
- WEBサーバーが動的処理を行うプログラムと連携する。現在はほとんどこれ。

後者の方法もCGIをはじめとしていくつか変遷を遂げた。

### 5.9. CGI (Common Gateway Interface)

リクエストの度に毎回プログラムを起動するため、アクセスが増えると遅くなる。cgi-binフォルダにある拡張子cgiがcgiプログラム。CGIの問題を解決するために下記のような方法も生まれた

- Apache Module：　Apacheの拡張機能。ただ、Prefork型であるため、C10K問題につながった
- FastCGI：　CGIの改良版。毎回外部プログラムを起動せずに、WEBサーバーと外部プログラムとの接続を維持・常駐させた。イベント駆動型である。外部プログラムとの通信はUNIXドメインソケットなど使わなければならない

<https://www.amazon.co.jp/dp/B092Q8SKDB/ref=cm_sw_r_tw_dp_KGFK4GJ0GF6ARKB15YHT?_encoding=UTF8&psc=1>

### 5.10. WSGI (Web Server Gateway Interface)

Webアプリケーションが発展していくに伴って、数多くのフレームワークが開発されました。そしてフレームワークは、Webサーバとのやりとりの処理をそれぞれ独自に実装していました。そのためフレームワークによって使用できるWebサーバやシステム構成に制限が発生するようになってきました。 そこでフレームワークとWebサーバの間に入ってインタフェースを提供し抽象化するための規格がPythonで提案されました。それがWSGIです。

HTTPを使ってWEBサーバーと外部プログラムが連携できるため、FastCGIを使う必要がなくなった。WEBサーバーとAPサーバーが分離したケース。WSGIは、ウィスキーまたはウィズギーと発音される。

<https://www.amazon.co.jp/dp/B092Q8SKDB/ref=cm_sw_r_tw_dp_KGFK4GJ0GF6ARKB15YHT?_encoding=UTF8&psc=1>

#### 5.10.1. Libraries / Frameworks for WSGI

- Bottle：　Bottleは高速、シンプル、軽量なPython用のWSGIマイクロウェブフレームワークです。Bottleは1つのファイルモジュールとして配布され、Python標準ライブラリ以外の依存関係はありません。<https://bottlepy.org/docs/dev/>
- Falcon：　Falconは、高速なWeb APIやアプリのバックエンドを構築するためのミニマルなWSGIライブラリ。<https://falcon.readthedocs.io/en/stable/>

### 5.11. Rack / PSGI (Perl Web Server Gateway Interface)

WSGIの登場によって、Python製のフレームワークはWSGIにさえ対応すれば、どのWebサーバやシステム構成でも動作させることが可能になりました。その有用性が認識され、ほかの言語でも同様のしくみが導入されました。RubyのRack、PerlのPlackがそれに当たります。

## 6. AP Server (Application Server)

アプリケーションサーバとは、アプリケーションによって動的コンテンツを送信するミドルウェアです。Webサーバからリクエストによって、アプリケーションソフトの実行を行います。「Java」や「PHP」などで作られたアプリケーションを実行し、Webサーバに結果を返すのがアプリケーションサーバの役割。

<https://www.amazon.co.jp/dp/B092Q8SKDB/ref=cm_sw_r_tw_dp_KGFK4GJ0GF6ARKB15YHT?_encoding=UTF8&psc=1>
[https://www.fenet.jp/infla/column/technology/ソフトウェアの1つ！ミドルウェアの役割6つ｜ミド/](https://www.fenet.jp/infla/column/technology/%E3%82%BD%E3%83%95%E3%83%88%E3%82%A6%E3%82%A7%E3%82%A2%E3%81%AE1%E3%81%A4%EF%BC%81%E3%83%9F%E3%83%89%E3%83%AB%E3%82%A6%E3%82%A7%E3%82%A2%E3%81%AE%E5%BD%B9%E5%89%B26%E3%81%A4%EF%BD%9C%E3%83%9F%E3%83%89/)

### 6.1. Tomcat

無料。Tomcatとは、簡単にいうとJava サーブレットを動かすときに必要なソフトです。JavaサーブレットとはWebサーバー上で実行されるJavaのプログラムのこと。
<https://agency-star.co.jp/column/tomcat>

### 6.2. JBOSS

有料と無料どちらもある。企業向けの機能を集めたJava EE(Java Platform Enterprise Edition）を使うことができるアプリケーションサーバである。日本では、JBossというと、RedHatが販売しているJBoss Enterprise Application Platformを指す場合が多い。しかし、JBossには、WildFlyと呼ばれるオープンソースのコミュニティ版も存在している。そのため、必ずしも商用ソフトウェアの名称というわけではない。

<https://www.designet.co.jp/faq/term/?id=SkJvc3M>

### 6.3. Microsoft IIS

Microsoftのミドルウェア（WEBサーバーでもある）

<https://qiita.com/tamago3keran/items/f470593926458b7ef52a>
<https://thinkit.co.jp/article/11837>

## 7. HTML and CSS

### 7.1. HTML (HyperText Markup Language)

いくつかのバージョンがある

- HTML 1：　初期のHTML
- HTML 2：　1995年公開。フォームやテーブル、英語以外の言語の使用が可能になった
- HTML 3：　1997年1月公開。色々あって流行らなかった
- HTML 4：　1997年12月公開。充実してきた
- XHTML ：　2000年前半。XML（Extensible Markup Language）を使って定義されたHTML。利点はあったが、流行らず開発中止
- HTML 5：　2014年公開。最新で主流。2021年8月時点だとバージョンは5.2
- HTML 6：　まだ未公開。小型アップデートで時期未定で出るという噂。

<https://en.wikipedia.org/wiki/HTML>
<https://www.creativebloq.com/features/html6>
<https://www.amazon.co.jp/dp/B092Q8SKDB/ref=cm_sw_r_tw_dp_KGFK4GJ0GF6ARKB15YHT?_encoding=UTF8&psc=1>

### 7.2. DOM (Document Object Model)

W3Cが標準化・管理。HTMLはテキスト文書を扱うために構造化された言語だが、そのままではコンピュータで扱うことはできず、一度解析をして、メモリ上に構造化されたデータとして読み込む必要がある。こんなツリー上のデータ。

![DOMのイメージ](2021-09-27-18-54-54.png)

ブラウザで解析された HTMLのデータに対してデータの読み込みや変更を行いたい場合は、何らかの形で操作方法を提供する必要がある。

DOMは、 HTMLのようなマークアップ言語の文書をプログラミング言語から操作可能にするためのプログラミングインタフェース。

### 7.3. OGP (Open Graph Protocol)

FacebookやTwitterなどのSNSでシェアした際に、設定したWEBページのタイトルやイメージ画像、詳細などを正しく伝えるためのHTML要素。metaタグをHTMLソースコード内に記述することで、設定ができる。設定する際は1ページごとの画像や説明文が必要

<https://digitalidentity.co.jp/blog/seo/ogp-share-setting.html>
<https://bindup.jp/camp/marketing/promotion/27424>

### 7.4. CSS (Cascading Style Sheets)

HTMLから見栄えの機能を分離するために策定されたのがCSS。CSSはHTML 4から本格的に導入された。CSSを実現するために、HTML 4にはid、class、styleといった要素やstyleタグなどが追加されたり、linkタグを使って外部のCSSを読み込むことができるようになった。Tim Berners-Leeと一緒に働いていたHåkon Wium Lieが1994年に最初に提案した。W3Cが管理している

- CSS 1：　1996年公開。最初に策定されたCSS
- CSS 2：　1998年公開。CSS1を拡張した規格で、音声ブラウザへの対応や印刷向けの機能の追加、既存の機能の拡張などが行われた
- CSS 3：　各機能ごとにモジュールとしてまとめて別々に策定が進むようになった。なので厳密にはCSS3という塊は存在しない。あくまでモジュール単位。CSS2からさらにさまざまな機能が拡張されている。ほかにもアニメーション／要素の変形／グラデーションのような機能も追加されている。CSS3が現在主流の規格。モジュールによってはまだドラフトもある
- CSS 4：　同じくモジュール単位なので、もはや何がCSS4か曖昧。Level 4をCSS 4とみなすのであれば、いくつかのモジュールはドラフトが公開されてたりはする

<https://www.w3.org/Style/CSS/current-work>
<https://uxmilk.jp/53220>

### 7.5. Alt CSS (Alternative CSS)

CSSはHTMLの見栄えを変更することを目的に策定された。そのため変数や定数、継承のようなプログラミングに近い機能はあまり提供されていない。そこでCSSにもっとWebアプリケーション開発と親和性の高い機能を別の言語で実装し、CSSを出力する方法が開発された。このような言語を総称してAltCSSと呼ぶ。CSS Preprocessorともカテゴライズされる

- Less：　Lessは、2009年にAlexis Sellier（通称@cloudhead）によって開発されました。元々はRubyで書かれていたが、その後JavaScriptに移植された。
- Sass：　Sass（syntactically awesome style sheetsの略）は、カスケードスタイルシート（CSS）に解釈またはコンパイルされるプリプロセッサのスクリプト言語
- Stylus：　Stylusは、カスケードスタイルシート（CSS）にコンパイルされる動的スタイルシートプリプロセッサ言語です。Node.jsの元プログラマーであり、Luna言語の生みの親でもあるTJ Holowaychuk 氏によって作られました。JADEとNode.jsで書かれています。

### 7.6. CSS Frameworks

CSSでHTMLから見栄えの部分の分離ができたとはいえ、ゼロからCSSを書くのは大変です。そこでよく使われるスタイルをあらかじめ定義しておいて、それを利用する方法が考えられました。それがCSSフレームワークです。CSSフレームワークにもいくつか実装がありますが、代表的なものにBootstrap。2020年の利用率調査ではこんな感じでした。ただ、SatisfactionではTailwind CSSが1位で、Bootstrapは中位くらいでした。

![CSSフレームワークの利用実績率](2021-09-27-18-56-15.png)*利用実績率の推移。Usage = (would use again + would not use again) / total*

<https://2020.stateofcss.com/en-US/>
<https://coliss.com/articles/build-websites/operation/css/the-state-of-css-2020.html>

#### 7.6.1. Bootstrap

一番有名。世界で最も普及しているフロントエンドのオープンソースツールキットであるBootstrapは、Sass変数とミックスイン、レスポンシブグリッドシステム、豊富な組み込みコンポーネント、パワフルなJavaScriptプラグインを備えており、レスポンシブなモバイルファーストサイトを素早くデザイン、カスタマイズできます。<https://getbootstrap.com/>

#### 7.6.2. Tailwind CSS

対抗馬。最近よく聞きます。

flex、pt-4、text-center、rotate-90などのクラスが搭載されたユーティリティファーストのCSSフレームワークで、マークアップに直接組み込むことで、あらゆるデザインを構築できます。<https://tailwindcss.com/>

#### 7.6.3. Materialize CSS

まず、マテリアルデザインというものがあり、2014年に Google社によって発案されたデザインコンセプトです。主に Android のUI のために考案され、仮想的である画面のタッチ操作や見え方（ユーザインタフェース）を現実の紙のように近付けて自然な操作を実現しようというもの。

そのマテリアルデザインのページを実際に作成するためのCSSフレームワークが Materialize CSS。<https://blogk.com/1176>

#### 7.6.4. Foundation

CSSフレームワークといっていますが、htmlのテンプレートも用意されているようで、その場合はCLIをインストールすると、htmlが準備出来た段階から制作することが出来ます。[https://sterfield.co.jp/programmer/cssフレームワークfoundationを試してみた/](https://sterfield.co.jp/programmer/css%E3%83%95%E3%83%AC%E3%83%BC%E3%83%A0%E3%83%AF%E3%83%BC%E3%82%AFfoundation%E3%82%92%E8%A9%A6%E3%81%97%E3%81%A6%E3%81%BF%E3%81%9F/)

#### 7.6.5. Reactstrap

ReactでBootstrap 4を使えるようにしたライブラリ。React自体は後述。既存の CSS を React コンポーネントとして提供するもの。

サーバーレスホスティングサービスを提供している Netlify 社が開発している。

<https://reactstrap.github.io/>
<https://zenn.dev/kkeeth/scraps/dd30ae9d48f092>
<https://qiita.com/kyrieleison/items/39ce30dd2d204791a9ea>

#### 7.6.6. Material UI

Google Material Design のガイドラインに沿った React を前提とした React コンポーネントセットです。日本でも使っている人が多く、情報量も多い。

<https://mui.com/>
<https://qiita.com/kyrieleison/items/39ce30dd2d204791a9ea>
<https://zenn.dev/kkeeth/scraps/dd30ae9d48f092>

#### 7.6.7. Chakra UI

シンプルでモジュール化されたアクセス可能なコンポーネントライブラリで、Reactアプリケーションを構築するために必要なビルディングブロックを提供

<https://chakra-ui.com/>
<https://zenn.dev/sobaotto/articles/cc6db2747fc88e>

#### 7.6.8. Other CSS Frameworks

Bulma、Pure CSS、Semantic UI、Skeleton、Susy、UI Kit　など多数

### 7.7. Post CSS

ロシア人の Andrey Sitnik という人が開発している、Node.js製の「CSSツールを作るためのフレームワーク」です。PostCSS自体はただのCSSのパーサー。JavaScript（後述）のプラグインを使って、CSSを拡張/変換することができるツールという方がわかりやすいかもです。CSS Preprocessorにカテゴライズされる

公式サイトにいくつかサンプルコードが載っており、これを見ればCSSの変化前と変化後のイメージが少しわくかと思います。

<https://postcss.org/>
<https://qiita.com/morishitter/items/4a04eb144abf49f41d7d>
<https://bagelee.com/design/css/5-years-from-post-css-present-and-future/>

#### 7.7.1. Post CSS Tools

- Autoprefixer：　ベンダープリフィックスを自動で付与する
- cssnext：　未来のCSSの構文の一部を今のブラウザで解釈できるようにする
- stylelint：　カスタマイズ性に富んでいるCSSリンター

などが有名。PostCSSを使用している企業やサービスとして、Facebook, GitHub, Google等、日本では Qiitaで導入しています。

### 7.8. CSS in JS

JavaScriptを使用してコンポーネントをスタイルするテクニック。JavaScript自体は次の章で解説しますが、目的はCSSということでここで簡単にご紹介。

JavaScriptが解析されると、CSSが生成され（通常は style 要素として）、DOMに付加されます。

<https://coliss.com/articles/build-websites/operation/javascript/5-things-you-can-do-in-css-in-js.html>
<https://techlife.cookpad.com/entry/2021/03/15/090000>

#### 7.8.1. CSS in JS の主なライブラリ

- emotion：　stylis という CSS ライブラリが基盤。CSS を返す関数を定義することで、動的に スタイルを生成。クックパッドも使用している
- JSS：　CSSのオーサリングツールで、JavaScriptを使ってスタイルを宣言的に、矛盾なく、再利用可能な方法で記述可能。JSSは、ブラウザ、サーバサイド、またはNode.NETでのビルド時にコンパイルすることができます。また、JSSはフレームワークに依存しません。コア、プラグイン、フレームワーク統合など、複数のパッケージで構成されています。<https://cssinjs.org/>
- Redium：　React要素のインラインスタイルを管理するツール群です。CSSなしで強力なスタイリング機能を実現。<https://formidable.com/open-source/radium/>
- Styled-Components：　JSXのようにJavaScriptファイル内でCSSを書ける。但し、拡張子が .js とか .ts になるので、エディターやリンターによっては、拡張子に紐づいた支援ツールがうまく動かない場合もあるので注意

<https://qiita.com/jagaapple/items/7f74fc32c69f5b731159>

### 7.9. CSS Architecture

CSS の記法や設計方法について。CSS in JS も記法という意味では含まれますね。

#### 7.9.1. BEM (Block, Element, Modifier)

BEMとは、Block(かたまり)・Element(要素)・Modifier(修飾)の頭文字をとったものです。厳格なclass名の命名ルールが特徴的なCSS設計方法の一つ。下記のようなセパレータを使って記述をする（search__input などのアンスコ2つのこと）

```html
<div class="search"> <!-- Block -->
  <input class="search__input"> <!-- Element -->
  <input class="search__btn"> <!-- Element -->
</div>
```

セパレーターとは、Block、Element、Modifierを区切っている「アンダースコア２つ区切り(__)」や「ハイフン2つ区切り(--)」の区切り文字のこと。

BEMが生まれた理由は、下記の点である。つまり、HTMLとCSSがぐちゃぐちゃになりやすい歴史をかえりみて、生まれた。

1. 長期間メンテナンスできる設計で、ファーストバージョンの開発をすばやく
2. チームのスケーラビリティ
3. コードの再利用性

<https://www.codegrid.net/articles/bem-basic-1/>
<https://pikawaka.com/html-css/bem>
<https://cloudsmith.co.jp/blog/frontend/2021/03/1742107.html>
<https://qiita.com/Takuan_Oishii/items/0f0d2c5dc33a9b2d9cb1>

### 7.10. WEB Font

ちょっと細かくなりますが、WEBページを作る際に、SNSやSaaSのアイコンが欲しくなる時があります。そんな時は、Font Awesomeがいいかもしれません。他にも以下のようなものがある

- Google Fonts
- Adobe Typekit　など

#### 7.10.1. Font Awesome

WEB上でよく使用されるアイコンをWEBフォントにしたサービス。

HTMLのhead内にhrefを記述し、Font Awesomeのサイトから表示させたいアイコンの選んで、その `<i>` タグをHTMLの該当箇所にはるだけ。

<https://fontawesome.com/>

### 7.11. Image Files

JPEGやPNGなど色々あるが、それは扱ったことがあると思うので、SVGを紹介しておく。

#### 7.11.1. SVG (Scalable Vector Graphics)

「大きさを変えられるベクター画像」という意味です。PNGやJPEGなどがピクセルの集まりとして表現されるラスター画像（ビットマップ画像）であるのに対して、ベクター画像は曲線を描いたり一定の範囲を塗りつぶしたりといった処理を座標と数式によって行えることが特徴です。ベクター画像は、Adobe Illustrator や CorelDRAW などの画像編集ソフトで扱うことができます。

SVGの画像フォーマットは、HTMLやCSSをはじめとするWeb関連技術の規格策定などを行なっているW3Cによって1998年に作れられました。当時はブラウザ開発元の各社が競合技術を持っている状態だったため、なかなか普及には至りませんでしたが、その後ほとんどのブラウザがSVGに対応しています。

XMLに準拠しているため、画像なのに、テキストエディタで編集することも可能。

<https://jp.ext.hp.com/techdevice/technologysc/creator_004/>
[https://tech-blog.rakus.co.jp/entry/20201112/svg](https://tech-blog.rakus.co.jp/entry/20201112/svg#SVG%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%81%8C%E6%99%AE%E5%8F%8A%E3%81%97%E3%81%A6%E3%81%84%E3%82%8B%E3%83%AF%E3%82%B1)

### 7.12. Responsive Design

Webサイトのデザインを「閲覧ユーザーが使用するデバイスの画面サイズに応じて表示を最適化するデザイン」を指します。1つのHTMLで配信され、デバイスごとにCSSを用意して表示を変える仕組みをとっています。Googleが2021年3月にMFI（モバイル・ファースト・インデックス）へ完全移行する旨を発表したことから、さらに関心が高まっています。

レスポンシブデザインを作るには、ページのHTMLとCSSファイルにそれぞれ「meta viewportタグ」と「メディアクエリ」を記述する必要があります。

<https://semlabo.com/seo/blog/responsive_design/>

#### 7.12.1. Meta Viewport Tag

すべてのHTMLファイルのヘッダー内に、下記をいれる。

```html
<meta name=”viewport” content=”width=device-width,initial-scale=1.0″>
```

これにより、①閲覧ユーザーの使用デバイス情報の取得、②取得情報から画面横のサイズを把握してPC版・スマホ版を判断、ができるようになります。

<https://semlabo.com/seo/blog/responsive_design/>

#### 7.12.2. Media Query

閲覧ユーザーの画面サイズに応じたページサイズの切り替えができるようになります。

```css
@media screen and (min-width: 481px)　{ A }
@media screen and (max-width: 480px)　{ B }
```

1行目で「min-width: 481px」と指定することで、画面横のサイズ（CSSピクセル）が481pxに達した時に、モバイル版ページからPC版ページへと画面サイズが切り替わるようになります。Aの部分にCSSコードを入れます。2行目にはモバイル版のコードをBに入れるイメージ。

他にも方法は色々あるかとは思いますが、例えばこういう風に切り替えている。

<https://semlabo.com/seo/blog/responsive_design/>

### 7.13. User Interface Design

WEBサイトのデザインの変遷として、下記のパターンと流れがあった。絵で見た方がはやい。

#### 7.13.1. Skeuomorphism Design

![スキューモーフィズムデザイン例１](2021-09-27-19-14-45.png)
![スキューモーフィズムデザイン例２](2021-09-27-19-15-03.png)

スキューモーフィズムデザインと読む。初期のデザイン。ギリシャ由来の言葉で、リアリズムに影響を受けた実際にあるものに近しいデザイン。

初期のデザインなのですが、またブームが来ているとかいないとか。フラットデザインに飽きてくるんでしょうね。（個人的な意見ですが）

<https://b-risk.jp/blog/2020/01/skeuomorphism/>
<https://en.99designs.jp/blog/trends/skeuomorphism-flat-design-material-design/>

#### 7.13.2. Flat Design

![フラットデザイン例１](2021-09-27-20-41-48.png)
![フラットデザイン例２](2021-09-27-20-42-02.png)

現在主流。質感や立体感を取り除いたシンプルなデザイン。

シンプルな分、ページの読み込み時間も早くなったりするらしい。

<https://en.99designs.jp/blog/trends/skeuomorphism-flat-design-material-design/>

#### 7.13.3. Material Design

![マテリアルデザイン例１](2021-09-27-20-43-33.png)
![マテリアルデザイン例２](2021-09-27-20-43-47.png)

フラットデザインに少しスキューモーフィズムを追加した感じ。2014年にGoogleが提唱したデザイン。明確なガイドラインが定められたデザインであり、「見やすく、直感的に操作できるWebページ・サービス」を作ることを目的としています。

アニメーションが関係してたりもするので、実際に本家を訪れて、タッチしてみるのが早いです。

<https://material.io/develop/web/examples>
<https://tayori.com/blog/material-design/>

### 7.14. CMS (Contents Management System)

Webサイトのコンテンツを構成するテキストや画像、デザイン・レイアウト情報（テンプレート）などを一元的に保存・管理するシステムのこと。WEBアプリそのものには使わなくても（使えなくても）、それにまつわるLPやHPはまた別途必要になる、いやむしろ先に必要になるので、知っておいて損はない。

- オープンソース型：　ブログなど小規模サイト向け。代表的な製品は、WordPress、Joomla!、Drupal、Concrete5 などがある
- 商用パッケージ型：　中～大規模サイト向け。数千～数万ページ程度の中規模サイト（それでも多いけど）だと、HeartCore、NOREN。数万ページを超えるような大規模サイトだと、Sitecore、Adobe Experience Manager などがある

<https://www.hitachi-solutions.co.jp/digitalmarketing/sp/column/cms_vol01/>
<https://www.asobou.co.jp/blog/web/about-cms>

#### 7.14.1. WordPress

有名。2003年公開。PHPで書かれている。よくブログなんかで使われている。HPもこれでよいとされてきた。

#### 7.14.2. Drupal

PHPで書かれたフリーでオープンソースのウェブコンテンツ管理システムで、GNU General Public Licenseの下で配布されています。Drupalは、世界のトップ10,000のウェブサイトのうち、少なくとも13%にバックエンドフレームワークを提供しています。<https://www.drupal.org/>

### 7.15. Headless CMS

ビューを提供しないCMS。Node.js上で動作するものが非常に多くなっています。

<https://wk-partners.co.jp/homepage/blog/hpseisaku/htmlcss/headless-cms/>

#### 7.15.1. Contentful

2011年創業のドイツの会社が運営する Headless CMS 最大手。

2021年7月には175百万ドルの資金調達を行なっている。売上は10億円程度だが、3,000億円程度の企業価値がついている。すごい高いバリュエーションである（脱線しました）

日本語UIはない。

<https://www.contentful.com/>

#### 7.15.2. MicroCMS

日本製のHeadless CMS。日本語ドキュメントがあり、サポートも日本語。2017年創業のベンチャーmicroCMS（旧会社名ウォンタ）が開発・運営。元ヤフーのメンバー。すごい。

<https://microcms.io/>

## 8.  JavaScript

本編を特に詳しく扱います。

Webの初期のころに使われていたNetscape Navigatorというブラウザ上で動作する言語として実装された。当時Javaが大きな注目を浴びていた言語であったため、JavaScriptという名前が付けられた。ECMAScriptとして仕様が標準化。プロトタイプベースのオブジェクト指向が採用されているため型付が緩くバグになりやすい。ブラウザ上で動かすことがほとんど。大文字小文字を区別する。

色んな技術の外観はこんな感じ。右上は利用も満足度も高い。左上は利用は少ないが満足度は高い。

![JavaScript周りの技術](2021-09-27-20-56-44.png)

<https://2020.stateofjs.com/en-US/technologies/>

### 8.1. ECMA Script

MozillaとMicrosoftが別々に開発してたのでECMA(エクマインターナショナルが間を持った結果ECMAスクリプトという仕様名になった。（結局フレームワーク側でまた色んなものが開発されているが・・・）

- ECMAScript 1、2、3：　それぞれ1997年、1998年、1999年公開。まだ流行ってない頃
- ECMAScript 4：　うまく仕様決まらず、公開もされず2003年破棄
- ECMAScript 5：　2009年公開。各ブラウザに実装されていた機能を十分に織り込んだ本格的なバージョン
- ECMAScript 2015：　Version 6に該当。2015年公開。ここからVersion番号ではなく年が使われる。クラスベース寄りの機能が実装された。また変数のスコープや再代入不可の変数の定義ができるなど、プログラムをより安全に書くための機能も追加されている。
- ECMAScript 2016～2021：　以降、毎年6月に公開されている

<https://en.wikipedia.org/wiki/ECMAScript>
<https://stackoverflow.com/questions/186244/what-does-it-mean-that-javascript-is-a-prototype-based-language>
<https://chomado.com/programming/type-safety/>

#### 8.1.1. Prototype-based VS Class-based

JavaScriptはプロトタイプベースのオブジェクト指向言語。

クラスベースのオブジェクト指向は抽象クラスから具象オブジェクトを生成するのに対して、プロトタイプベースでは抽象クラスが存在せず実態のあるオブジェクトがオブジェクトを直接継承します。その、継承元になったオブジェクトをプロトタイプと言います。

Javascriptで全てはオブジェクトで、クラスベース言語でいうところのインスタンスのみだと思えば良い。

<https://qiita.com/awakia/items/8ff451ca5f8ae0122be7>

<https://www.wantedly.com/companies/ashita-team/post_articles/298904>

### 8.2. Alt JS / JavaScript Flavors

JavaScriptに何らかの機能を追加したい場合は、ブラウザのJavaScriptエンジンに実装が必要。かつ実装するだけでは駄目で、ユーザーに新しいブラウザへアップデートしてもらう必要がある。ユーザーは必ずしも新しいブラウザにバージョンアップしてくれるとは限らないので（特に企業ユースの場合）、新しい機能が使えるようになるには時間がかかる。そこでJavaScriptに何らかの機能を実装するときに別の言語で実装し、古いバージョンでも動作するJavaScriptを出力する方法が開発された。これらのJavaScriptを出力する言語をalternative JavaScript、通称AltJSと呼ぶ

#### 8.2.1. CoffeeScript

古くからある

#### 8.2.2. TypeScript

Microsoftが開発・保守しているプログラミング言語。JavaScriptの厳密な構文スーパーセット（上位集合）であり、オプションで静的な型付けが追加されています。（Node.jsやDenoのように）クライアントサイドとサーバーサイドの両方で実行されるJavaScriptアプリケーションの開発に使用することができます。

#### 8.2.3. JavaScript Flavors の利用率

TypeScriptの利用率が圧倒的。グラフは割愛したが、満足度も93％で1位。

<https://2020.stateofjs.com/en-US/technologies/javascript-flavors/>

![TypeScriptの利用実績率](2021-09-27-20-59-46.png)*利用実績率の推移。Usage = (would use again + would not use again) / total*

### 8.3. Front-End JS Frameworks

ここ数年はReactとVueがリード。Svelteが猛追している。

#### 8.3.1. React

React（React.jsまたはReactJSとも呼ばれる）は、UIやUIコンポーネントを構築するための、フリーでオープンソースのフロントエンドJavaScriptライブラリ。SPAやモバイルアプリケーションの開発において、ベースとして使用することができる。 JSで書かれており、2013年リリース。どうやら、2021年現在最も人気がある

#### 8.3.2. Vue.js

Vue.js（通称Vue、発音は/vjuː/で「ビュー」と同じ）は、UIやSPAを構築するためのオープンソースのMVC型フロントエンドJavaScriptフレームワーク。 Evan Youによって作成され、同氏をはじめとする現役のコアチームメンバーによってメンテナンスされている。TypeScriptで書かれており、2014年リリース

<https://www.amazon.co.jp/gp/product/B07X6F1C2P/ref=ppx_yo_dt_b_d_asin_title_o01?ie=UTF8&psc=1>

#### 8.3.3. Svelte

スヴェルト。人気急上昇中。Rich Harrisが作成。OSSとして公開されているJSコンパイラ。

コード量が少なくて済む特徴がある。ReactやVue.jsと大きく異なる特徴として、Svelteは仮想DOMを持ちません。仮想DOMはDOMのコピー、比較、更新とだいたい3つのステップを経て画面に変更が反映されますが、これを実現するためには一定量のオーバーヘッドコード（仮想DOMの処理が含まれるコード）をビルド時にバンドルしなければなりません。

実行時に仮想DOMを使用してアプリケーションコードを解釈するReactとは対照的に、ビルド時にアプリケーションをJavaScriptに変換するコンパイラです。この仕組みにより、Svelteは軽量かつ高速に動作。

#### 8.3.4. Angular

GoogleのAngularチームが中心となり、個人や企業のコミュニティによって運営されている、TypeScriptベースのフリーかつオープンソースのWebアプリケーションフレームワーク

#### 8.3.5. Front-End JS Frameworks の利用率や満足度

利用率ではReactがこの数年1位。Angularも高いが満足度が相対的に低い。満足度の高さと利用率の伸びでみるとSvelteの勢いはすごい。

<https://2020.stateofjs.com/en-US/technologies/front-end-frameworks/>

![Front-End JS Frameworks の利用実績率](2021-09-27-21-01-26.png)*利用実績率の推移。Usage = (would use again + would not use again) / total*

![Front-End JS Frameworks の満足度](2021-09-27-21-01-51.png)*満足度の推移。Satisfaction = would use again / (would use again + would not use again)*

#### 8.3.6. Other Alt JS

他にもかなりの種類がある。ありすぎて説明しきれない。

- Vanilla.js：　Vanilla JSは、超高速軽量クロスプラットフォームフレームワーク。<https://qiita.com/nobkz/items/9c79f019f93335ee5140>
- Lit：　lit-htmlは、軽量で拡張可能なHTMLテンプレート用JavaScriptライブラリで、LitElementと合わせて、あるいは単独で使用することができる。LitElementは、軽量のWebコンポーネントを開発するためのJavaScriptライブラリ。<https://www.infoq.com/jp/news/2019/08/polymer-lit-html-element-release/>
- Solid.js：　最近 1.0 が公開された JavaScript の UI フレームワーク。①JSX テンプレート、②仮想DOMなし、③事前コンパイルによって、フレームワークのコードが「消える」、④パフォーマンスが高い、といった特徴があります。
<https://zenn.dev/jay_es/articles/2021-07-24-solidjs>
- Alpine.js：　Vue, React, Angular 等の SPAツールの 超シンプル版。当初は7kb(gzipped), 今は機能が増えてそれでも11kb。Vueの58kbよりもかなり軽い。<https://qiita.com/kohashi/items/ae8b1186567ec34b2a75>
- Mithril.js：　クライアントサイドのJavaScript MVCフレームワーク。Mithrilはgzipされた状態でたったの7.8kbしかありません。Mithrilは、ハイパフォーマンスなレンダリング速度を持つ、仮想DOMの差分更新機能を持ったテンプレートエンジンや、関数型によるハイレベルなモデリングのサポート、ルーティング機能、コンポーネント化をサポート。公式に日本語ページがある。<http://mithril-ja.js.org/getting-started.html>
- Ember.js：　幾多のクライアントサイドMVCフレームワークのひとつ。表面的にはRails臭がするのですが、中身はガチのMVCであり、データバインディングやコンポーネントなどの機能を提供。<https://dev.classmethod.jp/articles/hello-emberjs/>
- Backbone.js：　RESTfulなJSONインターフェースを備えたJavaScriptライブラリで、モデル・ビュー・コントローラのアプリケーションデザインパラダイムに基づいています。CoffeeScript, Underscore.js などの作者である Jeremy Ashkenas が作っている。あくまで Backbone（背骨）であり、骨組みを用意するのみ。
<https://qiita.com/opengl-8080/items/36e9b380c64ba7766511>
- htmx：　AJAX、CSSトランジション、WebSocket、Server Sent Events に、属性を使って HTML 内で直接アクセスできるため、ハイパーテキストのシンプルさと力強さを備えた最新のUIを構築することができます。htmx は小さく (10k min.gzipped)、依存性がなく、拡張性があり、IE11 と互換性があります。<https://htmx.org/>

### 8.4. Runtime for JavaScript (and TypeScript)

Runtimeは実行環境。サーバーサイドもJavaScriptでやる利点は、サーバーサイドとクライアントサイドが同じ言語になり、同じ技術者がサーバーとクライアント両方を開発しやすくなり、通常なら必要となる双方の技術者間の仕様のすり合わせなどが少なくなり、開発コストが押さえやすくなること。

![JS Runtimeの利用調査](2021-09-27-21-03-11.png)*Which engines/runtimes/execution environments do you regularly use?*

<https://2020.stateofjs.com/en-US/other-tools/>
<https://persol-tech-s.co.jp/hatalabo/it_engineer/225.html>

#### 8.4.1. Node.js

ブラウザの外で動くJS環境。Node.jsは、V8エンジン上で動作し、Webブラウザの外でJavaScriptコードを実行する、オープンソースでクロスプラットフォームのバックエンドJavaScript実行環境です。サーバーも該当するが、ブラウザ外ならばローカルでもよい。

Node.jsは、開発者がJavaScriptを使ってコマンドラインツールを書いたり、サーバーサイドスクリプティングを行うことを可能にします。C、C++、JavaScriptで書かれており、2009年にリリースされました。イベント駆動型でノンブロッキングI/Oである。

ちなみに、Node.js REPL (Read-Evaluate-Print-Loop) とは、Nodeの対話インタプリタのこと。ローカルにインストールすると使える。

<http://www.w3big.com/ja/nodejs/nodejs-repl.html>
<https://digitalidentity.co.jp/blog/creative/javascript-nodejs.html>

#### 8.4.2. Deno（ディーノ）

Node.jsと同じ人が作って2018年に公開した。Node.jsで後悔したことを逆に詰め込んだJS/TSランタイム。Denoは、V8 JavaScriptエンジンとプログラミング言語「Rust」をベースにした、JavaScriptおよびTypeScript用の実行環境です。Node.jsの生みの親であるRyan Dahl氏によって開発されました。期待は高いが、まだまだ出たところなので、利用は少ない。

<https://deno.land/>
<https://yosuke-furukawa.hatenablog.com/entry/2018/06/07/080335>
<https://qiita.com/azukiazusa/items/8238c0c68ed525377883>
<https://youtu.be/M3BM9TB-8yA>

#### 8.4.3. npm (Node Package Manager)

NodeやDenoなどランタイムと同じ階層の話ではありませんが。。

Node.jsのパッケージ（Package ）を管理する（Manager）ツールです。2009年にオープンソースとして開発・公開。運営する npm, Inc. は、2014年に設立された会社で、2020年にGitHubに買収された（そしてGitHubはMicrosoftの傘下である）。

Node.jsで開発を行う際に欠かせない。代表的なパッケージ例は下記

- promise：　非同期処理を分かりやすく実装できます。
- async：　promise同様非同期処理を実装できます。
- Socket.io：　双方向のリアルタイムアプリケーションを実装できます。チャットアプリなど実際に動くサービスを開発する際に必要となります

<https://www.npmjs.com/>
<https://techacademy.jp/magazine/16105>
<https://qiita.com/shuari/items/75d8d938a80a27b4ba0a>

### 8.5. Back-End JS Frameworks

バックエンドの分野はまだ非常に細分化されていますが、Expressは圧倒的な存在感を示しており、Next.jsは高い満足度を維持しています。

WEBアプリ開発における必須のスキル「MERN」という言葉がありますが、MERNのEはExpressのEですから、そのあたりの言葉にも如実に表れています。ちなみにMはMongoDB、RはReact、NはNode.jsです。

![Back-End JS Frameworks の利用実績率](2021-09-27-21-05-33.png)*利用実績率の推移。Usage = (would use again + would not use again) / total*

![Back-End JS Frameworks の満足度](2021-09-27-21-06-01.png)*満足度の推移。Satisfaction = would use again / (would use again + would not use again)*

<https://2020.stateofjs.com/en-US/technologies/back-end-frameworks/>

#### 8.5.1. Express.js

最小限の機能と柔軟性を備えたNode.jsのWebアプリケーションフレームワークで、Webおよびモバイルアプリケーションのための堅牢な機能を備えています。APIを提供しています。

#### 8.5.2. Next.js

Vercelが開発・公開。Node.jsの上に構築されたオープンソースの開発フレームワーク。GitHubスター73,200。

サーバーサイドレンダリングや静的なWebサイトの生成など、ReactベースのWebアプリケーションの機能を実現します。Reactのドキュメントでは、"Recommended Toolchains "の中にNext.jsが含まれており、"Node.jsでサーバーレンダリングされたWebサイトを構築する "際のソリューションとして開発者にアドバイスしています。JavaScriptとTypeScriptで書かれています。

ディレクトリ構造とURL構造が連動しているので、ルーティング用のファイルなどは存在しない。

<https://qiita.com/jagaapple/items/faf125e28f8c2860269c>
<https://zenn.dev/razokulover/scraps/94844e54e519ed>

#### 8.5.3. Nuxt.js

Vue.js、Node.js、Webpack、Babel.jsをベースにした、フリーでオープンソースのWebアプリケーションフレームワークです。Nuxtは、React.jsをベースにした同様の目的のフレームワークであるNext.jsに影響を受けています。JavaScriptで書かれています。

ディレクトリ構造とURL構造が連動しているので、ルーティング用のファイルなどは存在しない。

<https://www.amazon.co.jp/gp/product/B08NSZJZ4Q/ref=ppx_yo_dt_b_d_asin_title_o09?ie=UTF8&psc=1>
<https://www.amazon.co.jp/gp/product/B07X6F1C2P/ref=ppx_yo_dt_b_d_asin_title_o01?ie=UTF8&psc=1>

#### 8.5.4. Sapper

Next.jsにインスピレーションを受けて開発された、Svelteのフレームワーク。Sapperは基本的にはサーバサイドでコンポーネントをレンダリングし、HTMLとしてクライアントに送信するSSR（Server Side Rendering）を採用しています。2021年2月時点では、Svelteのバージョンはv3.32.1、Sapperのバージョンはv0.29.1です。バージョンを見てわかるとおり、Sapperはまだベータ版

#### 8.5.5. SvelteKit

現在はSapperの後継であるSvelteKitの開発がプライベートリポジトリで進んでいるようです。とはいえ、公式ドキュメントによるとSapperで構築したアプリケーションはSvelteKitに移行可能

#### 8.5.6. Blitz.js

ざっくり言うとReact版Ruby on Railsです。Reactの面倒なところを全てすっ飛ばし、技術選定なんてどうでもいいから今すぐアプリを動かしたいんだよ、という要望を叶えるのに適したフルスタックフレームワーク。技術的にはReact + Next.jsで動いています。

<https://qiita.com/rana_kualu/items/69ef668e240ae9ccec87>
<https://qiita.com/nitaking/items/edfaae19d0b54aae7f9c>

### 8.6. Build Tool / Bandler for Alt JS

Node.jsスタイルのコードは、そのままの状態ではブラウザで動きません。 ソースコードを元にして、実際に動くプログラム（実行可能ファイル）を作ってあげる必要があります。 その作成処理のことを ビルド と言います。

バンドラとは、HTTP/1.1接続ではブラウザとウェブサーバーの同時接続数が限られるため、複数のファイルの転送に時間がかかります。複数のJSファイルを1つにまとめてしまうことが一般的な解決案として知られています。

webpackの優位性で議論が決着したかと思いきや、Snowpackやesbuildなどの新規参入者によってビルドツールのシーンが再び爆発的に増え、State of JSのサイトにおいても、2017年以来のフルセクションを設けられた。

![ビルドツールの利用実績率](2021-09-27-21-11-55.png)*利用実績率の推移。Usage = (would use again + would not use again) / total*

![ビルドツールの満足度](2021-09-27-21-12-25.png)*満足度の推移。Satisfaction = would use again / (would use again + would not use again)*

<https://2020.stateofjs.com/en-US/technologies/build-tools/>
<https://qiita.com/yukibe/items/453d874eb7ce929363d6>
<https://ics.media/entry/12140/>
<https://qiita.com/TsutomuNakamura/items/70dd97dcbdc02bef2706>

#### 8.6.1. Webpack

ウェブコンテンツを構成するファイルをまとめてしまうツール。一番多い使い方は、複数のJavaScriptを1つにまとめることでしょう。複数のJavaScriptをまとめるのは、上述した転送の最適化以外にもいろんな利点がある。Babel.jsと一緒に使われることが多い。<https://ics.media/entry/12140/>

#### 8.6.2. Rollup.js

Rich Harrisが作成。JSモジュールバンドラ。

#### 8.6.3. Vite

Vue.jsの作者のEvan You氏が開発中のノーバンドルなビルドツールです。ネイティブのESモジュールのインポートを利用しバンドル不要で高速に動作するdevサーバーと、Rollup.js をベースとしたプロダクションビルド機能を提供します。設定不要で「.vue」のSFC（Single File Components）をコンパイルできて、さらにデフォルトで今開発中のVue3.0が使えます。しかも、vue-cliのようにVue.js限定ではなく、React、Preactにも対応
<https://qiita.com/ryo2132/items/c1530dd590e34e68c494>

#### 8.6.4. Stencil.js

stencilはUIフレームのionicで利用されているWeb Componentをビルドするフレームワーク。<https://blog.cntlog.net/archives/4242>

### 8.7. Transcompiler for Alt JS

#### 8.7.1. Babel.js

マルチブラウザ対応してくれるトランスコンパイラ。Babelは、フリーでオープンソースのJavaScriptトランスコンパイラで、主にECMAScript 2015+（ES6+）のコードを、古いJavaScriptエンジンで実行可能な後方互換性のあるバージョンのJavaScriptに変換するために使用されます。2014年公開。JSで書かれている。バンドラのWebpackと一緒に使われることが多い。<https://www.cresco.co.jp/blog/entry/11716/>

### 8.8. CLI for Alt JS (a Command-Line Interface)

メモ程度であまり紹介しませんが・・・

- EXPO：　React用CLI。Expoは環境構築にかかる時間がほぼゼロで、エミュレーターをPCにインストールすることなくスマホにExpoというアプリをインストールするだけで開発を開始できる。しかもreact-nativeの機能を全て使える。パフォーマンスも悪くない。初学者が触るならこれだ。<https://ncdc.co.jp/columns/6959/>

### 8.9. State Container for JS

#### 8.9.1. Redux

Reactが扱うUIのstate(状態)を管理をするためのフレームワーク。Reactではstateの管理するデータフローにFluxを提案していますが、ReduxはFluxの概念を拡張してより扱いやすく設計されています。下記の3つの原則がある

1. Single source of truth：　アプリケーション全体の状態(state)はツリーの形で１つのオブジェクトで作られ、１つのストアに保存される
2. State is read-only：　状態を変更する手段は、変更内容をもったactionオブジェクトを発行して実行するだけ
3. Mutations are written as pure functions：　アクションがどのように状態を変更するかを「Reducer」で行う。「Reducer」は状態とアクションを受けて、新しい状態を返す関数

Reduxの主な機能は以下。

- Action：　アクション（何が起きたのか）とそれに付随する情報を持つオブジェクト。ActionをStoreへdispatch（送信）すると、Storeのstateが変更される。stateの変更は必ずActionを経由して行う
- Reducer：　上述したが、Storeから受け取ったActionとstateに応じて、変更されたstateを返す純粋関数（同じ引数を渡されたら必ず同じ結果を返す関数）
- Store：　アプリケーションの全てのstateを保持するオブジェクト。ActionをStoreにdispatchする手段（`store.dispatch()`）を提供する。また、stateとdispatchされたActionを、指定したReducerに渡してstateを変更する。

<https://redux.js.org/>
<https://qiita.com/soarflat/items/bd319695d156654bbe86>
<https://qiita.com/kitagawamac/items/49a1f03445b19cf407b7>
<https://future-architect.github.io/articles/20200429/>

#### 8.9.2. Flux

Facebook社が提唱している、クライアントサイドのWebアプリケーション開発のためのアプリケーション・アーキテクチャ（設計思想）です。単方向のデータフローを構築できることが最大の特徴で、開発の規模が大きくなってもデータの流れを見失いづらいことが大きなメリットです。Reactとの併用を主に想定して生み出された。

この思想に基づいて、Facebookがその方法を提供しているライブラリもまた、Fluxという。

<https://codezine.jp/article/detail/10751>
<https://qiita.com/knhr__/items/5fec7571dab80e2dcd92>

#### 8.9.3. MobX

FacebookやCoinbaseなど多数のスポンサーによって運営されている団体が開発してる、React状態管理ライブラリ。

<https://mobx.js.org/README.html>

#### 8.9.4. Jotai

Paul Henschel 氏が開発・運営しているReact状態管理ライブラリ。読み方は日本語の「状態」。

<https://jotai.pmnd.rs/>
<https://github.com/pmndrs/jotai>
<https://www.infoq.com/jp/news/2020/09/jotai-react-state-management/>
<https://zenn.dev/kkeeth/articles/studying-jotai-library>

#### 8.9.5. Vuex

Vue用の状態管理ライブラリ。一択。

<https://zenn.dev/kkeeth/scraps/dd30ae9d48f092>

### 8.10. Virtual DOM

jQueryでは処理するたびにDOM操作をしますが、DOM操作は処理が重くたくさんやりすぎると速度低下の原因になります。

DOM操作は毎回やる必要がなく、どこかに溜めておいて一気に反映させても問題ありません。そこでDOM操作を一時的にメモリ上に保存しておいて、定期的に実際のDOMへ一度に反映させるVirtual DOMというしくみが考案されました。

Virtual DOMの生成や変更はただのメモリ操作なので高速に処理できます。 そしてVirtual DOMの木構造と実際のDOMの木構造を比較し差分を抽出して、差分の内容だけをDOMに反映させます。このようにすることでDOM操作を最小に抑え、描画速度を高速化。

Virtual DOMを採用したフレームワークには、代表的なものとしてReactやVue.jsがある

#### 8.10.1. Shadow DOM

Virtual DOMと同じかと思って読み飛ばしてましたが、違うものです。（なので、Virtual DOMにネストして書くのも違うのですが、ついでにメモ）

Shadow DOM は、本来 web components において変数や CSS をスコープ化するために設計されたブラウザ技術。その役割はDOMツリーのカプセル（構造やスタイル、挙動を隠し、同じページの他のコードと分離すること）化である。

Shadow DOM により、通常の DOM ツリーの要素の下に DOM ツリーを追加し隠すことができます。shadow DOM ツリーは shadow root を根とし、その下には普通の DOM ツリーと同様に任意の要素を追加できます。

<https://ja.reactjs.org/docs/faq-internals.html>
<https://developer.mozilla.org/ja/docs/Web/Web_Components/Using_shadow_DOM>

### 8.11. Source Map

AltJSで書いても、実際にブラウザ上で実行されるのはJavaScriptである。そうすると、JavaScriptに何らかのエラーが発生した場合に、元のコードとの対応関係の特定が難しくなってくる。

そこでブラウザ側でAltJSをサポートする機能として、Source Mapというものが提供されている。 Source Mapにはブラウザで実行しているJavaScriptと、実際に記述したAltJSとの対応関係の情報が格納されている。

Source Mapに対応したブラウザであれば、その情報を読み取って実行しているJavaScriptのコードがAltJSで記述した元のコードのどこに対応しているのかを表示してくれる。

<https://qiita.com/pegass85/items/b9aae1adf51646707486>

### 8.12. Data Format

#### 8.12.1. JSON (JavaScript Object Notation)

JavaScriptのオブジェクトの書き方を元にしたデータ定義方法。通信時のデータ形式。JSONの方が文字数が少なく可視性は低いが、その分軽い。またJSが読み込む際に、XMLの場合はDOMにしないといけないが、JSで書かれたJSONは生で扱えるため、処理が早い。

現在はJavaScript以外にもPythonやJava、PHPなどの幅広い言語で使われていて、JavaScriptなどのクライアント言語とPythonなどのサーバサイド言語間のデータのやり取りで使われることが多い。

```json
{"menu": {
  "id": "file",
  "value": "File",
  "popup": {
    "menuitem": [
      {"value": "New", "onclick": "CreateNewDoc()"},
      {"value": "Open", "onclick": "OpenDoc()"},
      {"value": "Close", "onclick": "CloseDoc()"}
    ]
  }
}}
```

<https://products.sint.co.jp/topsic/blog/json>
<https://qiita.com/momonoki1990/items/cd9a65498c2b16b0ed55>

#### 8.12.2. XML (Extensible Markup Language)

XMLはHTMLの記法を元にしたデータ定義方法で、データ定義言語と呼ばれています。JSONが登場する前まではXMLというデータ構造が主に使われていました。CSVよりも複雑な構造も扱える。ただ、例えばJavaScriptの場合、扱うデータ形式がXMLだとXML構文を解析する必要がでてくるので、プログラムのパフォーマンスが低下するというデメリットがある

インターネット上で使用される各種技術の標準化推進団体である、W3C（World Wide Web Consortium）によるオープンな規格です。

```xml
<menu id="file" value="File">
  <popup>
    <menuitem value="New" onclick="CreateNewDoc()" />
    <menuitem value="Open" onclick="OpenDoc()" />
    <menuitem value="Close" onclick="CloseDoc()" />
  </popup>
</menu>
```

<https://hnavi.co.jp/knowledge/blog/xml/>
<https://products.sint.co.jp/topsic/blog/json>

#### 8.12.3. BSON (Binary JSON)

BSONは主にMongoDB（後述）のデータストレージ及びネットワーク転送フォーマットとして利用されている、データ交換フォーマットである。 単純なデータ構造や連想配列（MongoDBではオブジェクトまたはドキュメントと表す）を示すバイナリ構造である。JSONに比べて、ストレージ容量及びスキャン速度に効率的な設計である。

MongoDBのパートで出てきた方がいいのですが、JSONとの比較の文脈として先に登場させてます。例えば、バックアップコマンド実行時に作られます。

```wasm
\x16\x00\x00\x00               // total document size
\x02                           // 0x02 = type String
hello\x00                      // field name
\x06\x00\x00\x00world\x00      // field value (size of value, value, null terminator)
\x00                           // 0x00 = type EOO ('end of object')
```

<https://ja.wikipedia.org/wiki/BSON>

#### 8.12.4. YAML (YAML Ain't Markup Language)

人間が読み書きしやすい構造化データを扱う仕様です。拡張子は.yamlまたは.yml。YAML自体は仕様なので、各プログラミング言語でYAMLを扱うための実装が必要となります。JavaScriptの場合はYAMLを扱うためのライブラリとしてjs-yamlが存在。

GitHub ActionsやCIサービスの設定ファイルとしても利用されています。たとえば、ReactのリポジトリにはCircleCIの設定ファイルがあります。YAMLの公式サイト自体もYAML形式？

```yaml
---
 doe: "a deer, a female deer"
 ray: "a drop of golden sun"
 pi: 3.14159
 xmas: true
 french-hens: 3
 calling-birds:
   - huey
   - dewey
   - louie
   - fred
 xmas-fifth-day:
   calling-birds: four
   french-hens: 3
   golden-rings: 5
   partridges:
     count: 1
     location: "a pear tree"
   turtle-doves: two
```

<https://yaml.org/>
<https://www.codegrid.net/articles/2020-yaml-1/>
<https://qiita.com/Yama-to/items/587544993fb62610528a>
<https://www.cloudbees.com/blog/yaml-tutorial-everything-you-need-get-started>

### 8.13. Ajax (Asynchronous JavaScript and XML)

WEBブラウザではなく、ブラウザ上で動くJavaScriptがWEBサーバーと通信を行う。JavaScriptの機能を使った非同期通信であり、リクエスト中にレスポンスを待つだけでなく、レスポンスによらない部分を更新したり、ユーザーの入力を受け付けたりできる。

黎明期のJavaScriptは、Webページに多少の動きを加えるのが主な役割でした。あくまで静的なHTMLがベースで、近年のようにダイナミックな動きを伴うものではありませんでした。そこにXMLHttpRequest (XHR) という機能が実装されました。 XMLHttpRequest (XHR) を使うと、JavaScriptがサーバと通信してデータを取得できるようになります。このXMLHttpRequest (XHR) の機能を活用し、デスクトップアプリケーションと遜色ないサービスを提供したのがGoogle Mapsでした。

#### 8.13.1. Google による Ajax の先行事例

それまでの地図サービスは移動や拡大縮小をするたびに読み込みが発生していましたが、Google Mapsはデスクトップアプリケーションのようにマウス操作でスムーズな動きを実現することに成功したのです。 このようにXMLHttpRequest (XHR) を活用しJavaScriptがサーバと通信する技術がAjaxと呼ばれ、注目を浴びることになります。

また、GoogleスプレッドシートのようなUIは、サーバーサイドの開発のみでは実現できません。「文字入力する度にリロードされてフォーカスが消し飛ぶスプレッドシートとか使ってられないですね。」こちらより抜粋。

<https://teratail.com/questions/138648>

### 8.14. Animation

#### 8.14.1. GSAP (GreenSock Animation Platform)

GreenSock 社が開発しているアニメーション制作のJavaScriptのライブラリ。ジーサップと読む。

GSAP は JavaScript が触れることのできるあらゆるもの（CSS プロパティ、キャンバス ライブラリ オブジェクト、SVG、React、Vue、ジェネリック オブジェクトなど）をアニメーション化し、数え切れないほどのブラウザの不整合を解決します。また、トランスフォームの自動 GPU アクセラレーションを含め、すべてが驚異的なスピード（jQuery の最大 20 倍）です。

Google が JS ベースのアニメーションに GSAP を推奨しているのも、主要な広告ネットワークがファイルサイズの計算から GSAP を除外しているのも、GSAP が地球上で最も堅牢で高性能な JavaScript アニメーションライブラリであるから、らしい（公式サイトより）

<https://greensock.com/gsap/>
<https://qiita.com/takeshisakuma/items/97a7f702ec3c4f656525>
<https://liginc.co.jp/548232>

### 8.15. その他の JavaScript / React の概念や機能

WEB開発ロードマップで必須知識となっていたものを拾ってきてます。開発者でなくても知っているといいですね。よい開発者は技術のことを知っててほしいと願っているわけですから、リスペクトが必要です。

#### 8.15.1. Event Bubbling

要素上でイベントが起きると、最初にその上のハンドラが実行され、次にその親のハンドラが実行され、他の祖先に到達するまでそれらが行われます。たとえば、3つのネストされた要素 `FORM > DIV > P` があり、それぞれにハンドラがあった場合、一番ネストされたpタグのハンドラから実行される。この下から実行される感じが水中のリングの泡に似てるよね、から来てる。

公式から持ってきた例は下記。onclickがハンドラ。

```jsx
<style>
  body * {
    margin: 10px;
    border: 1px solid blue;
  }
</style>

<form onclick="alert('form')">FORM
  <div onclick="alert('div')">DIV
    <p onclick="alert('p')">P</p>
  </div>
</form>
```

<https://ja.javascript.info/bubbling-and-capturing>

#### 8.15.2. Scope

変数がどの場所から参照できるのかを定義する概念です。言い換えれば、変数の有効範囲ということです。同じスコープ上にある変数にはアクセスできますが、スコープが違えば、別々のスコープにある変数にはお互いにアクセスすることができません。これがある理由はいくつかあります

- 変数名重複を回避：　関数やブロックごとに別々のスコープが作られるため、プログラム内で同じ名前の変数があってもスコープが違えば別物になってくれる。これなら、変数名がかぶることを気にしなくて済む
- 無駄なメモリ消費を回避：　JavaScriptには、使われなくなったメモリ領域を自動的に解放するガベージコレクションという仕組みがある。もしスコープがなければ、すべての変数がグローバルに属することになります。そして、グローバルに属する変数はプログラムから参照され続けるため、ガベージコレクションされません。つまり、ページを閉じるまでの間ずっと、不要なメモリ領域を確保し続けてしまいます。

また、Scopeはいくつかの種類・タイプがあります

1. Global Scope：　プログラムのトップレベルで宣言された変数は、グローバル変数となり、プログラム全体のどこからでもアクセス可能
2. Local Scope：　ローバル変数以外のすべての変数は、ローカルスコープを持つローカル変数
    - Function Scope：　関数（function）ごとに作られるスコープ。関数スコープ内でvar、let、constのいずれかで変数宣言をすると、関数の外部からはアクセスできない
    - Block Scope：　ブロック（{}）ごとに作られるスコープ

<https://www.codegrid.net/articles/2017-js-scope-1/>
<https://www.w3schools.com/js/js_scope.asp>

#### 8.15.3. Strict Mode

ECMAScript 5 で導入された。JavaScriptのコードをより厳しくエラーチェックすることができる仕組みです。通常エラーとなっていなかったバグになりそうなコードに対して、エラーを表示することができます。

例えば、evalやwithといったレガシーな機能や構文を禁止します。それだけでなく、将来の ECMAScript で定義される予定の構文の使用を禁止してくれる

例えば下記の1行を入れると出来る。

```jsx
"use strict";
```

<https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Strict_mode>

<https://www.sejuku.net/blog/58342>

#### 8.15.4. Fast Refresh

Fast RefreshはNext.js（または React Native）の機能で、Reactコンポーネントに加えられた編集を瞬時にフィードバックすることができます。Fast Refreshは、9.4以降のすべてのNext.jsアプリケーションでデフォルトで有効になっています。Next.jsのFast Refreshを有効にすると、コンポーネントの状態（ステート）を失うことなく、ほとんどの編集内容が1秒以内に表示されます。

<https://reactnative.dev/img/homepage/ReactRefresh.mp4>

Hot Reloading との違いは、基本は似ているようですが、いくつかあり、

- 変更後にリロードされないことが多かったのが、なくなった
- Fast Refreshの機能自体が、Reactに組み込まれている
- Hooks付きの関数コンポーネントをサポート
- リロードしてもStateを保持する

<https://nextjs.org/docs/basic-features/fast-refresh>
<https://reactnative.dev/blog/2019/09/18/version-0.61>
<https://zenn.dev/uttk/scraps/f25adbba87e1ba>
<https://qiita.com/ryohey/items/2b6b94d00d3d2320f0e2>

#### 8.15.5. JSX

JavaScript を拡張して、UI 要素を記述するのに HTML のようなタグ構文が使えるようにしたもの。babelというツールで変換している。HTMLタグのように見えていたものの実態は単に関数で、単にJSでViewを構築するための簡易記法である

<https://react.keicode.com/basics/jsx.php>

## 9. WASM (Web Assembly)

ブラウザ上でより高速に実行するため新しく登場したのがWasm。Wasmは高速実行するために、ブラウザ上で直接実行するようなバイナリ形式を使用します。開発者はCやRustのような別言語でプログラムを書いてWasmを出力する。ロードマップにおいても最新のテクノロジーであるが、まだ普及していないし、この次の5年間でJavaScriptに取って代わるかというとそこまではいかないのでは？と思われている。だが重たいWEBアプリなどを皮切りに、シェアは拡大すると思われる。

2015年にMozilla Foundationによって発表され、その後World Wide Web Consortium（W3C）は、Mozilla、Microsoft、Google、Apple、Fastly、Intel、Red Hatの協力を得て、この規格を維持しています。

通常の開発はJavaScriptを中心に記述し、高速な処理を必要とする部分をRustで記述してWebAssemblyでブリッジすることで、使いやすさと安全面と速度を手に入れることができそう。

<https://dev.classmethod.jp/articles/rust-webassembly-javascript/>
<https://roadmap.sh/frontend>
<https://inzkyk.xyz/mozilla_hacks/wasi/>

### 9.1. WASMはどのくらい速いのか

何で測るかによりますが、シンプルな計算速度という意味で、フィボナッチ関数を何秒で計算できるかをJSと比較したサイトがありましたので、載せておきます。計算量が少なければ差はわずかですが、計算量が大きくなってくると差も歴然としてきます。やっぱり速いですね。

<https://thinkit.co.jp/article/17486>
<https://blog.htmlhifive.com/2019/04/02/webassembly-performance/>

### 9.2. Rust

C言語やC++に代わるオープンソースのシステムプログラミング言語です。2015年にバージョン1が登場したまだ新しい言語。Firefoxの開発元のMozillaが2009年から支援。2006年に開発がスタートした当初は、Mozilla所属のグレイドン・ホアレ氏の個人プロジェクトだった。WASMを吐き出すための言語というわけでは全然ないのですが、一緒に注目されることがあります。2016年、2017年、2018年のStack Overflow Developer Surveyで「最も愛されているプログラミング言語」で一位。見てみると2021年も1位でした。すごい愛されてる

Mozillaが2012年に開発を開始したWebレンダリングエンジン「Servo」がRustを用いられている他、Microsoftは2019年11月から、同社のコアプラットフォームであるWindowsの開発にRustを採用していることを公表。そしてGoogleは、2021年4月に同社のコアプラットフォームであるAndroid OSの開発にRustを採用すると発表している。

C言語に匹敵する処理速度を持っているが、習得難易度が高い言語ともいわれる。また、Rustはすべての変数が常に値を持つ構造をしているため、nullが基本的に存在しない言語でもある。Rustでの開発が適していると言えるのは、大規模なシステム開発とアプリケーション開発。

<https://www.rust-lang.org/ja>
<https://www.pasonatech.co.jp/workstyle/column/detail.html?p=2611>
<https://atmarkit.itmedia.co.jp/ait/articles/2107/28/news010.html>
<https://qiita.com/elipmoc101/items/3c8b6d8332a9019e578c>
<https://insights.stackoverflow.com/survey/2021#technology-most-loved-dreaded-and-wanted>
<https://docs.microsoft.com/ja-jp/learn/modules/rust-introduction/>
<https://zenn.dev/akfm/articles/81713d4c1275ac64a75c>

### 9.3. WASI (WebAssembly System Interface)

WASMはブラウザで動かす際のバイナリファイルですが、その実行環境はブラウザを飛び出し、Node.jsでも直接利用できるようになりました。WASIは、 WebAssembly（WASM）をウェブブラウザ以外の環境で実行するため、 ホストのファイルやネットワークなどの資源に安全にアクセスさせるための仕様、標準化の取り組みのことです。

CDN事業者のFastly、Cloudflareは、彼らのエッジで実行されるFaaS的なサービスでWASMを使っています。Intelはウェブブラウザ以外でのOSSのWASM実行環境の開発を進めています。他にもWASIには現時点でMozilla、Node.js、npmが賛同している

<https://wasi.dev/>
<https://medium.com/nttlabs/wasi-6060b243ac90>
<https://qiita.com/massie_g/items/40726e237594817bfee7>
<https://www.publickey1.jp/blog/19/webassemblywebwasimozillanodejs.html>
<https://inzkyk.xyz/mozilla_hacks/wasi/>

### 9.4. WASM Runtime

サーバー側でバイナリ形式のファイルであるWASMをそのまま実行することは出来ないので、一度WASMランタイムがコード変換する必要があります。WASIをサポートするWASMのランタイムとして、

- wasmtime：　Rustで作られた、リファレンス実装的なランタイム。<https://wasmtime.dev/>
- Lucet：　CDN業者Fastlyが開発するランタイム
- WebAssembly Micro Runtime(WAMR)：　組み込みデバイスで動かすことを前提とした軽量ランタイム。
- WASMER：　パッケージマネージャーや、PHP/Rubyなどのスクリプト言語からの呼び出しも対応。<https://wasmer.io/>

などがある。

<https://medium.com/nttlabs/wasi-6060b243ac90>
<https://qiita.com/massie_g/items/40726e237594817bfee7>

### 9.5. Rust Web Frameworks

RustのWebフレームワークをいくつか紹介していく。日本語記事もほとんどないので、薄めの情報だが、メモ程度に。

<https://youtu.be/c2o9JSzgITQ>

#### 9.5.1. Rocket

Rustで書かれたWebフレームワーク。Rails、Flask、Bottle、Yesod に影響を受けて開発された。2016年登場。

<https://rocket.rs/>
<https://en.wikipedia.org/wiki/Rocket_(web_framework>)
<https://qiita.com/yukinarit/items/c5128e67d168b4f39983>

#### 9.5.2. Actix-web

まず、actixとは、Rust製のActorフレームワーク。そのactixをベースとしてWeb開発用機能を追加したのが、軽量・高速なWeb開発フレームワークであるactix-web。

<https://actix.rs/docs/whatis/>
<https://dev.classmethod.jp/articles/actix-web/>
<https://qiita.com/Yoshihiro-Hirose/items/2426fe5199cb1ff74bd7>

#### 9.5.3. Warp

Warpは、コードやインフラの実行、デバッグ、デプロイにおいて、チームの生産性を向上させるために作られたターミナルです。WarpはRustで作られたフルネイティブのアプリで、すべてのレンダリングをGPUで行います。Warpを使うことで、すべての開発者がCLIのベテランのように生産性を上げることがWarpの目標。

<https://www.warp.dev/>

#### 9.5.4. Tide

Tideは、迅速な開発のために作られた、ミニマルで実用的なRustのWebアプリケーションフレームワークです。非同期のWebアプリケーションやAPIの構築をより簡単に、より楽しくするための堅牢な機能を備えています。

<https://docs.rs/tide/0.16.0/tide/index.html>

#### 9.5.5. Gotham

安定性、安全性、安心感、そしてスピードを促進する柔軟なRustのウェブフレームワークです。

<https://gotham.rs/>

## 10.  Server Side Script

主にAPサーバーで活躍する。色々な言語がある。

- Ruby、Perl、PHP、Python
- Go：　Googleによって開発された、静的型付け言語になります。「Go」といった言語名がググりにくいためか、「Golang」の呼び方が親しまれています。並行処理が言語レベルでサポートしており(goroutine)、コンパイルの速さ、メモリ安全性、パフォーマンスの良さから、ここ数年採用されるケースが増えている気がします。また、フレームワークを使わないケースが増えている言語
- Java：　Sun Microsystems社（後にOracle社が買収）のJames Gosling氏によって開発された。有名すぎるので省略する。
- Scala：　オブジェクト指向プログラミングと関数型プログラミングの両方をサポートする、強力な静的型付けされた汎用プログラミング言語
- Kotlin：　JetBrain社が開発。クロスプラットフォームの静的型付けされた、型推論機能を持つ汎用プログラミング言語。KotlinはJavaと完全に相互運用できるように設計されており、JVM版のKotlinの標準ライブラリはJava Class Libraryに依存していますが、型推論によって構文をより簡潔にすることができます。
- Nim：　全然ランク外ですが、、静的型付けで型安全な上にPythonっぽい構文でコード量も少なく済む「効率的、表現力豊か、エレガント」なプログラミング言語です。コンパイラが優秀すぎて、勝手に最適化して実行バイナリのサイズを小さくしてくれるし速い。誤解を恐れずに表現するなら「Pythonの皮を被ったC/C++」。
<https://nim-lang.org/>
<https://qiita.com/happy_packet/items/3c59abf9875f4f6869c9>
<https://ja.wikipedia.org/wiki/Nim>
- F#：　これまた写ってませんが・・・、OCaml という言語をベースに開発された2プログラミング言語で、C# の速度・クロスプラットフォーム性・ライブラリの多さ・開発環境、Python のオフサイドルール、Haskell のモナド文化、静的ダックタイピング(事実上のトレイト/型クラス)、コンパイル時型生成(type providers)、といった要素を兼ね備えています。<https://qiita.com/cannorin/items/59d79cc9a3b64c761cd4>

![JS以外の利用言語](2021-09-27-21-25-43.png)

<https://2020.stateofjs.com/en-US/other-tools/>
<https://qiita.com/inagacky/items/43cc0518ef11f1e4beb3>

### 10.1. Python Frameworks

Pythonは機械学習の人気も相まって、今最も人気のあるサーバーサイドスクリプトです。動的型付け言語。同じ数の空白でインデントされたまとまりを一つのブロックと認識します。Webアプリケーションやデスクトップアプリケーションといった様々なシステムの開発が行えます。科学計算、機械学習の分野において採用されるケースが多い

![Pythonフレームワークの利用調査](2021-09-27-21-27-00.png)

<https://www.jetbrains.com/lp/python-developers-survey-2020/>

#### 10.1.1. Flask

JetBrain社のサーベイだと利用率は1位。

Djangoに比べて、軽量なマイクロフレームワークです。標準で提供する機能を最小限に保っているようで、拡張性が高く、シンプルなフレームワークです。

#### 10.1.2. Django

Model-Template-View（MTV）アーキテクチャに基づいた、フルスタックフレームワークです。フレームワークに要求される機能がほとんど実装されています。PythonでWebアプリケーションを作る場合に、採用されることが多いです。

#### 10.1.3. Fast API

PythonのWeb frameworkで、Flaskのようなマイクロフレームワークにあたります。パフォーマンスの高さ、書きやすさ、本番運用を強く意識した設計、モダンな機能などが強みです。FastAPI は Starlette の肩に乗る形で書かれており、非同期処理が扱いやすい。日本語記事あり。<https://qiita.com/bee2/items/75d9c0d7ba20e7a4a0e9>

#### 10.1.4. Tornado

FriendFeedで開発されたPythonのWebフレームワークであり、非同期ネットワークライブラリ。ノンブロッキングネットワークI/Oを使用することで、Tornadoは何万ものオープンコネクションに対応することができ、長時間のポーリングやWebSocketなど、各ユーザーへの長期的な接続を必要とするアプリケーションに最適。<https://www.tornadoweb.org/en/stable/>

#### 10.1.5. Web2py

高速でスケーラブル、安全でポータブルなデータベース駆動のWebベースのアプリケーションを迅速に開発するための、無料のオープンソース・フルスタックフレームワーク。<http://www.web2py.com/>

#### 10.1.6. Pyramid

小さなウェブアプリを大きなウェブアプリにすることを目的とした、軽量のPythonウェブフレームワークです。<https://trypyramid.com/>

#### 10.1.7. Mako

Pythonで書かれたテンプレートライブラリです。慣れ親しんだ非XMLの構文を提供し、最大のパフォーマンスを得るためにPythonモジュールにコンパイルされます。月に10億以上のページビューがあるreddit.comで使用されている。<https://www.makotemplates.org/>

### 10.2. PHP Frameworks

#### 10.2.1. Laravel

ウェブ開発者のためのPHPフレームワーク。<https://laravel.com/>

#### 10.2.2. Symfony

Web アプリケーション、API、マイクロサービス、Web サービスを構築するための、再利用可能な PHP コンポーネントのセットであり、PHP フレームワーク。<https://symfony.com/>

### 10.3. Java Frameworks

個人的にはJavaは使わないのですが、一応メモ。

#### 10.3.1. Spring

あらゆる種類のデプロイメント・プラットフォーム上で、最新のJavaベースのエンタープライズ・アプリケーションのための包括的なプログラミングおよび構成モデルを提供。<https://spring.io/projects/spring-framework>

他にもたくさんあると思いますが、あまり使用しないので1つだけです・・・

### 10.4. Async Technologies for Python / Django

ワードの紹介にとどまりますが。Djangoから受けたアンケートの設問にも、「どういうAsync Technologiesを使っていますか？」というのがあったので、日本語記事は少ないですが、Djangoの団体は気にしてるようです。

#### 10.4.1. ASGI (Asynchronous Server Gateway Interface)

WSGIと呼ばれるPythonのWebサーバとWebアプリケーションが通信するためインタフェース定義の後継仕様となっており、WebSocketと非同期をサポートするように設計されているもの。<https://note.com/keyem/n/nc6d879ed59a4>

#### 10.4.2. AnyIO

AnyIO は asyncio や trio の上で動作する非同期ネットワーキングおよび同時実行ライブラリです。asyncioの上にtrioのような構造化された同時実行（SC）を実装し、trio自体のネイティブなSCと調和して動作します。<https://anyio.readthedocs.io/en/stable/>

#### 10.4.3. asgiref

リンクのみ・・・。<https://github.com/django/asgiref>

#### 10.4.4. asyncio

async/await 構文を使い 並行処理の コードを書くためのライブラリです。asyncio は、高性能なネットワークとウェブサーバ、データベース接続ライブラリ、分散タスクキューなどの複数の非同期 Python フレームワークの基盤として使われています。<https://docs.python.org/ja/3/library/asyncio.html>

#### 10.4.5. Channels

Channels は、Django の機能を HTTP 以外にも拡張し、WebSocket やチャットプロトコル、IoT プロトコルなどを扱えるようにするプロジェクトです。ASGIと呼ばれるPythonの仕様に基づく。  <https://channels.readthedocs.io/en/stable/>

#### 10.4.6. Curio

タスク、ソケット、ファイル、ロック、キューなどの標準的なプログラミングの抽象化を提供。<https://curio.readthedocs.io/en/latest/>

#### 10.4.7. Daphne

DaphneはDjangoプロジェクトのメンバーによって開発されたUNIX用の純Python製ASGIサーバです。ASGI のリファレンスサーバとして機能しています。プロトコルの自動ネゴシエーションをサポートしており、WebSocketのエンドポイントとHTTPのエンドポイントを判断するためのURLプレフィックスは必要ありません。<https://pypi.org/project/daphne/>

#### 10.4.8. Quart

QuartはPythonのWebマイクロフレームワークです。Quartを使うと以下が出来る。

1. HTMLテンプレートのレンダリングと提供
2. RESTfulなJSON APIの作成
3. WebSocketの提供
4. リクエストおよびレスポンスデータのストリーム
5. HTTPまたはWebSocketプロトコル上であらゆることが可能

<https://pgjones.gitlab.io/quart/>

#### 10.4.9. Responder

Responder は Requests や Pipenv の開発者として知られる Kenneth Reitz 氏によって開発された Web フレームワークです。Responder のコンセプトは、人気の Web フレームワークである。Flask と Falcon の両方から良い部分を取り入れ、さらに Kenneth Reitz 氏の持つ新しいアイデアを加えることで、新しい一つのWeb フレームワークに統合すること。<https://qiita.com/nskydiving/items/b98d5cea5a52459cb183>
<https://qiita.com/y_k/items/6e4da3bef5c8d8bd2730>

#### 10.4.10. Sanic

SanicはPython 3.7+のWebサーバとWebフレームワークで、高速に動作するように書かれています。Python 3.5で追加されたasync/await構文を使用することができ、ノンブロッキングで高速なコードを実現します。<https://github.com/sanic-org/sanic>

#### 10.4.11. Starlette

FastAPIが乗っている巨人のひとつである、Starlette は ASGI Framework/toolkit の一つです。処理が簡単になるだけでなく、効率的に実行するように非同期処理が工夫されており、高速です。<https://qiita.com/bee2/items/d629d8acc102cf92b7b2>

#### 10.4.12. trio

「async I/O for humans and snake people」を名乗るライブラリ。stack overflowの「asyncioとtrioって何が違うの？curioってライブラリもあるそうなんだけど…」という質問に、trioの"primary author"でcurioの"contributor"でもある Nathaniel J. Smith さんが以下のように答えています。

1. asyncio のほうが成熟したライブラリだ
2. trioはコードをもっとシンプルにしてくれる、など。詳細はこちら。<https://kiito.hatenablog.com/entry/2018/12/26/110317>

#### 10.4.13. Uvicorn

光速のASGIサーバーです。<https://www.uvicorn.org/>

#### 10.4.14. Hypercorn

Hypercornは、sans-ioのhyper, h11, h2, wsproto ライブラリをベースに、Gunicornにインスパイアされて開発されたASGI Webサーバーです。Hypercornは、HTTP/1、HTTP/2、WebSocket（HTTP/1およびHTTP/2上）、ASGI/2、ASGI/3の各仕様をサポートしています。Hypercornは、asyncio、uvloop、またはtrioのワーカータイプを利用できます。  <https://github.com/pgjones/hypercorn>

## 11. Web API (Application Programming Interface)

ブラウザからではなくプログラムからWebサーバにアクセスしてデータを取得し活用したいという要望が出てきました。そこでWebのしくみを使ってデータを提供するWeb APIというしくみが登場。

Web APIではプログラムに対してデータを提供するのが目的なので、レスポンスにHTMLが使われることはありません。代わりにプログラムが扱いやすいデータフォーマットを使用します。よく使われるのがJSONやXMLのようなフォーマット。

APサーバーとDBサーバーのやりとりもAPIですね。外部システムとのやりとりにはIFファイルベースのやりとりもありますが、APIではファイルは介さず、データのやりとりとなります。

### 11.1. RESTful API

REST（Representational State Transfer）は、APIを定義するときに使われる設計思想です。プロトコルではない。RESTに従ったAPIのことをRESTful APIと呼びます。 RESTはステートレスなプロトコルを使って、一意に指定可能なリソースに対して操作するという方法になっています。

ステートレスなプロトコルはHTTPそのものであり、一意に指定可能なリソースはURLに対応します。またリソースの操作はHTTPリクエストのメソッドに対応しています。

#### 11.1.1. RESTful API のデータ例

下記は、RESTful API の POST の例です（body 部分は XML）。XML の部分は JSON でもOKです。

```http
POST /api/2.2/auth/signin HTTP/1.1
HOST: my-server
Content-Type:text/xml

<tsRequest>
  <credentials name="administrator" password="passw0rd">
    <site contentUrl="" />
  </credentials>
</tsRequest>
```

<https://help.tableau.com/current/api/rest_api/en-us/REST/rest_api_concepts_example_requests.htm>

#### 11.1.2. Postman

Postmanは、Web APIのテストクライアントサービスのひとつ。1500万人以上の開発者がPostmanを使用しています。

<https://qiita.com/zaburo/items/16ac4189d0d1c35e26d1>
<https://www.postman.com/>
<https://qiita.com/zaburo/items/16ac4189d0d1c35e26d1>

### 11.2. GraphQL

RESTはリソースに対して操作をするという設計なので、複数リソースのデータを取得しようと思った場合、APIに複数回アクセスする必要があります。データ取得の効率を考えると、APIにアクセスする回数を減らして一度に取得するデータを多くしたほうがよいです。 そこでRESTよりも効率良くAPIからデータを取得する方法としてGraphQLが考案されました。

GraphQLはFacebookにより提案され標準化が進んでいます。今後はGraphQLを採用したAPIも増えていくでしょう。

#### 11.2.1. GraphQL のデータ例

型情報を持ったスキーマを定義し、そのスキーマに対してクエリを叩く。

まずスキーマの例。Queryはデータ取得を行うqueryのための型で、meというフィールドを持っています。meはUser型であることを示しています。User型は、文字列型のnameと整数型のageを持ちます。

```graphql
type Query {
  me: User
}
type User {
  id: ID
  name: String
  age: Int
}
```

このスキーマに対して、GetMeというクエリを投げて、meのnameをゲットします

```graphql
query GetMe {
  me {
    name 
  }
}
```

すると下記のようなデータが返ってくる

```graphql
{
  "me": {
    "name": "Luke Skywalker"
  }
}
```

<https://graphql.org/learn/queries/>
<https://www.amazon.co.jp/dp/B0912GHNCN/ref=cm_sw_r_cp_api_glt_TXXAJ2N11WA8AHAPJB1D?_encoding=UTF8&psc=1>

#### 11.2.2. Hasura

PostgreSQL サーバーから自動的に GraphQL サーバーを建てられるツール。Docker イメージとして配布されていて、対象となる PostgreSQL サーバーのアドレスや PW を設定して起動すればすぐに GraphQL サーバーとして使えます。

テーブル定義から自動でGraphQL APIを生成する。柔軟な検索ができるクエリメソッドや、Create, Update, Deleteなども自動生成され、シンプルだが十分なCRUDができる。

<https://hasura.io/>
<https://hasura.io/learn/ja/graphql/hasura/introduction/>
<https://qiita.com/yuno_miyako/items/4a4f68a473231f8c07cd>
<https://qiita.com/maaz118/items/9e198ea91ad8fc624491>
<https://speakerdeck.com/shinnoki/hasura-tohahe-zhe-ka-meritutodemerituto?slide=17>

#### 11.2.3. Apollo GraphQL

ApolloはGraphQLのフロントエンド＆バックエンドのライブラリです。バックエンド側はApollo Server、フロントエンド側は Apollo Clientを導入する必要があります。

またGraphiQLというVisual Editorがツールとして付属しているのでAPIの動作確認を簡単に行うことができます。Apollo を利用することで、あらゆるデータが GraphQL サーバーとして集約されます。

![Apolloのイメージ図](2021-09-27-21-48-32.png)

こうすることでバックエンドの複雑性が Apollo によって隠蔽され、クライアントおよびバックエンドは Apollo サーバーとの接続にのみ注意すればよくなる

<https://www.apollographql.com/>
<https://qiita.com/teradonburi/items/2ad98c7c21f1f6cc4390>
<https://qiita.com/jintz/items/4ddc6bf4f95238eff5e9>

### 11.3. Webhook

Webサービスがサービス内で起こったイベントをトリガーに、所定のURLにパラメータを渡してコールしてくれる機能。

例えばGitHubのWebhookはリポジトリにプッシュ時、コミット情報をパラメータとしてPOSTリクエストする。そのため、プッシュ時にコミット情報をSlackに通知をしたり、メールに通知できる。

<https://twitter.com/rapid_api/status/1436066031735300097?s=21>
<https://qiita.com/soarflat/items/ed970f6dc59b2ab76169>

## 12. WEB Application

### 12.1. SPA (Single Page Application)

WebアプリケーションをサーバAPIとフロントエンドの構成の単一ページとして実装するのがSPAです。 最近はSPAを使ってほとんどネイティブアプリケーションと遜色のない操作性を提供するWebアプリケーションも増えてきています。

ユーザーから見た感じは普通にページ遷移もしますし、その際のURLも変わります。が、実際に使われているHTMLファイルは1つで、JS側からブラウザに対してURLを変える操作をしているそうです。（下記リンクのGIFがわかりやすい）

#### 12.1.1. SPA と SEO

ちなみに、SPAで制作されたWebサイトはJavaScriptでコンテンツを描画しているため、Googlebotに正しく認識されずSEOの観点で問題が生じるのではないかという懸念の声がしばしば聞かれます。しかし、現在のGooglebotには、Chrome 74相当のレンダリングが搭載されており、最新のJavaScript技術に対応しています。ですので、SPAで制作されたWebサイトが何らかSEO上で不利になるということは考えられないでしょう。

このアップデートはGoogle I/O 2019にて発表され、[アメリカ版Googleウェブマスター向け公式ブログ](https://webmasters.googleblog.com/2019/05/the-new-evergreen-googlebot.html)でも告知されています。

<https://www.cresco.co.jp/blog/entry/11716/>

<https://qiita.com/ozaki25/items/41e3af4679c81a204284>

### 12.2. SSR (Server-Side Rendering)

世の中のシステムにはブラウザからではなく、プログラムからアクセスして処理するようなシステムもあります。そのようなシステムではSPAのWebアプリケーションを正常に処理できません。SPA構成のアプリケーションでも一部サーバサイドで処理をする必要が出てきます。そういった用途のために一部サーバ側で処理をすることをSSRと言います。SPA構成のアプリケーションを開発するときはSSRをどうするかを考慮する必要は出てくるでしょう。

<https://qiita.com/jagaapple/items/faf125e28f8c2860269c>

### 12.3. SSG (Static Site Generator)

アプリのビルド時にあらかじめページ表示に必要なデータを取得し、各ページごとに静的なHTMLファイルを出力しておく。そしてサーバーへのリクエスト時にはこのHTMLファイルを返却する。

たとえばヘルプページなんかはユーザーごとに表示するコンテンツが変わるわけではない。それなら最初から静的なファイルとして用意しておけばよくね？的な発想。（しかし、実態はヘルプページへの適用にとどまらない）

ブラウザが静的なHTMLファイルを取得するのはサイトへの初回リクエスト時のみで、ページ遷移時には代わりにJSONファイルを取得し、動的に変化する部分はこのJSONファイル内のデータを使ってレンダリングするため速い。

もはやSSRは不要で、SSGで十分だとNext.jsやVercelを開発したVercelが主張しているらしい。Next.jsはSSRでもあり、SSGとしても使える。

<https://tech.bitbank.cc/20210201/>
<https://qiita.com/jagaapple/items/faf125e28f8c2860269c>

#### 12.3.1. Hugo

Hugoは、Goで書かれた静的サイトジェネレーターです。2013年にSteve Franciaによって作成されました。

#### 12.3.2. Jekyll

静的サイトジェネレータです。好きなマークアップ言語で書かれたテキストを用意すれば、Jekyllはレイアウトを合成して静的サイトを作成する。Rubyで書かれている
公式日本語ページはこちら。<http://jekyllrb-ja.github.io/docs/>

#### 12.3.3. ASP.NET

無料。クロスプラットフォーム。オープンソース。.NETとC#でWebアプリケーションやサービスを構築するためのフレームワーク。<https://dotnet.microsoft.com/apps/aspnet>

#### 12.3.4. ASP.NET Core

ASP.NETは、.NETプラットフォーム上でWebアプリケーションを構築するための一般的なWeb開発フレームワークです。ASP.NET Coreは、macOS、Linux、Windowsで動作するオープンソース版のASP.NETです。ASP.NET Coreは2016年に初めてリリースされ、初期のWindowsのみのバージョンのASP.NETを再設計したもの。<https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core>

#### 12.3.5. Gatsby.js

Reactで作られた静的サイトジェネレーター（SSG）。Gatsby社が開発・運用。2021年9月時点でGitHubスター51,300。

内部的にGraphQLを用いてデータを取得し、markdownからHTMLを生成、などの処理を簡単に行うことができます。愛情のある記事があったので詳しくは下記リンク。

ちなみにディレクトリ構造とURL構造が連動しているので、ルーティング用のファイルなどは存在しない。

Gatsbyでは独自のデータレイヤーを持っており、そのレイヤーとReactコンポーネントのやり取りをGraphQLというクエリ言語で行う。また、そのGraphQLを簡単に扱えるGraphiQLというIDEもついてくる。ビルド時はこのGraphQLで取得したデータも含めて静的化するので別途GraphQLサーバーは必要ない。

<https://www.amazon.co.jp/dp/B0912GHNCN/ref=cm_sw_r_cp_api_glt_TXXAJ2N11WA8AHAPJB1D?_encoding=UTF8&psc=1>
<https://qiita.com/hppRC/items/00739eaf9ae7fc95c1ca>
<https://tech.bitbank.cc/20210201/>

### 12.4. PWA (Progressive Web Apps)

ブラウザ上で利用するウェブサイトですが、ユーザーはまるでパーソナライズ化されたアプリのように利用することができます。「Service Worker」というスクリプトを使用することで、様々な機能を実装することができます。たとえば、

- アプリを操作中に画像を表示する「スプラッシュスクリーン」
- ユーザーに合わせてメッセージを送る「プッシュ通知」
- GPS機能の利用で実現できる「提供するコンテンツのパーソナライズ化」

などの機能があります。

そして、「インストールの必要がない」、「常にアップデートされる」、「HTTPSを利用できる」などメリットも多い。PWAであればアプリのインストールは必要ないので、不具合が発見されても修正してサーバーに修正プログラムを乗せるだけ。多くの企業のサイトで導入されています。一例として、

- starbucks.com（スターバックスのホームページ）
- suumo（不動産に関する情報サイト）
- Alibaba（世界有数のECサイト）

「コンテンツをキャッシュする」という仕組みがあり、これは主に「オフラインでも動作する」ということと、「高パフォーマンス（サイト上での操作が高速になる）」という二つのメリットを実現しています。

PWA.Rocksには、インスピレーションを得るためのプログレッシブアプリの例が多数あります。

<https://www.e-xtreme.co.jp/topics/2238/>
<https://www.seleqt.net/programming/web-development-trends-2019-3/>

### 12.5. Hybrid Application

ネイティブアプリとWebアプリのメリットを組み合わせたものが「ハイブリッドアプリ」です。WEBアプリやPWAはあくまでブラウザ上で動きますが、ハイブリッドアプリはブラウザ上で動くのではなく、OS標準搭載のWebViewで動きます。

PWAより早い？がNative Appよりは遅い。でもアップデートはサーバー側でできるので再配布がいらない。

もちろん開発言語はネイティブと違い、いつものHTML、CSS、JSでよいので開発コストが下がりやすい。スマホのOSアップデートの影響も受けにくい。

<https://www.nttcoms.com/service/mobileweb-smartphoneapp/column/20200924/>

### 12.6. Hybrid App Frameworks

こちらも色々あるが、代表的なのは以下の3つ。

- React Native
- Flutter
- Ionic

他にも様々なフレームワークが存在する。

- PhoneGap、Xamarin、NativeScript、Kendo UI、Framework7　など

<https://www.mobileappdaily.com/best-hybrid-app-frameworks>
[https://www.wecode-inc.com/blog/アプリ開発のフレームワークは何を選ぶべきか/](https://www.wecode-inc.com/blog/%E3%82%A2%E3%83%97%E3%83%AA%E9%96%8B%E7%99%BA%E3%81%AE%E3%83%95%E3%83%AC%E3%83%BC%E3%83%A0%E3%83%AF%E3%83%BC%E3%82%AF%E3%81%AF%E4%BD%95%E3%82%92%E9%81%B8%E3%81%B6%E3%81%B9%E3%81%8D%E3%81%8B/)

#### 12.6.1. React Native

2015年にFacebookが開発したモバイル用のJavaScriptのフレームワークの「React」をモバイルで利用できるようにしたもの

#### 12.6.2. Flutter

2018年にGoogleによって開発された「Dart」という言語を使って開発を行うモバイルアプリフレームワーク

#### 12.6.3. Ionic

Cordova 上で使う UI フレームワークとしても、最も人気のあるフレームワークの一つです。Apache Cordova の上に構築されHTML5 を用いたクロスプラットフォームのハイブリットアプリケーションを開発できます。

#### 12.6.4. DART

Flutter で使われている DART。Googleによって開発され、2011年10月に公開されました。

Webブラウザ組み込み用スクリプト言語として、JavaScriptの後継言語を目的に設計されています。GoogleではDartをChromeに統合する計画でしたが、2015年にその計画を断念。以後はDartを使ったプログラムをJavaScriptにコンパイルして、JavaScriptエンジンを搭載するWebブラウザ上で動作するようになりました。

Googleが開発したので、「Google Ads」「Google Fiber」「Google Express」「Google社内セールス」などのGoogle社内チームでも使われています。しかし現在最も注目されているのは、2018年にGoogleが発表したマルチプラットフォーム・アプリケーション開発ツール「Flutter（フラッター）」用の言語として使われていること

<https://dart.dev/>
<https://www.fenet.jp/infla/column/technology/126-2/>

### 12.7. RIA (Rich Internet Application)

ソフトウェアの分類の1つであり、ブラウザなどのクライアントの機能を活かした、柔軟なインタフェースをもつWEBアプリケーションのことである。CurlやFlashのようにプラグインをベースにしたものや、GWTのような最終的にHTML＋JSに変換されるものまで様々。

- Adobe Flex：　当時圧倒来なシェアを誇っていたFlashをベースとして、2004年にRIAとして本格的なビジネスアプリケーション向けのUIを作れるようにしたAdobeのプラットフォーム

数多く登場し流行ってはいたものの一瞬たりともWebのUIの王座には立っていないらしい。あまり見ないですし、知ってる程度でいいかも。

<https://zenn.dev/koduki/articles/c07db4179bb7b86086a1>

### 12.8. BFF (Backends For Frontend)

フロントエンドのためのバックエンド（サーバ）です。フロントエンドのためにAPIをコールしたり、HTMLを生成したりするサーバのことを指します。ここだけ読むと「今までのWebアプリケーションサーバと何が違うのか」と思うかもしれません。本質的にはそこまで変わりませんが、「フロントエンド専用」という役割が異なります。

![BFFのイメージ](2021-09-27-22-03-58.png)

<https://atmarkit.itmedia.co.jp/ait/articles/1803/12/news012.html>

#### 12.8.1. BFF のメリット

例えば、下記のようないくつかのメリットが生まれる。

- APIの集約：　シンプルにクライアントはBFFに対してのみAPIを投げればよく、複数のバックエンドに対しての対応や加工などをクライアント側が気にしなくてよくなります。また、バックエンドからの複数のレスポンスをクライアントが求める形に適切に加工して返すことができるので、クライアントの処理も少なくできます
- フロントとバックの分離：　バックエンドとクライアントが直接通信を行う場合そのプロトコルは一致させないといけませんでしたが、BFFを挟む場合はBFF <-> クライアントとBFF <-> バックエンドは全く別の通信になるので、 BFF <-> クライアントのみ GraphQLで BFF <-> バックエンドは RESTとのような柔軟な調整ができる

#### 12.8.2. BFF のデメリット

当然、デメリットもある

- デプロイのタイミング：　BFFはバックエンドと密にやりとりをするため、例えばバックエンドのAPIの仕様変更をした場合BFFも変更して同時にデプロイしないと障害の原因になる
- 通信量の増大：　データを取得するために必要な経路が増えるためデータ取得にかかる時間は増える
- コードの冗長化：　例えばユーザー一覧の取得APIなど、機能や関心ごとが一致する場合はほぼ同じコードを書かないと行けないため、コードが冗長化

<https://qiita.com/souhei-etou/items/d5de99bb8cba1c59d393>

### 12.9. Microservices

ソフトウェアエンジニアリングの観点からみると、マイクロサービスはモノリシックに比べて開発しやすいと言えます。 アプリケーションの規模が小さいため、開発者は継続的インテグレーションと継続的デリバリー（CI/CD）によって更新や改善を容易に行うことができます。 また、マイクロサービスは任意のプログラミング言語で記述できるだけでなく、 APIを使用して他のマイクロサービスと通信することが可能。

こちらの記事から例を抜粋。

<https://qiita.com/inagacky/items/43cc0518ef11f1e4beb3>
<https://www.talend.com/jp/resources/monolithic-architecture/>

#### 12.9.1. Istio

マイクロサービスとネットワークの間に、「サービスメッシュ」と呼ばれるレイヤを挟み、マイクロサービス間を接続するネットワークのルーティング、ロードバランシング、通信の暗号化等々を行なってくれるプラットフォームです。

<https://istio.io/>

### 12.10. MVC (Model-View-Controller)

フレームワークを理解する重要な概念として、MVCというものがあります。MVCを採用するとアプリケーションをきれいな構造で実装できるので、ほとんどのフレームワークではMVCを採用しています。 MVCはもともとはPCで動くアプリケーションを開発するために提唱されましたが、その有用性の高さからWebアプリケーションでも利用されるようになりました。

### 12.11. MVVM (Model-View-ViewModel)

UIを持つソフトウェアに適用されるソフトウェアアーキテクチャの一種。Model-View-Controller (MVC) パターンの派生であり、特にPresentation Model パターンを直接の祖先に持つ。2005年に、マイクロソフトのWPFおよびSilverlightアーキテクトであったJohn Gossmanが自身のブログでModel-View-ViewModel (MVVM) パターンを発表した。

MVVMとは、プログラムを3つの要素、Model、View、ViewModel に分割し、各要素は、単方向に依存している View -> ViewModel -> Model。また、あくまでUI周り構成について触れているだけであって、Modelの中身については、各自で考える必要がある

<https://ja.wikipedia.org/wiki/Model_View_ViewModel>
<https://qiita.com/ebi-toro/items/046c9a43b15b9e376198>

#### 12.11.1. Model

アプリケーションのドメイン（問題領域）を担う、そのアプリケーションが扱う領域のデータと手続き（ビジネスロジック - ショッピングの合計額や送料を計算するなど）を表現する要素

#### 12.11.2. View

アプリケーションの扱うデータをユーザーが見るのに適した形で表示し、ユーザーからの入力を受け取る要素である。すなわちユーザインタフェースの入出力が責務

#### 12.11.3. ViewModel

Viewを描画するための状態の保持と、Viewから受け取った入力を適切な形に変換してModelに伝達する役目を持つ。すなわちViewとModelの間の情報の伝達と、Viewのための状態保持のみを役割とする要素である。実装ではしばしば、Viewとの通信はデータバインディング機構のような仕組みを通じて行う。

### 12.12. Accessibility (a11y)

可能な限り多くの人に利用してもらうようにすること。以前はハンディキャップを持つ人々のためのものだと考えていましたが、現在はそのためだけでもはなく、モバイルデバイスや遅いネットワークを利用している人々のためのものでもあると考えられています。

> 世界保健機構(WHO)の障碍と健康（英語）の報告によると、「10億人以上の人(世界人口の約15%)が何らかの障碍を持っています」し、「1億～1億9000万人の大人に目立った機能障碍があります」

ちなみに、a11y と略されることが多く、"a "の後に11文字、そして "y "という意味です。

Wix などのサイト作成ツールでも、アドミン内で対応が奨励されていて、チュートリアルを見ながらやっていけば対策されるようになっています。主に `<alt></alt>` タグを入れていくイメージですが。

<https://developer.mozilla.org/ja/docs/Learn/Accessibility/What_is_accessibility>
<https://developer.mozilla.org/ja/docs/Learn/Accessibility/HTML>

## 13.  RDBMS (Relational DataBase Management System)

アーキテクチャは下記の層になっている

- 構文解析器：　クエリが構文解析（パース）され、抽象構文木の形になる
- Query Planner ＆ 実行計画：　実行計画を作る
- Query Executor：　実行計画通りに、アクセスメソッドを呼び出す
- Access Method：　ディスク上のデータ構造を辿って、Query Executorの要求通りの結果を返す。Access MethodとしてはB+Treeなどがある。実際のディスクの読み書きはしない
- Buffer Pool Manager：　データの塊をメモリにキャッシュする。実際のディスクの読み書きはしない。ディスクの読み書きは遅いので、メモリにキャッシュすることで早く見せる役割。ファイルシステムにもキャッシュ機能はあるが、自分でやるために、あえてファイルシステムの方のキャッシュ機能は無効にする場合もある
- Disc Manager：　ディスクの読み書きをする。ヒープファイルという、ファイルを固定のバイトでページに区切ったファイルに書く。1ページが4096バイト。ページ単位でしか読み書きできない。ファイルはファイルシステムによって、HDDやSSDに書き込まれる

### 13.1. RDBMSの種類

- PostgreSQL：　PostgreSQLは、拡張性とSQL準拠を重視したフリーでオープンソースのリレーショナルデータベース管理システムで、Postgresとも呼ばれています。元々はPOSTGRESという名前で、カリフォルニア大学バークレー校で開発されたIngresデータベースの後継として開発されたことに由来しています。<https://www.postgresql.org/>
- Oracle Database：　OracleのRDBMS
- SQL Server：　MicrosoftのRDBMS
- MySQL：　オープンソースのRDBMS。イルカのやつ
- MariaDB：　MariaDBサーバーは、最も人気のあるオープンソースのリレーショナルデータベースの一つです。MySQLのオリジナル開発者によって作られており、オープンソースであることが保証されています。<https://mariadb.org/>
- SQLite：　小型、高速、自己完結型、高信頼性、フル機能を備えたSQLデータベースエンジンを実装したC言語ライブラリ（と本家が言ってる）。
<https://www.sqlite.org/index.html>
<https://products.sint.co.jp/topsic/blog/sqlite>

### 13.2. DBの冗長化

データの永続性を満たすためには冗長化が必要。冗長化の方法にはいくつかある

- Mirroring：　プリンシパルDBで受けたクエリをコピーして、同時にミラーDBにも実行
- Replication：　マスタDBで受けたクエリを実行した後の内容を、スレーブDBにコピー。即時ではない。スレーブとはSlave（奴隷）のことで副を指す
- Shared Disk：　DBサーバーだけ冗長で、ディスクは共有型

### 13.3. Query Cache

APサーバーからのクエリと、それに対するレスポンスを一定期間記憶し、期間内に同じクエリが来たら同じ結果を返す。それによりレスポンスが速くなる。

DBサーバー内のメモリに作られる共有バッファという領域にデータが確保されることで、やりとりの遅いディスクに比較して、速い応答を実現している

<https://www.postgresql.jp/sites/default/files/2016-12/kataoka_check_your_config.pdf>
<https://gihyo.jp/dev/feature/01/dex_postgresql/0002>
<https://thinkit.co.jp/cert/tech/10/1/3.htm>

### 13.4. ORM (Object-Relational Mapper)

プログラミング言語からRDBMSにクエリを発行しようと思ったら、SQLを生成する必要があります。SQLは文字列として生成しなければならず、SQL自体をしっかり把握していないといけません。またSQLの文字列生成は、プログラミングの処理としては扱いづらい方法です。 そこでデータベースに問い合わせをする専用のライブラリとしてO/Rマッパーが登場しました。

サーバサイドフレームワークではRDBMSと組み合わせて使うことが多く、RDBMSへのクエリを簡単に行うためO/Rマッパーを提供していることがほとんどです。O/Rマッパーを使うと開発者はSQLのことを意識することなく、データベースへのアクセスが簡単にできるようになります。

### 13.5. SQL Antipatterns

という名前のオライリーの本が出版されてもいる。その中でもMENTORの原則というものがあり、紹介しておく。

#### 13.5.1. MENTOR Your Indexes

MENTORとは下記のこと。

1. Measure：　頻度が高いのに実は遅いクエリ、測って特定せよ。そのためのツールもある
2. Explain：　クエリを特定したら、その実行計画をみよ
3. Nominate：　Sequential Scan（ただ順番にチェックする処理）をみつけよ。インデックスをはると速くなる（かも）
4. Test：　インデックス貼ったら再実行！再度実行計画をみよ
5. Optimize：　インデックスをメモリ上にキャッシュせよ
6. Repair：　定期的にデフラグせよ

<https://note.com/usop/n/n6f56220ebd85>

<https://kyabatalian.hatenablog.com/entry/2016/12/23/172700>

### 13.6. Dump

テーブルの中身をバックアップすること。

ただし、対象データの容量が大きいと、dumpしてる間に更新されたりしてしまうので、アクセスがない時間帯にやるか、その間テーブルロックする必要がある。dumpファイルはテキスト情報なのでエディターで中身を見ることも可能。これをもとに復元することをRestoreという。

<https://www.sejuku.net/blog/82770>

### 13.7. ERD (Entity Relationship Diagram)

通称、ER図。実体関連モデル。主にデータベースや情報システムでデータを編成するときの設計図として使われています。

ER図では、データベースを構成するデータのまとまりを「エンティティ」と呼ばれる四角形で表します。そして、データ同士を「リレーション」と呼ばれる線で結び「カーディナリティ」と呼ばれる記法で相互の関係性を示します。ER図には、概念データモデル、論理データモデル、物理データモデルの3種類があります。

ER図は、実体そのものの間の関連ではなく、実体内の要素の関連に重きを置いたデータ構造図 (DSD) に関連した図です。また、ER 図はしばしば、プロセスやシステムの流れを描き出すデータフロー図 (DFD) とも関連して用いられます。

<https://cacoo.com/ja/blog/entity-relationship-diagram-for-beginner/>

<https://www.lucidchart.com/pages/ja/er-diagram>

#### 13.7.1. Conceptual Data Model

概念データモデル。システム全体をモデル化し、シンボルを用いて事象を大まかな分類した図

![Conceptual Data Modelのサンプル](2021-09-27-22-10-25.png)

<https://online.visual-paradigm.com/knowledge/visual-modeling/conceptual-vs-logical-vs-physical-data-model/>

#### 13.7.2. Logical Data Model

論理データモデル。概念データモデルを詳細に落とし込んで、画面や帳票などのシステムで必要とする属性を付与したモデル図

![Logical Data Modelのサンプル](2021-09-27-22-11-00.png)

<https://online.visual-paradigm.com/knowledge/visual-modeling/conceptual-vs-logical-vs-physical-data-model/>

#### 13.7.3. Physical Data Model

物理データモデル。論理データモデルさらに詳細に落とし込んだ図で、実際のデータベースの情報と1対1の関係になっています。

![Physical Data Modelのサンプル](2021-09-27-22-11-30.png)

<https://online.visual-paradigm.com/knowledge/visual-modeling/conceptual-vs-logical-vs-physical-data-model/>

### 13.8. EERD (Enhanced / Extended ERD)

ER図を拡張した「拡張実体関連モデル」。EER図は、ER図に以下のような要素を追加しています。

1. サブクラスとスーパークラス
2. 特殊化と一般化
3. カテゴリーまたはユニオン
4. アトリビュート（属性）やリレーションの継承

![サブクラスとスーパークラスのイメージ](2021-09-27-22-13-09.png)*サブクラスとスーパークラス*
![特殊化と一般化のイメージ](2021-09-27-22-13-33.png)*特殊化と一般化*
![カテゴリーまたはユニオンのイメージ](2021-09-27-22-13-50.png)*カテゴリーまたはユニオン*

<https://www.tutorialspoint.com/Extended-Entity-Relationship-EE-R-Model>
<https://cacoo.com/ja/blog/entity-relationship-diagram-for-beginner/>
<https://www.lucidchart.com/pages/enhanced-entity-relationship-diagram>

### 13.9. Drawing Tools

作図ツール。ERDを書くためだけとも限らないのですが、ここにメモしていきます。デザインを伴わない画面遷移図などにも使えます。手軽さ的には、ExcelやVisioもいいですが、しっかりドキュメントとして残すのであれば、見た目の統一性が図りやすく、効率のいいツールを推奨したいところです。

かくいう私もずっとExcelできれいに書くことを目指していましたが、その視点が既に井の中だったと思いました。

#### 13.9.1. Draw.io

「draw.io」とは、*フローチャートやオフィスのレイアウト図、ネットワーク図を作成できる無料の作図ツール*です。GoogleChromeのようなブラウザ上で操作ができ、作成した図はGoogleドライブやGithubと連携させて保存が可能です。

個人的にもよく使いますが、すごくきれいに書けます。Excelで作図するのはやめたいところです。すぐ慣れますが、他のサービス同様に多少の学習コストはあります。Excelよりいいのは、下記のようなポイントですね

- オブジェクトに対して、矢印がくっつけられるポイントが多い
- 矢印に対する補足コメントは、矢印を選択して、Enterを押すだけで入れられる
- アイコンが豊富で、テキスト検索でだいたいヒットする
- 最初から背景が方眼紙の状態であり、かつグリッドに対してオブジェクトがぴたっとなる

AWSもサービスの概念モデルに draw.io で作図した図を使ってるのを見たことがあります。こういうのはデモをYouTubeで見るのが早いです。

<https://youtu.be/WlCKv49Pkvg>
<https://qiita.com/G-awa/items/8fd414700b68b2bcafcc>
<https://ferret-plus.com/8408>

#### 13.9.2. Lucidchart

draw.io と同じくらい有名だと個人的に思う。Lucidchart（ルシドチャート）は，図や表の描画，修正，共有を共同で行うことができるWebベースの独自プラットフォームである。 米国ユタ州に本拠地を置くLucid Software Inc.が制作している。

2011年、Lucid社は「エンジェル・ファンディング」で100万ドルを調達。2018年、Lucid社はMeritech CapitalとICONIQ Capitalから7,200万ドルの追加調達を発表。

Lucidchartは使ったことはありませんが、これも使いやすそうですね。

<https://youtu.be/5a_FQPLMkKI>
<https://en.wikipedia.org/wiki/Lucidchart>

#### 13.9.3. Cacoo

カクー。2009年登場の国産のオンライン作図ツール。Backlogなどを展開するNulab Inc.が開発・運営している。

日本語ベースなので、それが一番のメリット。多少、上の2つに比べると機能的に見劣りするかも（あくまで、ぱっと見の印象です）。

<https://youtu.be/ehKvPnWsR10>
<https://cacoo.com/ja/>
<https://en.wikipedia.org/wiki/Cacoo_(software>)

## 14.  NoSQL DB (Not Only SQL DataBase)

今じわじわとその存在度を高めている NoSQL です。何より速い。速いは正義。しかし、その代わりに何らかのトレードオフ（それは学習コストも含む）を飲み込もう、という代物。よく勘違いされてますが、No More SQL!! （もうSQLしなくていい！！）じゃないですからね。SQLだけじゃない、です。

RDBMSの場合、書籍レコードはしばしば分解 (「正規化」) されて別々のテーブルに格納され、それらの関係がプライマリキーと外部キーの制約によって定義されます。

この例では、Books テーブルには ISBN、Book Title、Edition Number の列があり、Author テーブルには AuthorID と Author Name の列があり、最後に Author-ISBN テーブルに AuthorID と ISBN の列があります。

リレーショナルモデルは、データベース内のテーブル間で参照整合性を維持し、正規化して冗長性を減らし、全般的にストレージを最適化できるように設計されています。

対して、NoSQL DBの場合、書籍レコードは通常、JSON ドキュメントとして保存されます。書籍ごとに、ISBN、Book Title、Edition Number、Author Name、AuthorID の各項目が、属性として単一のドキュメント内に格納されます。このモデルでは、データが、直感的な開発と水平スケーラビリティのために最適化されています。

NoSQL の特徴は下記。

- スキーマレス。テーブルの項目定義をしなくていいという意味
- テーブル結合ができない
- トランザクションがないので、有事の際にデータ復旧出来ない
- 水平スケールアウトが容易

<https://www.amazon.co.jp/dp/B07BGC4MJ1/ref=cm_sw_r_cp_api_glt_TH4H5DR153PR5HA7AF49>

### 14.1. NoSQL DB の種類

NoSQL DBには大きく4種類ある。

1. KVS (Key-Value Store)：　キーとバリューの組み合わせ。代表的なOSSは、RedisやMemcached
2. Column-Oriented DB：　カラム指向DB。列方向のデータのまとまりをファイルシステム上の連続した位置に格納し効率的にアクセスする。代表的なOSSは、cassandra、HBASE
3. Document-Oriented DB：　ドキュメント指向DB。キーに対してJSONあるいはXMLを格納する。代表的なOSSは、mongoDB、Apache couchDB、Firestore
4. Graph-Oriented DB：　グラフ指向DB。グラフ理論に基づいて関連性を持たせる。代表的なOSSは、neo4j、TITAN

<https://aws.amazon.com/jp/nosql/>
<https://qiita.com/gold-kou/items/966d9a0332f4e110c4f8>
<https://youtu.be/W2Z7fbCLSTw>

### 14.2. KVS (Key-Value Store)

#### 14.2.1. Redis

Remote Dictionary Serverの略。速さ的に特に注目度が高い印象があります。DB、キャッシュ、メッセージブローカー、およびキューとして使用するための、高速でオープンソースのメモリ内 Key-Value 型のNoSQL データベース。

このプロジェクトは、Redis の最初の開発者である Salvatore Sanfilippo 氏が、イタリアのスタートアップ企業のスケーラビリティを改善しようとしていたときに始まりました。現在はVMWareが支援し、大きなコミュニティとなっている。

Redis は今、ミリ秒未満の応答時間を実現し、1 秒間に数百万件のリクエストを処理できます。キャッシング、セッション管理、ゲーム、リーダーボード、リアルタイムアナリティクス、地理空間、ライドヘイリング、チャット/メッセージング、メディアストリーミング、およびパブ/サブアプリケーションに広く使用されています。

<https://youtu.be/G1rOthIU-uo>
<https://agency-star.co.jp/column/redis/>
<https://qiita.com/wind-up-bird/items/f2d41d08e86789322c71>

#### 14.2.2. Memcached

Redisとよく似ているが、Memcached はシンプルに、また Redis は幅広いユースケースに対して効果的とされる。Memcached はマルチスレッドであるため、複数の処理コアを使用できます。これは、コンピューティング性能をスケールアップすることで、より多くの操作を処理できることを意味します。

AWSのサイトなどでの比較ではRedisの方が高機能である。

<https://aws.amazon.com/jp/elasticache/redis-vs-memcached/>
<https://dev.classmethod.jp/articles/which-choice-redis-memcached/>

### 14.3. Column-Oriented DB（カラム指向DB）

#### 14.3.1. Apache Cassandra

フリーでオープンソースの分散型ワイドカラムストアNoSQLデータベース管理システム。Apache Software Foundation が開発、2008年に初公開。開発言語は Java。

多数のコモディティサーバーで大量のデータを処理し、単一障害点のない高可用性を実現するように設計されています。複数のデータセンターにまたがるクラスターをサポートしており、非同期のマスターレス・レプリケーションにより、すべてのクライアントに対して低レイテンシーでの操作を可能にしています。AmazonのDynamo分散ストレージおよびレプリケーション技術と、GoogleのBigtableデータおよびストレージエンジンモデルを組み合わせて実装するように設計されています。

AmazonのDynamoの作者の一人である Avinash Lakshman と Prashant Malik は、当初Facebookの受信トレイ検索機能を動かすためにFacebookでCassandraを開発。Facebookは2008年7月にCassandraをGoogle Code上のオープンソースプロジェクトとして公開し、2009年3月にはApache Incubatorプロジェクトとなり、2010年2月17日にはトップレベルのプロジェクトに昇格した。

<https://cassandra.apache.org/_/index.html>
<https://en.wikipedia.org/wiki/Apache_Cassandra>
<https://www.nttpc.co.jp/technology/cassandra.html>
<https://techblog.yahoo.co.jp/entry/20200129803067/>

### 14.4. Document-Oriented DB（ドキュメント指向DB）

#### 14.4.1. MongoDB

NoSQL では一番有名。

ソースから入手可能なクロスプラットフォームのドキュメント指向データベースプログラムです。NoSQLデータベースプログラムに分類されるMongoDBは、オプションのスキーマを持つJSON形式のドキュメントを使用します。また、ドキュメントはRDBにおける行を意味する。

MongoDBは、MongoDB Inc.によって開発されています。開発言語は、JavaScript。名前の由来は、humongous から来ており、バカでかいを意味する。

以下のようなメリットを持つ

- スキーマレスにより、保守性が高い
- 機能を制限による高パフォーマンスを実現
- RDBと似た操作により、学習効率が高い
- オープンソースなので無料
- 簡単な設定だけでスケールアウト（負荷分散）が可能

<https://www.mongodb.com/>
<https://www.amazon.co.jp/dp/B07BGC4MJ1/ref=cm_sw_r_cp_api_glt_TH4H5DR153PR5HA7AF49>

#### 14.4.2. Robomongo

MongoDB の GUI ツール。

#### 14.4.3. Apache Couch DB

Apache CouchDB（読み：アパッチ カウチディービー）とは、ドキュメント指向のオープンソースデータベース。2005年登場。開発言語は、Erlang, JavaScript, C, C++。主にErlang。

<https://ja.wikipedia.org/wiki/Apache_CouchDB>

#### 14.4.4. Realm

オープンソースのオブジェクトデータベース管理システムで、当初はモバイルOS（Android/iOS）向けでしたが、Xamarin、React Native などのプラットフォーム、デスクトップアプリケーション（Windows）も含めて利用可能。

2016年9月には「Realm Mobile Platform」が発表され、続いて2017年1月に最初の安定版がリリースされました。Realm Object Serverと、所定のログインユーザーに属するクライアント側のデータベースとの間で双方向の同期が可能。2019年春、MongoDBはRealmを3,900万米ドルで買収した

<https://realm.io/>
<https://en.wikipedia.org/wiki/Realm_(database>)

#### 14.4.5. Firestore

非常に強力な機能性を備えたマネージド・データベースです。

ドキュメント指向データベースに分類され、特にJavaScriptから使う場合はJSON形式のデータをそのまま読み書きできるので、O/Rマッピングの煩わしさもありません。自動スケーリング機能を備えたデータベース・ソリューションは数多くありますが、それに加えてクエリが強整合性を持っているところが、Firestoreの優れた点です。

Authenticationのサポートを得て、クライアントから直接アクセスができるようになったFirestoreの主な役割は、従来のJSONデータを提供していたREST APIやBackends for Frontend(BFF)が担当していた部分をそのまま置き換えることです。

Firestoreは本質がデータベースでありながら、従来のREST APIの役割を代替することができます。それは「クライアントからセキュアに直接読み書きが可能」「ドキュメント指向でありO/Rマッピング不要」「強い整合性」という特性を獲得し、極めて高い可用性とスケーラビリティーを持っているからです。もはや、バックエンドとデータのやり取りをするために、REST APIを用意する必要はなくなりました。

### 14.5. Multi-Model DB

単一の統合されたバックエンドに対して複数のデータモデルをサポートするように設計されたデータベース管理システムを指します。Multi-Model DB がサポートするデータモデルの例としては、上述した Document-Model、Graph-Model、Relational-Model、Key-Value-Modelなどがあります。

対になる概念は、Polyglot Persistence で、アプリケーションで複数のデータベースモデルを統合する考え方である。

#### 14.5.1. ArangoDB

ArangoDB GmbHが開発した、フリーでオープンソースのネイティブマルチモデルデータベースシステム。2011年に登場。開発言語は、C++、JavaScript。<https://en.wikipedia.org/wiki/ArangoDB>

#### 14.5.2. Azure Cosmos DB

マイクロソフトによるグローバル分散型マルチモデルデータベースサービス。2017年5月に登場。<https://en.wikipedia.org/wiki/Cosmos_DB>

#### 14.5.3. CrateIO

ドキュメント指向のデータストアを統合した分散型SQLデータベース管理システム。開発言語はJava。<https://en.wikipedia.org/wiki/CrateDB>

#### 14.5.4. MarkLogic

MarkLogic社の製品は、JSONやXMLドキュメント、セマンティックデータ（RDFトリプル）を保存、管理、検索できることから、マルチモデルのNoSQLデータベースとされています。<https://en.wikipedia.org/wiki/MarkLogic>

#### 14.5.5. OrientDB

Javaで書かれたオープンソースのNoSQLデータベース管理システムです。グラフモデル、ドキュメントモデル、キー／バリューモデル、オブジェクトモデルをサポートするマルチモデルデータベースであるが[2]、リレーションシップの管理はグラフデータベースのようにレコード間を直接接続して行う。

#### 14.5.6. Virtuoso

従来のリレーショナルデータベース管理システム（RDBMS）、オブジェクトリレーショナルデータベース（ORDBMS）、仮想データベース、RDF、XML、フリーテキスト、Webアプリケーションサーバー、ファイルサーバーなどの機能を一つのシステムにまとめたミドルウェアとデータベースエンジンのハイブリッドです。

<https://en.wikipedia.org/wiki/Virtuoso_Universal_Server>
<https://en.wikipedia.org/wiki/Multi-model_database>
<https://docs.microsoft.com/ja-jp/azure/azure-sql/multi-model-features>
<https://jp.marklogic.com/product/marklogic-database-overview/database-features/multi-model-database/>
<https://martinfowler.com/bliki/PolyglotPersistence.html>
<https://en.wikipedia.org/wiki/Comparison_of_multi-model_databases>

#### 14.5.7. Fauna DB

最後にもってきてしまいましたが・・・特に注目度が高いのはこの Fauna DB でしょうか。（それともマーケティングが上手いのか）

柔軟性が高く、開発者が使いやすいトランザクションデータベースで、ネイティブなGraphQLを備えた安全でスケーラブルなクラウドAPIとして提供されます。データベースのプロビジョニング、スケーリング、シャーディング、レプリケーション、正確性などの心配はもうありません。とのこと（公式サイトより）。

元 Twitter のエンジニアの Evan Weaver と Matt Freels によって立ち上げられたクラウドサービスで、アーキテクチャは2012年に発表されたCalvinの論文からインスパイアされている。

<https://fauna.com/>
<https://youtu.be/2CipVwISumA>
<https://bagelee.com/programming/faunadb-graphql-trial/>
<https://dev.classmethod.jp/articles/faunadb-with-graphql/>

## 15. Version Control System

### 15.1. GitHub

特に事情もなく新しく選ぶならGitHub一択。といっても中にいくつかサービスがある

#### 15.1.1. GitHub Actions

GitHub上のリポジトリやイシューに対するさまざまな操作をトリガーとしてあらかじめ定義しておいた処理を実行できる機能で、今まで外部サービスとの連携が必要だった自動テストや自動ビルドなどがGitHubだけで実現できるようになる。

GitHub Actionsは2018年に発表された機能で、しばらくは利用申請をした一部のユーザーのみが利用できる機能だったが、2019年11月には正式版の機能となり、現在はGitHubを利用するすべてのユーザーが特に申請や手続きを行うことなく利用できるようになっている。GitHub Actionsでは、実行する処理とその処理を実行する条件を定義したものを「Workflow（ワークフロー）」と呼ぶ。ワークフローはYAML形式で記述し、リポジトリ内の.github/workflowsディレクトリ内に保存することで実行できるようになる。<https://knowledge.sakura.ad.jp/23478/>

#### 15.1.2. GitHub Webhooks

Webhook 自体は上述。

GitHub Webhook はリポジトリへのpushを検知して、任意のURLにコミット内容などの情報をパラメータにのせて送り込んでもらえます。GitHubのプルリクエスト通知をSlackに投げるといった具合です。

<https://www.blog.danishi.net/2019/05/22/post-1195/>

#### 15.1.3. GitHub Marketplace

GitHub Marketplaceは、プロジェクト管理からコードレビューまで、開発プロセス全般で使えるツールを販売するウェブサイト。これまでも同様のツールは入手可能だったが、提供元がばらばらだったため、複数のアカウントを取得し、異なる決済方法に対応する必要があった。GitHub Marketplaceに集約することでユーザーの手間を軽減し、開発ワークフローのブラッシュアップやカスタマイズの容易化を支援するとしている。

<https://japan.cnet.com/article/35101578/>

#### 15.1.4. GitHub Enterprise

企業の導入に適したGitです。履歴管理やブランチの作成といった基本機能はGitと変わりません。

- セキュリティを担保できるか？
- 既存環境へ導入できるか？
- 運用コストを抑えられるか？

これらを容易に解消してくれるのが、GitHub Enterprise。

<https://style.potepan.com/articles/8570.html>

#### 15.1.5. GitHub Copilot

VSCodeの拡張機能として使える。関数名とコメントから、関数のコードを丸ごと自動補完するAIプログラミング機能。

OPEN AIが開発した技術「GPT-3」をベースとしている。OPEN AIも、GitHubも、VSCodeもMicrosoft傘下の企業や製品なので、一番最初に実現したと思われる。

2021年9月末時点でも、Waitlist状態なのですが、日本でも既に使ってみた方も結構いらっしゃるようなので、企業規模だったり、実績（？）だったりを見て、ファストパスがあるのかもしれません。そうでない方は並んでおいた方がお得かと存じます。早く使ってみたいです。

<https://copilot.github.com/>
<https://www.itmedia.co.jp/news/articles/2106/30/news063.html>

### 15.2. Git Command

よく聞くコマンドだが、時々反対になってたり、間違ってたり、こんがらがってたりする。フェッチって英単語がマイナーなせいなのか、使ってない率が高い気がする

- git fetch：　リモートのリポジトリの内容をローカルのリポジトリに取り込む
- git push：　ローカルのリポジトリの内容をリモートのリポジトリに送り込む
- git pull：　 まず git fetch してから、次に、現在のローカルのブランチに対して、それに対応するリモートのブランチを git merge するコマンド。なので、push と pull は正確には対となる言葉ではない
- git merge：　対象ブランチを、チェックアウト中のブランチへマージする
- git remote：　リモートリポジトリの一覧を出力する
- git clone {リポジトリのURL}：　対象リポジトリのデフォルトブランチをクローンする。クローンとはリポジトリのコピーを取得することができる機能。 リモートリポジトリの内容をローカルの環境で使用する場合などで使用します。初めてコピーしてくるときに使うので、git fetch とも git pull とも違う
- git branch：　ローカルブランチの一覧を出力する
- git checkout {ブランチ名}：　対象ブランチに切り替える　※古いらしい
- git switch {ブランチ名}：　対象ブランチに切り替える
- git commit：　指定したエディタでメッセージを書き、インデックスにある全ファイルをコミットする

<https://git-scm.com/about>
<https://qiita.com/usamik26/items/28be7d2c221a7a53c2c3>
<https://qiita.com/uhooi/items/c26c7c1beb5b36e7418e>
[https://nobwak.github.io/posts/2019-06-06-わたしにgit_pullとgit_cloneの違いを教えてください/](https://nobwak.github.io/posts/2019-06-06-%E3%82%8F%E3%81%9F%E3%81%97%E3%81%ABgit_pull%E3%81%A8git_clone%E3%81%AE%E9%81%95%E3%81%84%E3%82%92%E6%95%99%E3%81%88%E3%81%A6%E3%81%8F%E3%81%A0%E3%81%95%E3%81%84/)
<https://next.rikunabi.com/journal/20170120_t12_iq/>

## 16. CI/CD (Continuous Integration and Continuous Delivery)

継続的インティグレーション／継続的デリバリーといいます。CI/CDは1つの技術を指すものでなく、ソフトウェアの変更を常にテストして自動で本番環境にリリース可能な状態にしておく、ソフトウェア開発の手法を意味します。なので根本的には概念の話だが、それをサポートするツールの一部として下記を紹介する。

ツールを使うと、GitHub等へのpushをトリガーとして、テスト・コード解析・ビルド・デプロイを自動化することができます。GitHub Actionsが今は利用できるので、別のサービスを利用する必要性は下がったかも。

<https://codezine.jp/article/detail/11083>
<https://qiita.com/inagacky/items/43cc0518ef11f1e4beb3>

### 16.1. CI/CD Tools

#### 16.1.1. CircleCI

クラウド型のCIツールです。CIツールの中でも、国内の採用事例が最も多いサービスだと思います。<https://circleci.com/ja/>

#### 16.1.2. Travis CI

クラウド型のCIツールです。<https://travis-ci.org/>

#### 16.1.3. Jenkins

Javaで書かれたオープンソースのCIツールです。オープンソースなため、好きな環境にインストール可能です。無料。日本人が開発。<https://jenkins.io/>

#### 16.1.4. GitHub Actions

上述。<https://github.com/features/actions>

#### 16.1.5. Other CI/CD

他にも以下のがある

- GitLab CI
- Concourse
- Hudson
- TeamCity

### 16.2. DevOps (Software Development and IT Operations)

CI/CDをするためにDevOpsという考え方があるのか、はたまた、その逆なのかはさておき・・・。このDevOpsという言葉はよく聞きますが、その使われ方に違和感がありました。

本来のDevOpsの意味は、より早くビジネスの価値を高め、エンドユーザーに届け続けるために行う、文化の変化を伴うカイゼン活動を指す。それは元々がオライリー主催の2009年のイベントで発表されたFlickrの資料「10+ Deploys Per Day: Dev and Ops Cooperation at Flickr（1日10回以上のデプロイ： Flickrにおける開発と運用の協力）」による。まさに、Cooperation＝協力・協業という言葉が使われている。この概念を助けるために、ツールがあるのが本当の由来。

AWSのサイトによると、最近はここにセキュリティや品質チームなども合体した、DevSecOpsという言葉も紹介している。またAWS自体も文化と考え方の変化について言及している

<https://www.buildinsider.net/enterprise/devops/01>
<https://aws.amazon.com/jp/devops/what-is-devops/>
<https://qiita.com/bremen/items/44c3de10413f45f9f41e>

### 16.3. SRE (Site Reliability Engineering)

回復力の高い分散システムを構築・運用するために使用される、システムおよびソフトウェア・エンジニアリングの複数の原則から成る方法論のこと。

SREチームの具体的な業務内容は「インシデント管理」「問題管理」「オペレーション」など、一見すると従来からのシステム管理者が担う業務と変わりはない。ただ、「すべてにソフトウェア・エンジニアリングを活用する点で一線を画す」。

ガートナーの調査では海外の大企業の41％がすでにSREを採用。国内でもメルカリやクックパッド、ビズリーチなど、クラウド・ネイティブ企業や先進企業を中心に利用が加速中。

<https://www.sbbit.jp/article/cont1/48848>
<https://codezine.jp/article/detail/11002>

## 17. Text Editor

やや閑話休題。じゃあ実際、何を使って書いていくの？ということで、エディタです。単なる書くためのツールではなく、エクステンションやアドインで後述のLintツールなども導入可能。意外とこういうところで無駄に時間を使って調べたりする人も多いと思います（かくゆう私もはまるタイプです）

### 17.1. VSCode (Visual Studio Code)

エディターで悩むなら、これ使っておくべし。Microsoftのエディターで、どの調査でもだいたい1位である。拡張機能やプラグインが豊富。前述の Prettier Code Formatter など。

VSCode自体の主な開発言語は、TypeScript、JavaScript、CSS。Wikiから引用したところによると、2016年のStack Overflowによる調査では、Visual Studio Codeは、13番目に人気のある開発ツールで、46,613人のうち、7.2%がこれを使っていた。しかしながら、2019年の調査では、Visual Studio Codeは1位に位置し、87,317人の開発者のうち、50.7%がこれを使っていた。これは2021年も変わらないトレンドである。

<https://ja.wikipedia.org/wiki/Visual_Studio_Code>
<https://qiita.com/kumapo0313/items/a59df3d74a7eaaaf3137>

#### 17.1.1. VSCode Extensions

数多くのブログやYouTubeでまとめられていますので、そちらを基本は見て、がしがし入れていくとよいでしょう。

- Markdownlint：　その名の通り Markdown の lint ツールです。インストールすると、よろしくない書き方をビシバシ指摘してくれます。
- Auto Close Tag：　HTML/XML タグを書いたら、この拡張機能は面倒な作業を省き、自動的にタグを閉じてくれます
- Auto Rename Tag：　Open/Close タグの名前を変更すると、もう一方のタグの名前も自動的に変更してくれる
- ESLint：　後述
- Prettier：　後述
- Path Intellisense：　入力時にファイルパスを自動で補完してくれます
- Bracket Pair Colorizer：　一致する括弧を色分けしてくれる
- Git Lens
- Debugger for Chrome
- REST Client：　PostmanやSOAP UIのようなツールを使用しなくても、VSCode内で出来るようになる
- JavaScript (ES6) code snippets：　同じコードを入力する手間を大幅に減らしてくれる
- Code Spell Checker：　スペルミスがあったときに警告が表示されます
- VSCode Icon：　ファイルの拡張子に応じて、さまざまなファイルタイプを美しく視覚的に表現してくれる

<https://codeforgeek.com/best-visual-studio-code-extensions-web-development/>
<https://scotch.io/bar-talk/22-best-visual-studio-code-extensions-for-web-development>
<https://towardsdatascience.com/20-best-vs-code-extensions-for-productive-web-development-in-2020-95bf904ceb69>

### 17.2. Atom

GitHubが開発したオープンソースのテキストエディタ。MicrosoftはGitHubの親会社でもあるので、VSCodeとは兄弟的な関係になった。開発言語は、C++ / Node.js / CoffeeScript / JS / CSS / HTML。Electronを使用したデスクトップアプリケーションである。

[https://ja.wikipedia.org/wiki/Atom_(テキストエディタ)](https://ja.wikipedia.org/wiki/Atom_(%E3%83%86%E3%82%AD%E3%82%B9%E3%83%88%E3%82%A8%E3%83%87%E3%82%A3%E3%82%BF))

### 17.3. Eclipse IDE

Eclipse Foundation が提供する統合開発環境。

ベースとなるワークスペースと、環境をカスタマイズするための拡張可能なプラグインシステムが含まれている。Eclipseは主にJavaで書かれており、主にJavaアプリケーションの開発に使用されるが、Ada 、ABAP、C 、C ++ 、C＃ 、Clojure 、COBOL 、D、Erlang、Fortran 、Groovy 、Haskell、JavaScript、Julia、Lasso、Lua、NATURAL、Perl、PHP、Prolog、Python、R、Ruby（Ruby on Railsフレームワークを含む）、Rust、Scala、Schemeなどのプラグインを介して他のプログラミング言語のアプリケーションを開発するために使用することもできる。

[https://ja.wikipedia.org/wiki/Eclipse_(統合開発環境)](https://ja.wikipedia.org/wiki/Eclipse_(%E7%B5%B1%E5%90%88%E9%96%8B%E7%99%BA%E7%92%B0%E5%A2%83))
<https://www.eclipse.org/>

### 17.4. Web Storm

JetBrains 社製の有料のIDE。

WebStormは、JavaScriptとその関連技術のための統合開発環境です。他のJetBrainsのIDEと同様に、ルーチンワークを自動化し、複雑なタスクを簡単に処理できるようにすることで、開発体験をより楽しいものにします。

<https://www.jetbrains.com/webstorm/>
<https://ics.media/entry/11642/>

## 18. Static Code Analysis

静的規約チェックツール。そもそも、テストとは下記のように分類される。静的テストを特に分解するとこうなる

- Static Analysis：　静的解析。実行せずに、ソースを見てチェックするテスト
  - 前者には人による目視
  - ツールを使ったチェック
    - コーディング規約やコーディング作法と呼ばれるものと一致しているかチェック
    - 脆弱性になりうるもの、パフォーマンスを落とすもの、メモリリークを引き起こすものなどのバグになりうる問題のある箇所をチェック
- Dynamic Analysis：　動的解析。実際に動かしてみるテスト

<https://qiita.com/s-tanoue/items/7eb485409765442fcb54>
<https://hldc.co.jp/blog/2018/03/29/1211/>

独自に会社内で定義された規約もあれば、公開されているものもある

### 18.1. Coding Standards for C

#### 18.1.1. MISRA-C

C言語のためのコーディング・ガイドラインです。MISRA-Cは、より安全なC言語サブセット。車載機器や産業機器、医療機器といったミッションクリティカル分野の組み込みソフトウェア開発では、MISRA などのコーディング規約の遵守が求められています。

<http://www.c-lang.org/detail/misra_c.html>
<https://www.techmatrix.co.jp/product/ctest/staticanalysis/codingrule.html>

#### 18.1.2. CERT-C

C言語を使ってセキュアコーディングを行うためのルール (Rule) とレコメンデーション (Recommendation) を定めています。CERT が提案しているセキュアコーディングスタンダードは、標準化団体が定める明文化された標準言語に基づく。C以外にもC++やJava用の規約も提供する。

さまざまな機器がIoT化する流れの中で、サイバーセキュリティを確保するためのコーディング規約として、CERTへの対応なども求められつつあります。

<https://www.jpcert.or.jp/sc-rules/>
<https://www.techmatrix.co.jp/product/ctest/staticanalysis/codingrule.html>

#### 18.1.3. Coding Standards for JS

- Google JavaScript Style Guide：　Googleによる、最も代表的なスタイルガイド
- Airbnb JavaScript Style Guide：　GitHub上で最も人気のある、Airbnbのスタイルガイド
- Node.js Style Guide：　GitHub上で人気のある、Mr.felixge によるNode.jsのスタイルガイド

<https://qiita.com/takeharu/items/dee0972e5f39bfd4d7c8>

## 19. Code Formatter

コードの整形。コードフォーマッターは、WebStormやVisual Studio Codeなどのエディターにも付属していますが、これらはユーザー環境に依存する。PrettierはNode.js上で動作するため、ユーザー環境に依存することなく、プロジェクト単位でコードフォーマットを統一できます。

下記のようなことをやってくれる

- 一重引用符と二重引用符の統一
- 正しいインデント
- 空白、行の折り返しの整合性　などなど

<https://ics.media/entry/17030/>
<https://www.digitalocean.com/community/tutorials/how-to-format-code-with-prettier-in-visual-studio-code-ja>
<https://en.wikipedia.org/wiki/List_of_tools_for_static_code_analysis>

### 19.1. Code Formatter のサービス例

#### 19.1.1. Prettier (for JS)

Node.js上で動作するコードフォーマッターです。2017年1月にリポジトリが開設されてからわずか1年で2万Starを集めており、ReactやBabel、Material-UIなど著名なプロダクトでも採用され話題になっています。

<https://ics.media/entry/17030/>

#### 19.1.2. autopep8 (for Python)

PEP8 コーディングスタイルに準拠した Python のコードフォーマッタ。

<https://qiita.com/genbu-jp/items/c25b67c95425b733fb7d>

#### 19.1.3. Black (for Python)

Pythonのコードフォーマッター。PEP8に準拠。autopep8 や yapf などありますが、blackはより制限が強く、自由に設定ができないのが特徴。PEP8では触れられていない、改行の仕方や、シングルクォートとダブルクォートの統一、末尾カンマの統一、余計な丸括弧の削除、数値リテラルの書き方統一などをしてくれます。

<https://blog.hirokiky.org/entry/2019/06/03/202745>

#### 19.1.4. isort (for Python)

Python PEP8に準拠したpackageの並びにしてくれる。具体的には、PEP8では、importは次の順序でグループ化して、なおかつ、グループの間には空行を挿入する必要がある。

1. Standard library imports.（標準ライブラリ）
2. Related third party imports.（サードパーティ関連）
3. Local application/library specific imports.（ローカルアプリケーション/ライブラリ固有）

<https://dev2prod.site/python/install-isort/>

#### 19.1.5. YAPF (for Python)

Pythonコードフォーマッタ。Yet Another Python Formatterの略。

<https://wonderwall.hatenablog.com/entry/2017/09/03/224500>

## 20.  Code Linter

Code Formatterとも重複する部分はあるが、Code Linterは、より良い構文、新しい機能、そして可能性のあるエラーをキャッチするために利用されるため、Code FormatterとCode Linterでそれぞれツールを入れることも多い。

<https://qiita.com/s-tanoue/items/7eb485409765442fcb54>
<https://medium.com/@awesomecode/format-code-vs-and-lint-code-95613798dcb3>
<https://en.wikipedia.org/wiki/List_of_tools_for_static_code_analysis>

### 20.1. Code Linter for JS

#### 20.1.1. ESLint

恐らく最も使われている。初期リリースは 2013 年頃。 作者は Nicholas C. Zakas です。 ルールの拡張を自由に行えることが特徴で、これを Pluggable と読んでいます。

JSLint/JSHint 互換のルールも、デフォルトで Pluggable なルールとして用意されています。 実装的には、Esprima でパースした結果の AST (Abstract Syntax Tree) をそれぞれの Lint ルールに渡すようになっているため、ESLint の本体はクリーンな実装がキープされるようになっています（1-pass で実行されないため若干遅いところが欠点）。 それぞれのルールはルール名で区別され、個別に ON/OFF することができます

<https://maku77.github.io/js/tool/static-analysis-tools.html>
<https://www.cresco.co.jp/blog/entry/11716/>

#### 20.1.2. JSHint

初期リリースは 2011 年頃。 作者は Anton Kovalyov（アントン・コバリャノフ）で、JSLint の fork として作られました。

ベースとなった JSLint は便利である一方で、作者 Douglas Crockford の頑固な設定（var 宣言は 1 つにまとめないと必ずエラーなど）が強制されるため、開発者から敬遠される部分が多くありました。 そこで、Anton は、より柔軟な設定を行える JSLint となることを目指して 2011 年に JSHint の開発を始めました。

<https://maku77.github.io/js/tool/static-analysis-tools.html>

#### 20.1.3. JSLint

初期リリースは 2007 年頃。 作者は Douglas Crockford で、著書に JavaScript Good Parts があり、JSON RFC4627 の仕様策定などを行っている人です。 後出の JSHint に比べると、デフォルトのチェックが厳しいです。

<https://maku77.github.io/js/tool/static-analysis-tools.html>

### 20.2. Code Linter for CSS

#### 20.2.1. Stylelint

CSSのLinterといえば、これ。デファクトスタンダード。

<https://stylelint.io/>
<https://qiita.com/jagaapple/items/7f74fc32c69f5b731159>

### 20.3. Code Linter for Java

#### 20.3.1. SpotBugs

SpotBugsは、Javaプログラムの中のバグを見つけるプログラムです。このプログラムは「バグパターン」のインスタンスを探します。「バグパターン」とは、エラーとなる可能性の高いコードのインスタンスです。

<https://spotbugs.readthedocs.io/ja/latest/introduction.html>

### 20.4. Code Linter for Multi-Languages

#### 20.4.1. Coverity

シノプシス社のCoverityは、ソースコードに潜在する重大な不具合やセキュリティ脆弱性を、高精度で検出するソースコード静的解析プラットフォームです。様々な言語に対応している

誤検出率が15％と非常に低く、大量の誤検出で開発者の時間を無駄にすることがありません。また不具合やリスクを的確な検出するとともに、コード修正方法に関する具体的なガイダンスも提供し、開発者のスキル向上にも寄与。数々の特許技術、10年間にわたる研究開発成果、そして100億行以上のコード解析で得たノウハウを組込んでいます。

他のツールもそうかもしれませんが、15％となると、ユーザー側にも誤検出であることを見抜くスキルが求められますね

<https://www.hitachi-solutions.co.jp/coverity/>

## 21. Test Frameworks

こちらも言語ごとに色々あります。JSだと利用実績と満足度はこんな感じ。

![Test Frameworksの利用実績率](2021-09-27-22-52-03.png)*利用実績率の推移。Usage = (would use again + would not use again) / total*

![Test Frameworksの満足度](2021-09-27-22-52-45.png)*満足度の推移。Satisfaction = would use again / (would use again + would not use again)*

<https://2020.stateofjs.com/en-US/technologies/testing/>

### 21.1. Test Frameworks for JS

#### 21.1.1. Jest

利用実績も満足度も1位。（満足度は僅差でTesting Libraryが上だが）

シンプルさを重視した、快適な JavaScript テスティングフレームワーク。Babel、TypeScript、Node、React、Angular、Vueなどを使ったプロジェクトに対応しています。

<https://jestjs.io/ja/>

#### 21.1.2. Mocha

Node.js 上とブラウザ上で動作する機能豊富な JavaScript テストフレームワークで、非同期テストを簡単かつ楽しく行うことができます。Mochaのテストは連続して実行されるため、柔軟で正確なレポートを作成することができ、キャッチされなかった例外を正しいテストケースにマッピングすることができます。GitHubで公開されています。

<https://mochajs.org/>
<https://qiita.com/hietahappousai/items/35bef9a16333ba84e46f>

#### 21.1.3. Selenium

JS専用というわけではありませんが、Selenium は Web ブラウザの操作を自動化するためのフレームワークです。2004 年に ThoughtWorks 社によって Web アプリケーションの UI テストを自動化する目的で開発されました。テスト以外にもタスクの自動化や Web サイトのクローリングなど様々な用途で利用されています。<https://qiita.com/Chanmoro/items/9a3c86bb465c1cce738a>

## 22. Development Methods

開発手法。ここも大きな章で、1つ1つにたくさんの本が出ていますが、大きくこういうものがあります。海外ソースも含めて調べると分かりますが、カテゴリ定義自体も結構曖昧です。。

- Waterfall（ウォーターフォール）
- Prototype（プロトタイプ）
- Agile（アジャイル）
- Spiral（スパイラル）

あの会社はいまだにウォーターフォールだ！（だからレガシーなのよ）、とか、うちの開発はアジャイル（だからモダン）だよ！、とか聞きますよね。しかし、知れば知るほど、そんな簡単にどれだなんて言えるのか、とも思う奥の深い概念でもあります。真の問題の所在は単にこの開発手法にはない場合もあるので、良い悪いを特に明言しにくいパートですね。ではそれぞれ簡単に紹介していきましょう。

### 22.1. Waterfall

要件定義から外部・内部設計、コーディング、テスト、運用まで順番にフェーズを区切りながら、次のフェーズに進む際は、前フェーズを凍結しながら進む、後戻りをしない開発方法。

<https://onetech.jp/blog/what-are-the-four-types-of-system-development-methods-7101>

とはいえ、言葉で書くほど簡単にその通り出来るものではなく、往々にして後戻りすることが多いことが、長年の課題だった。逆にこの思想を盾に、今更仕様変更できないよと、その大小に関係なく、開発者が要求をはねつける、という場面もよく見る。

全面的にだめな手法というわけではなく、誰もがイメージしやすいという利点もあるし、部分的に活用するなども可能だし、最初のローンチやリリースでは管理上向いている等の見方もある。

### 22.2. Prototype

ウォーターフォール・モデルの問題点を改善した手法がプロトタイプ・モデルです。プロジェクトの途中で試作品を開発し、発注者の要望と相違がないか確認しながらシステム開発するのが特徴。MVP（Minimum Viable Product）といわれる概念も近いですが、MVPは「実用最小限の製品」を実際に市場に投入することなのでプロトタイプ・モデルはあくまでも内部の開発プロセスという違いがあります。

<https://onetech.jp/blog/what-are-the-four-types-of-system-development-methods-7101>

これまた言葉で書く以上に難しいことで、これは途中の状態だよ、だけど認識齟齬のないように見せるよ！と言ったところで、それを忘れてしまう、理解できないことは往々にしてあり、後工程でやるはずのことばかり指摘されてしまう、またそうなってしまうのではと尻込みしてしまう、なんてことも多いイメージです。見せる側・見る側に適切な知識が必要です。

### 22.3. Agile

発注者と開発者がよりコミュニケーションしながらシステム開発を進める手法がアジャイル開発です。開発するシステムを小さく区切り、機能ごとに繰り返し開発していくのが特徴です。発注者が開発途中のシステムを試せるため、隠れたニーズや仕様の不満を見つけやすいのがメリット。優先度の高いところから開発することで、発注者が求めるシステムを効率的に提供できます。ただ、アジャイル開発は計画を立てるのが難しく、発注側にも適切な知識がないと管理上の問題が起きやすいです。

<https://onetech.jp/blog/what-are-the-four-types-of-system-development-methods-7101>

個人的には、アジャイルだから計画できないんだと、まったく未来のスケジュールを見せなくなるのも違うなあという感覚です。変化を許容する、歓迎するという大前提の概念は維持しつつも、その上で時間的コストをかけすぎないように計画を可視化することもまた大事でしょう。まさにこの塩梅が難しくて俗人的なので、開発者にとって人気の高い手法ですが、ベストアンサーになり切れないところなのかなと思います。

少なくとも「うちはアジャイルだよ！」の後に、「具体的にはこういうところがアジャイルだよ！」というドキュメントが続くようになってるといいなと思います。

### 22.4. Spiral

ウォーターフォール・モデルとアジャイル開発のメリットを組み合わせた開発手法がスパイラル・モデルです。システムの設計とプロトタイピングを繰り返して成果物の完成を目指します。

言葉が定義されてることは初めて知りましたが、現実的にはむしろ、ほとんどのケースで、ウォーターフォールとアジャイルな要素が混ざり合うので、この開発手法に該当するような気もしました。

<https://onetech.jp/blog/what-are-the-four-types-of-system-development-methods-7101>

### 22.5. Other Development Methods

同列ではないのですが・・・他にも開発手法というか概念に近い開発原則もあります。ここで少しだけ紹介します。

[https://プログラマが知るべき97のこと.com/エッセイ/DRY原則/](https://xn--97-273ae6a4irb6e2hsoiozc2g4b8082p.com/%E3%82%A8%E3%83%83%E3%82%BB%E3%82%A4/DRY%E5%8E%9F%E5%89%87/)
<https://qiita.com/yatmsu/items/b4a84c4ae78fd67a364c>

#### 22.5.1. DRY (Don’t Repeat Your Self)

Andy HuntとDave Thomasが、著書「達人プログラマ」の中で提唱した原則。単に「コードを重複させない」という原則ではなく、DBスキーマ、テスト、ビルドシステム、ドキュメントなども対象になっており、「ソフトウェア開発全体において情報を重複させない」という原則。DRYは素晴らしい考えですが、やり過ぎると密結合を生んでしまう。

#### 22.5.2. OAOO (Once And Only Once)

「コードを重複させない」という原則。

#### 22.5.3. SOLID

単一責任の原則。以下の頭文字をとった言葉である。詳細は参照リンクが詳しいのですが、概念には納得できたとしても、日々の業務の中で善管的に実行するのは難しいですね。しかし、あくまで原則であり、適用できないケースがまさにケースバイケースなのだとすると、ツールに仕込むことも難しいのかもしれません。

1. Single Responsibility Principle：単一責任の原則
2. Open/closed principle：オープン/クロースドの原則
3. Liskov substitution principle：リスコフの置換原則
4. Interface segregation principle：インターフェース分離の原則
5. Dependency inversion principle：依存性逆転の原則

<https://note.com/erukiti/n/n67b323d1f7c5>
<https://qiita.com/baby-degu/items/d058a62f145235a0f007>

#### 22.5.4. KISS (Keep It Simple, Stupid)

シンプルにしておけ、愚か者よ。の意。コードを書くとき、「単純性」や「簡潔性」を最重要視せよということ。元々は Stupid ではなかったそうなのですが、語呂が良すぎて Stupid になりました。

<https://qiita.com/DeployCat/items/09bb6831b029f5185b33>
<https://qiita.com/ryotanatsume/items/018cae5c5be8faba367a>

#### 22.5.5. YAGNI (You Aren't Going to Need it.)

それはきっと必要にならない、の意。コードが必要最低限にしろということ。

あらかじめ、いろいろな事態に備えてコードを盛り込んでおいても、結局は利用されないことが多い。そして、それによってコードに「余計な」複雑性を盛り込んでしまうことになり、KISSに思想にも反する

<https://qiita.com/ryotanatsume/items/018cae5c5be8faba367a>
<https://hawk-tech-blog.com/principle-yagni/>
<http://sukikoba.com/2018/05/11/yagni/>

## 23. Agile Development Practices

こちらはアジャイル開発の中の、より具体的なプラクティスになるので、上述の概念よりは分かりやすいかもです。しかし、上位の概念のせいか、こちらもカテゴライズの定義自体がすごく曖昧です。TDDなどが何かメモしたいので用意した章です。例えばこういうものがあります。開発だとか設計だとか若干入り乱れてるのですが、あしからず。

- TDD (Test Driven Development)：　テスト駆動開発
- BDD (Behavior Driven Development)：　振舞駆動開発
- DDD (Domain Driven Design)：　ドメイン駆動開発

他にもこういうものがあります。聞いたことがありませんでした。

- ATDD (Acceptance Test-Driven Development)：　受入テスト駆動開発
- ADD (Attribute Driven Design)：　品質特性駆動型設計
- FDD (Feature-Driven Development)：　ユーザー機能駆動開発
- MDD (Model Driven Development)：　モデル駆動開発
- UCDD (Use Case Driven Development)：　ユースケース駆動開発
- PDD (Proof Driven Development)：　証明駆動開発

<https://en.wikipedia.org/wiki/Agile_software_development#Agile_software_development_practices>

### 23.1. TDD (Test Driven Development)

テスト駆動開発。主に開発者が対象。

最初にテストケースを作成してから、それらのテストケースの基礎となるコードを記述します。テストファーストに基づく設計手法で、軽快なフィードバック、きれいで動くコードを作ろうという開発プロセスです。ユニットテストを使ったテスト技法といった程度に見られていますけど、本当はシステムテストも含んだ開発全般を含んでいます。

TDDに続く開発者にとって最も難しいことは、コードを書く前にテストケースを書くことです。基本的に自動テストを想定しています。TDDをサポートするツールには、JUnit、TestNG、NUnitなどがあります。

<https://ja.myservername.com/tdd-vs-bdd-analyze-differences-with-examples>
<https://qiita.com/kenji-yokoi/items/6b07a62415b56a959caf>
<https://www.browserstack.com/guide/tdd-vs-bdd-vs-atdd>

### 23.2. BDD (Behavior Driven Development)

振舞駆動開発。開発者、利用者、QA（Quality Assurance：品質管理）の全員が対象。

TDDがテストという言葉が先行してしまったので、改めて提唱されたのが振舞駆動開発。システムに期待されている「振る舞い」や「制約条件」を上位レベルからテストしようという開発手法です。TDDの拡張/改訂版です。Gherkin記法（Given/When/Then）という特定の記法を用いる。

プロセスは、予想される動作に従ってシナリオを作成することから始まります。シナリオは単純な英語形式で記述されているため、TDDと比較すると読みやすくなっています。テストケースにしてもシナリオ自体は最初は文章で書くはずなんですがね。。そのあたりはちょっと謎。

<https://qiita.com/kenji-yokoi/items/6b07a62415b56a959caf>
[https://www.it-mure.jp.net/ja/tdd/bddとtddのテストケースの作成の違いは何ですか？/l967293690/](https://www.it-mure.jp.net/ja/tdd/bdd%E3%81%A8tdd%E3%81%AE%E3%83%86%E3%82%B9%E3%83%88%E3%82%B1%E3%83%BC%E3%82%B9%E3%81%AE%E4%BD%9C%E6%88%90%E3%81%AE%E9%81%95%E3%81%84%E3%81%AF%E4%BD%95%E3%81%A7%E3%81%99%E3%81%8B%EF%BC%9F/l967293690/)
<https://ja.myservername.com/tdd-vs-bdd-analyze-differences-with-examples>
<https://www.browserstack.com/guide/tdd-vs-bdd-vs-atdd>

#### 23.2.1. BDD Tools and Frameworks

下記のような自然言語で実装できるフレームワークが登場しています。xSpecとは、Rubyの「RSpec」を始祖とするテスティングフレームワークの総称で、JBehaveと比較してよりコードの見やすさやドキュメンテーションの作りやすさに注力している。SpecとはTestを指す。

- Cucumber：　JS用のBDDフレームワーク。<https://cucumber.io/>
- JBehave：　Java用のBDDフレームワーク。<https://jbehave.org/>
- RSpec：　Ruby用のBDDフレームワーク。
- CSpec / C++Spec：　CやC++用のBDDフレームワーク。<https://toroidal-code.github.io/cppspec/>
- SpecFlow：　.NET用のBDDフレームワーク。<https://specflow.org/>

<https://xspec.io/about/>

<https://atmarkit.itmedia.co.jp/ait/articles/1403/25/news033_3.html>

### 23.3. DDD (Domain Driven Design)

ドメインとはシステムが対象とする業務知識や適応範囲です。

<https://qiita.com/kenji-yokoi/items/6b07a62415b56a959caf>

### 23.4. ATDD (Acceptance Test Driven Development)

受入テスト駆動開発。開発者、利用者、QA（Quality Assurance：品質管理）の全員が対象。

受入テストを先に書く。ATDDで決めた仕様は受入基準となります。その受入基準はまた受入テストのもととなります。テストシナリオはATDDのツールで実装したE2Eテストと紐付きます。それによって、決めた仕様がテストとマッピングされます。BDDはGherkin記法（Given/When/Then）という特定の記法を用いるのに対して、ATDDには厳密な記法の指定はない。

ATDDを導入するとこによって、書いた仕様書（受入基準）と受入テストが連動されるので、ドキュメントとソースコードのズレが生じにくいです。これは本当ならばかなりでかいですね。

<https://qiita.com/kenji-yokoi/items/6b07a62415b56a959caf>
<https://qiita.com/abchyw8611/items/54b84b77ef87755fdf3e>
<https://www.browserstack.com/guide/tdd-vs-bdd-vs-atdd>

#### 23.4.1. ATDD Tools and Frameworks

主なテストフレームワークは、

- Cucumber：　有名なBDDツール。Gherkin Syntax。<https://cucumber.io/>
- Gauge：　ThoughtWorks社がメンテしているGo製の受入テスト自動化フレームワーク。Markdownベースのシンプルな仕様記述Syntax。ステップ実装のための言語は Java/JS/TS/Python/Ruby/C# をサポート。<https://gauge.org/>
- その他：　Serenity、Concordion、KARMA、FitNesse、Robot Framework など

### 23.5. ADD (Attribute Driven Design)

品質特性を基にモジュール分割を再帰的に行う開発プロセス。

[https://qiita.com/kenji-yokoi/items/6b07a62415b56a959caf](https://qiita.com/kenji-yokoi/items/6b07a62415b56a959caf#:~:text=%E5%93%81%E8%B3%AA%E7%89%B9%E6%80%A7%E9%A7%86%E5%8B%95%E5%9E%8B%E8%A8%AD%E8%A8%88,%E3%81%AB%E8%90%BD%E3%81%A8%E3%81%97%E8%BE%BC%E3%82%93%E3%81%A7%E3%81%84%E3%81%8D%E3%81%BE%E3%81%99%E3%80%82)

### 23.6. FDD (Feature Driven Development)

ユーザーには価値を提供しなければなりません。概念モデルからユーザーに提供する価値を抽出し、インクリメンタルな開発を行う手法。

<https://qiita.com/kenji-yokoi/items/6b07a62415b56a959caf>

### 23.7. MDD (Model Driven Development)

設計とアーキテクチャがそれぞれ独立して変更するための開発手法。ドメイン固有言語(domain-specific language; DSL)を使ってシステムに依存しない設計を行い、プラットフォームに特化したモデルに変換する。

<https://qiita.com/kenji-yokoi/items/6b07a62415b56a959caf>

### 23.8. UCDD (Use Case Driven Development)

システムに関わるアクターを識別し、アクターの振舞をユースケースとして定義します。ユースケースを実現するためにロバストネス分析を行い、システム設計に落とし込んでいきます。

<https://qiita.com/kenji-yokoi/items/6b07a62415b56a959caf>

### 23.9. PDD (Proof Driven Development)

証明によってプログラムが期待通りの性質を有しているかを確かめながら開発していきます。数学的な観点ですね。Coq/Gallina といった定理証明支援系言語を使ってテストを行います。

<https://qiita.com/kenji-yokoi/items/6b07a62415b56a959caf>

## 24. Testing Pyramid

Mike Cohn が2009年に提唱した概念。これは言葉としては聞いたことがなくても、開発をしたことがあれば通ったことのある道です。ピラミッドの下から書くと、

- Unit Test：　単体テスト
- Integration Test：　結合テスト。Service Test ともいう。他システムとのデータ連携などがある場合は、内部結合と外部結合とわかれることもある。
- E2E Test：　総合テスト。UI Test (User Interface Test) ともいう

<https://speakerdeck.com/hgsgtk/atdd-by-genba-example?slide=24>

<https://www.amazon.co.jp/dp/B002TIOYWQ>

### 24.1. Unit Test

単体テスト。プログラムを構成する比較的小さな単位（ユニット）が個々の機能を正しく果たしているかどうかを検証するテスト。プログラムが全体として正しく動作しているかを検証する結合テストは、開発の比較的後の段階でQAチームなどによって行なわれることが多いのとは対照的に、単体テストは、コード作成時などの早い段階で開発者によって実施されることが多いのが特徴。

単体テストの中にも種類が大きく2つある。

- White-Box Testing
- Black-Box Testing

<https://www.techmatrix.co.jp/t/quality/unittest.html>

#### 24.1.1. White-Box Testing

開発者などコードレベルで理解してる人が作る場合。

テスト対象関数またはメソッドの内部構造に着目し、条件分岐や繰り返しなどの各部分を確実にテストします。

- 関数・メソッド中のすべての命令を実行する命令網羅（ステートメントカバレッジ）
- すべての分岐条件で真/偽の両方の分岐を通るようにする判定条件網羅（デシジョンカバレッジ、または分岐網羅、ブランチカバレッジとも呼ばれます）

などがあります。そのため、網羅率の測定（カバレッジ解析）や条件を網羅するためのテスト値の抽出などが必要。

<https://www.techmatrix.co.jp/t/quality/unittest.html>
<https://qiita.com/mikimaromomose/items/ef12e3823d81bf537c10>
<https://qiita.com/masatakaaaa/items/ca8a05ce9bd3fb0e4637>

#### 24.1.2. Automated Testing

自動化テスト。特に単体テストレベルであれば、自動化を行えると大きい。自動化のタイミングは夜間の間や、デプロイ時、手動トリガーなど色々ある。完全手動の場合、現実問題、やられないことが起きやすい。

自動化テストのためのフレームワークは各言語ごとに色々あるが、総称して、xUnitフレームワークとカテゴライズされている。xUnitフレームワークは、テストの実行および結果の検証機能を提供します。テストケースはすべてコードとして作成されるので、もちろん自動実行が可能です。ただし、基本的にはテストケースの生成機能は提供しないため、自力でテストケースを作成する必要がある

<https://www.techmatrix.co.jp/t/quality/unittest.html>

#### 24.1.3. Coding Coverage

ホワイトボックステストに対する計測指標。どれがいい悪いもあるでしょうが、これまで不具合が多いにもかかわらず、何も測ってなかったのであれば、まずは測れそうなものから測っていくことが肝要。

コードカバレッジツールでは、コードの実行を監視するステートメントをコードの必要な箇所に挿入する静的インスツルメンテーションを使用します。

下に示すように、指標はいくつも種類があります。下記のようなコードを例にとると主に、

```jsx
if(条件文a1 || 条件文a2){ // 判定条件A
  命令文X;
}

if(条件文b1 || 条件文b2){ // 判定条件B
  命令文Y;
} else{
  命令文Z;
}
```

- Statement Coverage (C0)：　命令網羅率。それぞれの命令文が少なくとも1回は実行されれば、カバレッジ率＝100％
- Branch Coverage (C1)：　分岐網羅率。それぞれの判定条件（IF文など）の分岐における真偽（True or False）が少なくとも1回実行されれば、カバレッジ率＝100％。C1カバレッジ率＝100％の場合、C0カバレッジ率も100％となる
- Condition Coverage (C2)：　条件網羅率。それぞれの判定条件の中の複数の条件文における真偽が少なくとも1回実行されれば、カバレッジ率＝100％。C2カバレッジ率＝100％でも、C1・C2カバレッジ率＝100％になるとは限らない

があります。他にも、

- Function Coverage：　すべての関数のうち、テストで最低1回実行された関数の割合
- Call Coverage：　すべての関数呼び出しのうち、テストで呼び出された関数の割合
- Loop Coverage：　すべてのループのうち、テストで最低1回実行されたループの割合
- Line Coverage：　行網羅率。すべての実行可能な行数の内、実行された行の割合
- Path Coverage：　すべてのパス（可能な実行経路）のうち、テストで実行されたパスの割合
- Opcode Coverage：　関数やメソッドのオペコードが、 テストスイートの実行中に実行されたかどうかを計測します。 通常は、1 行のコードをコンパイルすると、複数のオペコードになります。 ラインカバレッジは、複数のオペコードのうち少なくともひとつが実行された時点で、 その行が実行されたとみなします。
- Block Coverage：　すべてのブロックのうち、テストで実行されたブロックの割合です。ブロックは、if文などによる分岐を含まない一連のステートメント
- Multiple Condition Coverage (MCC)：　複合条件網羅率。すべてのパターンをテストする。組み合わせの要素が増えるにしたがって、パターンがべき乗で増えていくため、現実的にできないし、しないことが多い

などがあります。できれば、1つの指標だけではなく、2つ以上の指標で多角的に見たいですね。

<https://www.techmatrix.co.jp/t/quality/coverage.html>
<https://qiita.com/bremen/items/8b6542467d2a0066e5af>
<https://www.browserstack.com/guide/code-coverage-vs-test-coverage>
<https://phpunit.readthedocs.io/ja/latest/code-coverage-analysis.html>

### 24.2. Integration Test

結合テスト。自社システム内のモジュール間の結合テストであれば内部結合テスト、社外の外部システムも含めた結合テストであれば外部結合テストと言ったりする。

ユーザーストーリーに則ったシナリオは総合テストで行うのであれば、総合テストがシナリオを検証する以前の通信で失敗したりしないように、外部結合テストは外部システムとの疎通テストにとどまる場合もある。

外部システムとの結合テストがない場合は、内部結合テストが事実上の総合テストやE2Eテストに該当する場合もある。いずれにしても、内外に定義を文章として明確にするのは最低限必要であると思われる。

### 24.3. E2E Test (End to End Test)

E2E (End to End) テストとは、システム全体が正しく動作することを確認するものです。具体的には「利用者による画面操作（Web ブラウザの操作）により、想定通りの動作となっていることを確認する」ことを指します。

E2E テストは「総合テスト」フェーズで実施されます。多くの開発現場で E2E テストはテスト仕様書を元に、人手でテストを行っています。そのためテスト工数の削減は大きな課題となっていました。そう、まさにその通りで、開発現場によっては納期を守るために「ウソ」が発生することもあります。また自動化されていなければ、総合テスト中に追加機能が実装されて（それもどうなのというのはさておき、ありうる）、その部分は結局総合テストしきれなくて無視される、なんてことも起こりうるでしょう。

<https://wagby.com/manual9/wtf.html>
<https://qiita.com/abchyw8611/items/54b84b77ef87755fdf3e>
<https://qiita.com/mt0m/items/7e18d8802843d9f60d28>

#### 24.3.1. Black-Box Testing

主に総合テストや受入テストなど後半のテストが該当。

テスト対象関数またはメソッドの外から見た機能（入出力）に着目し、コードが期待される機能（仕様）を満たしているかどうかを検証します。仕様に関わる検証であるため、テストケースの作成や結果の確認には、人間による判断が必要。

内部構造はさておき、そもそも元々達成したかった○○は出来てんの？という視点で行う。

<https://www.techmatrix.co.jp/t/quality/unittest.html>
<https://qiita.com/mikimaromomose/items/ef12e3823d81bf537c10>
<https://qiita.com/masatakaaaa/items/ca8a05ce9bd3fb0e4637>

#### 24.3.2. E2E Test Frameworks

主なテストフレームワークは、selenideなど。本家のselenium自体はテストクレームワークではないので、テストを書くのはつらいですが、selenideはseleniumをうまいことwrapして、テストに特化するlibraryで、使い心地がseleniumよりよいです。他にも、WebdriverIOや、Nightmareなどがあります。

#### 24.3.3. E2E Test の不安定さ

テストケースが不安定になると工数が増大しますが、その例としてテスト時のアカウント共有などがあります。「ログイン状態であることをテストしようとしたら、別の人が実行しているテストでログアウトしていて失敗する」「登録できることをテストしようとしたら、別の人が実行しているテストですでに登録しているので失敗する」などです。これはテストケース毎にユーザアカウントを分離したり、アカウントIDにタイムスタンプをつけてテスト実行毎にユニークなアカウントを作成して対応するケースが多いようです。

### 24.4. Feedback Cycle

テストしたら、その結果を早く知り、原因を探し、修正して、再度テスト！というサイクルを早く回す必要があります。だいたいの場合、当初スケジュールに比較して、開発が遅れていて、テスト開始日が遅れていて、でも納期は変わってない、なんてことが起こります。また、テスト工数の見積もり時に、何回もテストが失敗し、何回もコードを修正するような見積もりはされてないことが多いです。そのため、このフィードバックサイクルは仕組みとしてあった方がよいでしょう。

- テストの実行：　Slackのslash commandでテストを実行など
- テスト結果の通知：　SlackのテストChannelに通知など。まあこれを無視してしまうようなボリュームになってきたら、また改善は必要ですが。
- テスト結果のエビデンス作成：　脱Excelにぺたぺた
- テスト結果のレビュー：　基準を決めて人が見るべきものと、見ないものとわけられるといいです。全部見るべき！とか言ってると、結局現場ではどれも見てない、なんてこともありえます

<https://qiita.com/mt0m/items/7e18d8802843d9f60d28>

## 25. Infrastructure

インフラパート。クラウドだと、AWSやGCP、Microsoft Azureなど。AWSを例にメモしていきます。

### 25.1. AWS Service

AWSの全体像はこんな感じ。落ちてるものから分かりやすかったものをいくつか拾ってきた。まずは公式サイトのAmazonにあるWEBアプリケーションのよくある構成。（AWSのサイトで拾ったので、全部AWSサービスで構成されているが・・・）

![AWSの構成イメージ](2021-09-27-23-04-13.png)

<https://docs.aws.amazon.com/whitepapers/latest/web-application-hosting-best-practices/an-aws-cloud-architecture-for-web-hosting.html>

### 25.2. AWSの各種用語

#### 25.2.1. VPC (Virtual Private Cloud)

AWS内の自分用の領域

#### 25.2.2. Internet Gateway

図には載ってないが、VPCとインターネットをつなぐGateway。これを使うことで、VPC内のシステムがグローバルIPを使えるようになります。

#### 25.2.3. Virtual Private Gateway

インターネットGatewayがインターネットに接続するのに対し、こちらはオンプレミス環境に接続するためのゲートウェイ

#### 25.2.4. NAT Gateway (a Network Address Translation Gateway)

VPC内に構成した「プライベートサブネット」からインターネットに接続するためのゲートウェイ。公式サイトから持ってきた上図とはなんか逆ですが、調べる限り、「プライベートサブネットから」出るため用のようです
<https://docs.aws.amazon.com/ja_jp/vpc/latest/userguide/vpc-nat-gateway.html>

#### 25.2.5. Subnet

サブネット。VPCという大きなネットワークをIPアドレスの範囲で分割した小さなネットワークのこと

- Public Subnet：　インターネットゲートウェイに接続ができるサブネット
- Private Subnet：　インターネットに接続できないサブネットの中に配置したシステム

#### 25.2.6. Route Table

サブネット内のリソースがどこに通信するのか？というルールを定めた表のこと。サブネットを作成すると、ローカル（作成したVPC内）と通信できますよ〜という設定がされたルートテーブルが自動で作成されます。サブネットによっては、ここにインターネットとも通信ができるようなルートも追加する

#### 25.2.7. Amazon Route 53

DNSサーバー。

#### 25.2.8. Amazon S3 (Amazon Simple Storage Service)

高確率で使う。データためるところ。「オブジェクトストレージ」というタイプのストレージサービスであり、データを「オブジェクト」と呼ばれる単位で読み書きするためのHTTPSなどでアクセス可能なエンドポイントを提供。Amazon EFSに比べると安い分、直接読むことは出来ず、一度SCP（コピー）してこないと取り出せない

#### 25.2.9. Amazon EFS (Amazon Elastic File System)

ファイルサーバー。S3より取り出しやすい分、料金が高い。「ファイルストレージ」というタイプのストレージサービスであり、LinuxなどのOSでマウント可能なファイルシステムを提供。マウントすることで複数のEC2インスタンスから参照が可能。読み書きスピードは若干遅い

#### 25.2.10. Amazon EBS (Amazon Elastic Block Store)

直接上には出てこないが、別の種類のストレージ。「ブロックストレージ」というタイプのストレージサービスであり、Amazon Elastic Compute Cloud (EC2)のインスタンス(仮想マシン)にアタッチするためのボリュームを提供。

#### 25.2.11. Amazon ECS (Amazon Elastic Container Service)

完全マネージド型コンテナオーケストレーションサービスであり、コンテナ化されたアプリケーションを簡単にデプロイ、管理、スケール。AWS Fargate のサーバーレス技術を利用して、自律型のコンテナ運用を実現し、設定やパッチ適用、セキュリティに要する時間を削減。<https://aws.amazon.com/jp/ecs/>

#### 25.2.12. Amazon ElastiCache

AmazonでRedisやMemcachedを使えるサービス。綴りはCが足りてないが、間違いではない。

#### 25.2.13. Amazon DynamoDB

キーバリューおよびドキュメントデータ構造をサポートする、フルマネージドな独自のNoSQLデータベースサービスで、Amazon.comがAmazon Web Servicesポートフォリオの一部として提供しています。

#### 25.2.14. Amazon API Gateway

あらゆる規模の REST、HTTP、および WebSocket API を作成、公開、維持、モニタリング、およびセキュア化するための AWS のサービス。<https://docs.aws.amazon.com/ja_jp/apigateway/latest/developerguide/welcome.html>

#### 25.2.15. AWS Lambda

サーバーレスコンピューティングサービスで、サーバーのプロビジョニングや管理、ワークロード対応のクラスタースケーリングロジックの作成、イベント統合の維持、ランタイムの管理を行わずにコードを実行できます。Lambda を使用すれば、実質どのようなタイプのアプリケーションやバックエンドサービスでも管理を必要とせずに実行できます。<https://aws.amazon.com/jp/lambda/>

#### 25.2.16. Amazon CloudFront

CDN機能を提供。それ以外にも利点が2つある。1つ目はCloudFrontが、リクエストに応じて各AWSサービスに振り分ける、リバースプロキシの役割を提供する点。2つ目は静的コンテンツからAPIを実行した場合にクリアしなければいけないCORS（Cross-Origin Resource Sharing）の課題が回避できる点

#### 25.2.17. AWS Certificate Manager

パブリックおよびプライベートのSSL/TLS（Secure Sockets Layer/Transport Layer Security）証明書を簡単にプロビジョニング、管理、導入して、AWSサービスや社内の接続リソースで使用できるようにするサービス。プロビジョニングは、IT インフラストラクチャをセットアップするプロセスです。また、データとリソースへのアクセスを管理し、ユーザーとシステムによる利用を可能にするために必要なステップを指すこともあります。

<https://business.ntt-east.co.jp/content/cloudsolution/column-64.html>
<https://zenn.dev/tomoshimizu/articles/6945b7ac472ca0>
<https://www.bit-drive.ne.jp/managed-cloud/column/column_31.html>

#### 25.2.18. Amazon Cognito

Amazon Cognito を使用すれば、ウェブアプリケーションおよびモバイルアプリに素早く簡単にユーザーのサインアップ/サインインおよびアクセスコントロールの機能を追加できます。

<https://aws.amazon.com/jp/cognito/>
<https://dev.classmethod.jp/articles/re-introduction-2020-amazon-cognito/>

#### 25.2.19. AWS Fargate

コンテナ向けサーバーレスコンピューティング。サーバーのスケーリング、パッチ適用、セキュリティ、管理などの運用上のオーバーヘッドを取り除きます。

<https://aws.amazon.com/jp/fargate/>

#### 25.2.20. Amazon Aurora

クラウド向けに構築された、MySQL および PostgreSQL と互換性のあるリレーショナルデータベースです。商用データベースと同等のパフォーマンスと可用性を、10 分の 1 のコストで実現。

<https://aws.amazon.com/jp/rds/aurora/?aurora-whats-new.sort-by=item.additionalFields.postDateTime&aurora-whats-new.sort-order=desc>

#### 25.2.21. Amazon Kinesis Data Firehose

リアルタイム配信用の完全マネージド型サービス

<https://docs.aws.amazon.com/ja_jp/firehose/latest/dev/what-is-this-service.html>

### 25.3. Managed Services

Managed Servicesのメリットは以下。サーバーレスのこと。

- 常時起動するわけではないため、利用料を抑えることができる
- 負荷に応じて、自動でスケールアウト／スケールインが行われる
- インフラ、OS、ミドルウェアのメンテナンスが不要
- サーバ自体がないため、セキュリティのリスクや対処負担が減る

### 25.4. Load Balancer

サーバーにかかる負荷を、平等に振り分けるための装置のことを指します。これによって1つのサーバーにかかる負担を軽減したり、停止状態を防ぐことができたりします。SSLアクセラレーターを使用することにより、本来サーバーごとに必要なSSL証明書を1本化したり、暗号化通信の負荷を軽減できたりします。

![LBのイメージ](2021-09-27-23-08-52.png)

<https://www.kagoya.jp/howto/it-glossary/network/loadvalancer/>

#### 25.4.1. LBの負荷分散方法

負荷分散の方法はいくつかある

- ラウンドロビン方式：　順番に単純に振り分ける。
- 動的分散方式：　サーバーのCPUやメモリ使用率などの負荷状況を加味して軽いところに振り分ける
- パーシステンス：　ログイン情報など同じユーザーは同じWEBサーバーの方がありがたい場合がある。これを加味する

## 26. Serverless Hosting Service

AWSやGCPもサーバーレスを提供しているが、使い勝手の良いサーバーレスなホスティングサービスは他にもある。ちなみにホスティングとは、サーバーを貸し出すこと。日本だとレンタルサーバーのことだが、クラウドも含む広義な言葉。

- Firebase
- Netlify
- Vercel
- Heroku
- Supabase
- Gatsby Cloud

<https://qiita.com/asahi13/items/84582438371ca6ecd834>
<https://qiita.com/fussy113/items/ba204747e3f0e6c59af0>
<https://qiita.com/0622okakyo/items/65b8c5e7d09ac383e9a0>
<https://www.jaipa.or.jp/hosting/about2.html>

### 26.1. Firebase

2011年設立。米有力VCのYCombinator卒業。2014年にGoogleが買収。以降、Googleが管理・開発しているBaaS（Backend as a service）。なので、がっつりGoogleがバックにサポートしたサービスになってます。Spark Planが無料プラン。

対応言語：Node.js, C++. Kotlin, Java, Object-C, Swift。モバイルアプリ開発に使われることも多いので、mBaaS(mobile backend as a Service)と呼ばれたりもします。例えばNuxt.jsを利用して開発したSPAをインターネット上で配信する際にバックエンドで必要となる機能は、大きく分けて下記の点。

![Firebaseのイメージ](2021-09-27-23-09-55.png)

<https://firebase.google.com/>
<https://www.ycombinator.com/companies/firebase>
<https://www.amazon.co.jp/gp/product/B08NSZJZ4Q/ref=ppx_yo_dt_b_d_asin_title_o09?ie=UTF8&psc=1>
<https://zenn.dev/razokulover/scraps/94844e54e519ed>
<https://qiita.com/0622okakyo/items/65b8c5e7d09ac383e9a0>

#### 26.1.1. Firebase Hosting

ホスティングサービス。

#### 26.1.2. Firestore

Firebaseが提供する、ドキュメント指向データベース。

#### 26.1.3. Firebase Authentication

ユーザー認証基盤

#### Firebase のその他の機能

Googleがバックなので、Google Analytics など各種サービスが連携しやすい。

### 26.2. Netlify

最新のWebプロジェクトを自動化するためのオールインワンプラットフォーム。対応言語：Node.js, Golangなど。

ホスティングインフラストラクチャ、継続的統合、展開パイプラインを単一のワークフローに置き換えます。プロジェクトの成長に応じて、サーバーレス機能、ユーザー認証、フォーム処理などの動的機能を統合します。

mainブランチが新しくなる度に都度デプロイするが、その他にHTTPリクエストを受けてデプロイを行う Build Hooksという仕組みもある

<https://megumu.me/posts/20210212/>
<https://qiita.com/0622okakyo/items/65b8c5e7d09ac383e9a0>

### 26.3. Vercel

Vercel（企業名）によって運営/開発されている、FaaS（Function as a Service）。DNSやCDNサービスも展開しているため、PaaS（Platform as a Service）と言っても良いかもしれません。対応言語：Next.js, Node.js, Python, Golang, Rubyなど

16ものエッジロケーションを備えるCDNやサーバレスファンクションは、AWSまたはGCPなどの大手クラウドコンピューティングプラットフォームのリソースを抽象化したもので、利用者がAWSやGCPを意識することはほとんどありません。また従来の“サーバレスアーキテクチャ”を謳うSaaSとは異なり、サーバのスペックを選択できなかったり、ほとんどの設定が自動で行われ、かつ無効にすることができなかったりと、サーバの存在がほとんど隠蔽されているサービス。

<https://qiita.com/jagaapple/items/faf125e28f8c2860269c>
<https://zenn.dev/razokulover/scraps/94844e54e519ed>
<https://qiita.com/0622okakyo/items/65b8c5e7d09ac383e9a0>

### 26.4. Heroku

Salesforceが買収した、PaaS(Platform as a Service)です。ユーザーのインフラ管理が不要で、「git push」を行うだけでリリースが行えたり、各種アドオンの追加で、ミドルウェアのインストールを行うことができます。

<https://jp.heroku.com/>
<https://qiita.com/0622okakyo/items/65b8c5e7d09ac383e9a0>

### 26.5. Supabase

同じくYC卒業。オープンソースFirebaseの代替。2分以内にバックエンドを作成できます。Postgresデータベース、認証、インスタントAPI、リアルタイムサブスクリプション、ストレージを備えたプロジェクトを開始できます。

<https://supabase.io/>
<https://techcrunch.com/2020/12/15/supabase-raises-6m-for-its-open-source-firebase-alternative/>

### 26.6. Gatsby Cloud

特にGatsbyのビルド・ホスティングに特化したサービス。ビルド時にGoogle Lighthouse のレポート作成までしてくれる。Gatsbyを使うなら使いたい。ホスティングには裏でFastlyというCDNを利用している

## 27. Infrastructure Monitoring

インフラ監視・分析。限りなく100%に近い稼動を必要とするシステムの場合、ハードウェアやソフトウェアの保守管理はもちろん、システムそのものが常に正常に稼動しているかを見守る必要があります。そして、もしもシステムに問題が発生したときにはいち早くそれを発見して対応する必要があります。

システム監視とは、システム内で動作しているサーバ、アプリケーション、ネットワークなどが正常に稼働しているか定期的に確認することによって、システムで発生した障害やリソース不足を検知し、システム管理者に通知を行うための作業や仕組みのこと

<https://www.itmanage.co.jp/column/system-monitoring-item-list/>
<https://www.bit-drive.ne.jp/managed-cloud/column/column_06.html>
<https://qiita.com/inagacky/items/43cc0518ef11f1e4beb3>

### 27.1. Monitoring の種類

インフラ監視の種類は様々あり、それをあげていきます。

<https://www.itprotoday.com/containers/it-monitoring-moves-beyond-way-beyond-infrastructure-and-application-monitoring>

#### 27.1.1. 死活監視

対象機器にPINGをおくり、それを受け取った機器が送り返す応答を確認することで機器が動作しているとみなす監視方法で、稼働監視とも呼びます。サーバやネットワークの監視によく使われる方法で、PING応答がなかった場合、対象機器か経路のネットワークかのどちらかに問題があります。

#### 27.1.2. リソース監視

CPU、メモリ、ディスク、ネットワークなど、OSやサーバ、ハードウェア、ネットワーク機器などのリソース使用状況をチェックすることで、性能監視とも呼ばれます。

#### 27.1.3. 接続監視

ネットワークの指定ポートへ接続をし応答があることを監視することです。ネットワークがダウンしていないか、あるいは性能低下でレスポンスが悪化していないかを調べる目的で行われます。

#### 27.1.4. ログ監視

サーバからの収集したログを監視することです。予めログに含まれる文字列やキーワードをもとに監視をし、設定したキーワードのログが検知するとアラートがでる仕組み

#### 27.1.5. プロセス/サービス監視

サーバ上で稼働をするプロセスやサービスをまとめてアプリケーションとして定義をしプロセスの生死やWindowsサービスの状態によってアプリケーションが正常に動作しているかを監視すること。

<https://www.itmanage.co.jp/column/system-monitoring-item-list/>

### 27.2. 監視サービス

#### 27.2.1. Amazon CloudWatch

AWSが提供する「フルマネージド運用監視サービス」で、AWSの各種リソースを監視してくれるもの。AWSでやるなら、せっかく用意してくれてるわけだし、これでいいかも。

- CloudWatch：　リソースを監視する。CPUやメモリなど複数項目をグラフ化してダッシュボードを作れます。
- CloudWatch Logs：　ログを集めて監視する。Amazon Linux、RedHat、Windowsなどに対応し、インスタンスにエージェントを入れることで各種ログを取得します。OSに加えて、アプリケーションのログも対応していて、キーワードでアラート通知させることもできます。つまり「アプリケーションやOSがエラーログ吐いたら管理者のメールに通知」が実現できる
- CloudWatch Events：　APIのイベントをトリガーに何らかのアクションを実行させる、というサービスです。APIというとなにか特殊な用途に思えますが、AWSはさまざまな処理をAPIで実行しています。たとえばEC2インスタンスの起動停止もAPIで実行するんですね。こういったイベントを監視するのがCloudWatch Events、ということです。具体的には、インスタンスのterminate（削除）でアラート通知する、コンソールに特定のユーザがサインインしたときにアラート通知する、ということなんかができるそう。

<https://www.bit-drive.ne.jp/managed-cloud/column/column_06.html>

#### 27.2.2. Datadog

クラウド型の監視アプリケーションサービスです。SaaSベースのデータ分析プラットフォームを介してサーバー、データベース、ツール、およびサービスの監視を提供します。<https://www.datadoghq.com/ja/>

#### 27.2.3. Mackerel

はてなが開発したサーバー管理・監視サービスです。仮想サーバーなどクラウドサービスをMackerelで統合管理および監視することができます。<https://mackerel.io/ja/>

#### 27.2.4. Prometheus

SoundCloudが中心になって開発しているプル型のリソース監視ツールです。サーバー管理・監視や、しきい値を超えた場合のアラート等を行うことができます。UIがかっこいいです。<https://prometheus.io/>

#### 27.2.5. Zabbix

ネットワーク管理のソフトウェアです。こちらもサーバー管理・監視や、しきい値を超えた場合のアラート等を行うことができます。C言語、PHP、JavaScriptで記述されてるらしいです。2004年に初版がリリースされ、比較的歴史が長いツールです。<https://www.zabbix.com/jp>

#### 27.2.6. Sentry

イベントログ収集(エラー検知)のSaaSサービスになります。バックエンドのエラーのみならず、フロントエンドのエラーを収集して、可視化することができます。<https://sentry.io/>

#### 27.2.7. New Relic

インフラからアプリケーションまで監視・分析してくれるSaaSサービスになります。<https://newrelic.co.jp/>

## 28. Virtualization vs Containerization

仮想化とコンテナ化技術。仮想化とコンテナ化は似ているが異なる。

- 仮想化：　ソフトウェアによって複数のハードウェアを統合し、自由なスペックでハードウェアを再現する技術で、限られた数量の物理リソース（CPU、メモリ、ハードディスク、ネットワーク等）を、実際の数量以上のリソース（論理リソース）が稼働しているかのように見せかけること。<https://www.fsi.co.jp/solution/vmware/knowledge/virtualization.html>
- コンテナ化：　ソフトウェアのコードをライブラリやフレームワークなどの依存関係にあるすべてのコンポーネントとともにパッケージ化し、それぞれの入れ物、「コンテナ」に隔離すること。<https://www.redhat.com/ja/topics/cloud-native-apps/what-is-containerization>

### 28.1. Virtualization

仮想化技術を使ったサービスやツールをあげていきます。

#### 28.1.1. VirtualBox

オラクルが開発。無料で高機能。

<https://eng-entrance.com/vm-list#VirtualBox-2>

#### 28.1.2. VMware

カリフォルニア州にあるVMware社が販売。

#### 28.1.3. AWS EC2

ワードとしては上述ですが、これも仮想化環境である。ただインスタンスはAMI (Amazon Machine Images) というイメージから作成するところが、コンテナと似ている

### 28.2. Containerization

コンテナ化技術を使ったサービスやツールをあげていきます。

#### 28.2.1. Docker

どこでも聞くようになってきました。コンテナと呼ばれるOSレベルの仮想化環境を提供するオープンソースソフトウェアです。2013年にDocker社が公開。

仮想化を行うツールの中ではディスク使用量は少なく、仮想環境作成や起動は速いらしい。

イメージからコンテナ、コンテナからイメージを作れる。イメージは0から作ることは稀で、Docker Hubという公式が運営するDockerレジストリで取得可能。基本は1コンテナ＝1アプリ。

<https://www.docker.com/>
<https://www.amazon.co.jp/gp/product/B08T961HKP/ref=ppx_yo_dt_b_d_asin_title_o04?ie=UTF8&psc=1>

#### 28.2.2. Kubernetes (K8s)

コンテナ化したアプリケーションのデプロイ、スケーリング、および管理を行うための、コンテナオーケストレーションシステムです。Docker等で構築されたコンテナの管理を行うことができます。

2014年にGoogleによって初めて公開され、その後、Cloud Native Computing Foundation に引き継がれ、オープンソースとして開発・運用がなされている。Googleが開発したのでGOで書かれている。Kubernetes とはギリシャ語で操縦者や統治者を意味する。

ちなみに、K8s の 8 は、Kubernetes の頭と尻の間にある文字数の8から来ています。余談ですが、米著名VCの Andreessen Horowitz も a16z と名乗っています。

<https://kubernetes.io/ja/>
<https://en.wikipedia.org/wiki/Kubernetes>
<https://www.amazon.co.jp/gp/product/B08T961HKP/ref=ppx_yo_dt_b_d_asin_title_o04?ie=UTF8&psc=1>

#### 28.2.3. Micro Kubernetes (Micro K8s)

ローオペ（低運用コスト）、ミニマムプロダクションのKubernetes。開発者、クラウド、クラスター、ワークステーション、エッジ、IoT向け。Canonical社が開発。

MicroK8sは、Kubernetesのデータストアに最適なノードを自動的に選択します。クラスタのデータベースノードを失っても、別のノードが昇格します。防弾エッジに管理者は必要ありません。

<https://microk8s.io/>
<https://qiita.com/ynott/items/89941c36c606a8384028>

#### 28.2.4. Lightweight Kubernetes (K3s)

IoTとエッジコンピューティングのために作られた認定Kubernetesディストリビューション。Rancher Labs社が開発。

無人でリソースに制約のある遠隔地やIoTアプライアンス内の本番ワークロード向けに設計された。40MB以下の単一のバイナリとしてパッケージ化されている。ARM64とARMv7の両方に対応しており、バイナリと multiarch イメージが用意されています。K3s は、Raspberry Pi のような小さなものから、AWS のa1.4xlarge 32GiB サーバーまで、幅広く動作します。

10文字でなるKubernetesの「半分の大きさ」のもの、という意味で5文字のものとなり、それを表現する際に、間の3文字を数字に変えて、k3s となった。

<https://k3s.io/>
<https://github.com/k3s-io/k3s>
<https://qiita.com/ynott/items/89941c36c606a8384028>

## 29. IaC (Infrastructure as Code)

構成管理ツール。あらかじめ設定ファイルを作成することで、それを元にミドルウェアやリソースの配置を行う技術です。一つ設定ファイルを作っておけば、同様の環境を複数立ち上げることができます。

- インストーラをどこからダウンロードしてきたのかわからない
- 設定、どれが初期値で何を変更したのかがわからない
- そもそもどうやってインストールしたのか思い出せない
- というか、手順書がない

こんな悲劇を未然に防ぐのが構成管理ツールです。

<https://qiita.com/inagacky/items/43cc0518ef11f1e4beb3>
<https://qiita.com/pottava/items/5b386a952bf1d26ea387>

### 29.1. Terraform

HashiCorp社が提供するオープンソース。クラウド上のリソース(AWSのインスタンス等々)を定義ファイルに沿った形になるように生成・配置してくれるツールです。構築手順を書くのではなく、完成系を定義ファイルに宣言することで、その構成にしてくれます。開発言語はGo。また、Go言語で書かれたAWS SDKを使用しています。

<https://www.terraform.io/>
<https://www.lac.co.jp/lacwatch/service/20200903_002270.html>

### 29.2. Ansible

レッドハットが開発するオープンソースの構成管理ツールです。あらかじめ用意した設定ファイルに従って、ソフトウェアのインストールや設定を自動的に実行する事が出来ます。Pythonで作成されています。エージェントレス(設定先サーバーにエージェントを入れる必要がない)なことが特徴です。開発言語は、Python, PowerShell, Shell, Ruby。

<https://github.com/ansible/ansible>

### 29.3. Chef

Ruby、Erlangで記述された構成管理ツールです。Ansibleとは異なり、設定先サーバーにエージェントを入れる必要があります。Rubyで記述するため、Rubyが好きな方にはぴったりです。<https://github.com/chef/chef>

## 30. Security

どうしても疎かになりがち。往々にして、クライアントユーザーの制約などで対応を検討するケースが多い気がする。まずはそのリスクの種類とその対策についてメモしていく。

### 30.1. Security Risks

#### 30.1.1. Password Cracking

よく使われる文字列を試す辞書攻撃と、手当たり次第に試すブルートフォース攻撃などがある。ブラウザが推奨するパスワードで入力させるような工夫が求められる

#### 30.1.2. DOS Attack (Denial of Service)

DOS攻撃。SYNパケットを送りまくることでサーバーを接続待ち状態にさせることで別のユーザーが繋げなくするSYN flood攻撃や、リクエストしまくることでサーバー負荷を障害レベルまであげるF5攻撃がある。（F5は画面リロードなので）

#### 30.1.3. DDOS Attack (Distributed DOS)

DDOS攻撃。単一ではない大量のクライアントからのDOS攻撃。Amazonなど防御システムを提供している

#### 30.1.4. Session Hijacking

セッションハイジャック。CookieやセッションIDからログイン情報などを盗まれる。急に異なるIPアドレスからのリクエストを察知する必要あり。

#### 30.1.5. Directory Traversal

ディレクトリ・トラバーサル。WEBで公開されてないディレクトリに侵入し、WEBサーバー自体のログイン情報を盗む。リクエストに対するURLのチェックが必要。Traversal とは横切る、横断するの意味。

#### 30.1.6. XSS (Cross Site Scripting)

攻撃者がリンクを用意。これを踏むとクライアントサイドスクリプトが実行され、cookieやセッションIDが盗まれたり、ウィルスがダウンロードされたりする。

#### 30.1.7. CSRF (Cross Site Request Forgeries)

通称、シーサーフともいう。XSSと同じだが、目的はなりすましログインである。Forgery とは偽造や捏造の意味。

#### 30.1.8. SQL Injection

DBサーバーに送るクエリに悪意あるクエリを混ぜる。

### 30.2. Security Policies

様々なポリシーがある。

#### 30.2.1. Same-Origin Policy

Web セキュリティの重要なポリシーの一つに、Same-Origin Policy (同一オリジンポリシー)があります。これは、オリジン間のリソース共有に制限をかけるもので、上述のXSSやCSRFのような脆弱性を防ぐことを目的としたものです。

#### 30.2.2. CORS (Cross-Origin Resource Sharing)

読み方: コルス or シーオーアールエス。「オリジン間リソース共有」。オリジンとは、例えば、<https://yahoo.co.jp/> のようなドメインに、プロトコルとポート番号がついたもののこと（URLとだいたい同じ）。CORS とは、あるオリジンで動いている Web アプリケーションに対して、別のオリジンのサーバーへのアクセスをオリジン間 HTTP リクエストによって許可できる仕組みのこと

<https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS>
<https://qiita.com/att55/items/2154a8aad8bf1409db2b>
<https://zenn.dev/kkeeth/scraps/dd30ae9d48f092>

### 30.3. WAF (Web Application Firewall)

ファイアウォール。一般的に高機能だが高い。後述するIDSやIPSは中身をチェックするわけではないので、一見正常に見える攻撃は防げない。そこでWAFが必要になる。

- ブラックリスト型
- ホワイトリスト型

### 30.4. 不正アクセスを防ぐ仕組み

ファイアウォールで防ぎきれない攻撃を防ぐ手段としてIDSとIPSがある。通信を監視するネットワーク型とサーバー上のユーザーの動きを監視するホスト型がある。ネットワーク型だと、

- IDS：　Intrusion Detection System。不正アクセスを検知したら、管理者に通知するだけ
- IPS：　Intrusion Prevention System。上に加えて遮断もする

不正アクセスの検知方法は2種類あり

- Signature型（不正検知型）：　データベースに登録された既知の攻撃と照らし合わせる。SYN flood攻撃などを特定できる
- Anomaly型（異常検知型）：　通常を定義して外れる異常なものを検知する。F5攻撃を特定できる

### 30.5. PKA (Public Key Authentication)

公開鍵証明書。WEBの世界の身分証明書。

- SSL証明書：　認証局が発行する。発行費や時間がかかる
- オレオレ証明書：　自己証明書。自らが発行するため費用や時間はかからないが、暗号化通信は可能。ブラウザ側で警告が出る

### 30.6. Authentication

認証。本人確認処理のこと。元々は各サイトで実装していたが、GoogleやFacebookなどが開発した認証を使うようになってきた。

- 認証API方式：　Googleなど各社が提供するAPIに個別に合わせる方法
- OPEN ID方式：　個別の認証処理を標準化したプロトコル。同じ手順で複数の認証処理が使える

#### 30.6.1. Open ID

Open IDの処理は下記

1. ユーザーが、Open IDアカウント（Googleなど）の選択
2. WEBアプリが、アカウントを持つサイトを検索し暗号鍵を交換
3. WEBアプリからユーザーにOpen IDへのログイン指示
4. ユーザーがログイン
5. Open IDサイトからWEBアプリへ認証完了通知
6. WEBアプリからユーザーにログイン成功を通知

<https://qiita.com/kaysquare1231/items/c4e4736f2a924b03777b>

### 30.7. Authorization

認可。サービスをまたいだ機能の利用時に必要。

<https://qiita.com/kaysquare1231/items/c4e4736f2a924b03777b>

#### 30.7.1. OAuth (Open Authorization)

オーオースと読む。（オースじゃないよ）

サイトを跨いだ認可を実現するために標準化されたプロトコル。認可のみで認証は行わない。利用したいサービスをリソース、サービスを提供するサーバーはリソースサーバー、ユーザーをリソースオーナー、認可を受けてリソースを使うアプリなどをクライアントと言う。リソースの使用時は合言葉（トークン）を使う。

#### 30.7.2. Open ID Connect

OAuth2.0をベースに認証機能を追加したプロトコル。

#### 30.7.3. JWT (JSON Web Tokens)

JSON Web Token (JWT) はオープンスタンダード (RFC 7519) で、当事者間で情報を JSON オブジェクトとして安全に送信するための、コンパクトで自己完結的な方法のこと。このやりとりされる情報は、デジタル署名されているため、検証および信頼することができます。JWTは、秘密鍵（HMAC アルゴリズムを使用）、またはRSAやECDSAを使用した公開鍵/秘密鍵ペアを用いて署名することができます。

ユーザーがログインすると、それ以降の各リクエストにJWTが含まれるようになり、そのトークンで許可されたルート、サービス、リソースにアクセスできるようになります。シングル・サインオンは、オーバーヘッドが小さく、異なるドメイン間で簡単に使用できることから、現在では広くJWTが使用されている機能です。

あまり深堀りしません。。セキュリティは事前に学習するにしては、どうしても意識が高まりにくいですね。

<https://jwt.io/introduction>
<https://qiita.com/Naoto9282/items/8427918564400968bd2b>

#### 30.7.4. Auth0

クラウドにもオンプレミスでも、あらゆるアプリ、APIに柔軟に対応可能な次世代型の認証基盤サービスです。世界での導入実績は10,000社を越え、毎月40億回以上のセキュアなログインを支えています。Auth0, Inc. が開発。

Auth0 Inc.は2013年に米国Microsoftに在籍していたメンバーを中心に創業した会社で、Washington州Bellevueに本社があります。創業メンバーはEugenio Pace(CEO), Matias Woloski(CTO)　などMicrosoftに在籍していたメンバーのほか、Node.jsの認証フレームワークである"Passport"の開発者であった Jered Hanson, AT&T, Amazon.com, 国防総省での勤務経験のある Eugen Koganも創業メンバーです。

![Auth0のイメージ](2021-09-28-14-48-02.png)

<https://auth0.com/>
<https://classmethod.jp/partner/auth0/>
<https://qiita.com/furuth/items/68c3caa3127cbf4f6b77>

### 30.8. Pen Test (Penetration Testing)

ペネトレーションテスト、脆弱性診断。ツールやセキュリティ企業への依頼など方法がある。ECサイト構築時などは必ずこれをやって、クライアントに提出してる場合も多いです（しかし、その中身はまた往々にして見られておらず、結果がOKだったかどうかしか興味を持たれない印象）

### 30.9. Pen Test Tools

以下、簡単にツールを紹介しておく。（まったく使ったことはありませんが）特に知識がないので、詳しい方いらっしゃったらコメント下さい。

<https://www.csoonline.com/article/2943524/11-penetration-testing-tools-the-pros-use.html>

#### 30.9.1. Kali Linux

ペンテスト用のLinux OS。Debianベース。以前はBackTrack Linuxとして知られ、Offensive Security（OSCP認証を運営しているOffSec）の優秀な人々によって維持されていたKaliは、ペネトレーション・テスターとして攻撃的に使用するためにあらゆる面で最適化されています。<https://www.kali.org/>

#### 30.9.2. NMAP (Network Mapper)

ポートスキャナの祖先。1997年登場。どのポートが開いているのか？そのポートでは何が動いているのか？これは、ペンテスターが偵察を行う際に必要不可欠な情報であり、nmapはしばしばその作業に最適なツール。開発言語は、C, C++, Python, Lua。<https://en.wikipedia.org/wiki/Nmap>

#### 30.9.3. Metasploit

ペネトレーションテストやIDSのシグネチャ開発を支援するプロジェクト。マサチューセッツ州ボストンを拠点とするセキュリティ企業Rapid7社が所有。

最もよく知られているサブプロジェクトは、オープンソースのMetasploit Frameworkであり、リモートのターゲットマシンに対してエクスプロイトコードを開発・実行するためのツールである。開発言語は、Ruby。<https://en.wikipedia.org/wiki/Metasploit_Project>

#### 30.9.4. Wireshark

Wiresharkは、ネットワークを通過するトラフィックを理解するためのユビキタスなツールです。一般的には日常のTCP/IP接続の問題を掘り下げるために使用されますが、Wiresharkは数百ものプロトコルの解析をサポートしており、それらのプロトコルの多くでリアルタイム解析と復号化をサポートしています。開発言語は、C, C++。<https://en.wikipedia.org/wiki/Wireshark>

#### 30.9.5. Burp Suite

Web脆弱性スキャナのBurp Suiteを抜きにして、ペンテストツールを語ることはできません。Burp Suiteは、これまでに紹介した他のツールとは異なり、フリーではなく、プロが使用する高価なツールです。Burp Suiteにはコミュニティ版があるものの、機能の多くを欠いており、Burp Suiteエンタープライズ版は年間3,999ドル。

テストしたいウェブのプロパティに向けて、準備ができたら発射する。Burpの競合製品であるNessusも、同様に効果的な製品を提供している（価格も同程度）。

<https://portswigger.net/burp>

#### 30.9.6. OWASP ZAP (Zed Attack Proxy)

ZAPはブラウザとテスト対象のウェブサイトの間に設置され、トラフィックをインターセプト（別名man in the middle）して検査や修正を行うことができます。

ZAPは、Burpの機能の多くを備えていませんが、オープンソースのライセンスを採用しているため、大規模な導入が容易かつ安価に行えます。また、ウェブトラフィックがいかに脆弱であるかを学ぶための初心者向けツールとしても最適です。ZAPの競合であるNiktoも同様のオープンソースツールを提供しています。開発言語は、Java。

<https://en.wikipedia.org/wiki/OWASP_ZAP>

## 31. Log運用

ログは重要。ログを制する者がバグを制す。そのログにも種類がある。

- System Logs
- Application Logs
- Access Logs
- Garbage Collector Logs

など。その運用の仕方も色々考えるべきルールあり。

- ログローテーション：　ログファイルの切り替え間隔など
- アクセスログ解析：　ApacheLogViewerやVisitorsなどのソフトもある

## 32. Performance

指標は色々。非常に重要、むしろかなり重要なんですが、軽く。

- 応答時間：　リクエスト送信から何らかのHTTPレスポンスが帰ってくる時間
- 表示完了時間：　リクエスト送信からページ表示完了時間までの時間
- ページ読み込み時間：　ページの読み込み開始から完了までの時間
- 可用性：　エラーなくWEBサイトにアクセスできた確率

### 32.1. Performance 計測ツール

#### 32.1.1. Google Lighthouse

Webページの品質を測定するためのオープンソースの自動化ツール。

公開されているかどうかに関わらず、認証を必要とするあらゆるウェブページに対して実行することができます。Webページのパフォーマンス、アクセシビリティ、検索エンジン最適化を監査します。

<https://developers.google.com/web/tools/lighthouse>

## 33. Payment

決済系のツールは直接開発せずに、外部サービスとのAPI連携も視野に入れたいところ。特に新規事業ではここを頑張って内製化するよりも、本業のUIやロジックを磨いた方がいいはず。

### 33.1. Payment Services

色々なオンライン決済ツールのタイプがあります。

- クレジットカード決済
- 電子マネー決済：　Suicaとか
- QRコード決済：　PayPayとか
- キャリア決済：　ソフトバンクとか
- ネットバンキング決済：　みずほダイレクトとか
- 後払い決済：　Net Protections とか
- コンビニ決済：　セブンとか

<https://www.alpha-note.co.jp/cashless/weblink/weblink-type>

#### 33.1.1. Stripe

今もっとも注目の決済ツールだと思います。決済ごとに3.6％の手数料。

ちなみに、Stripe 社は、アイルランド系アメリカ人の金融サービス企業で、米国のサンフランシスコとアイルランドのダブリンに本社を置く。2009年創業と若い会社だが、既に2020年の売上は74億ドル、従業員数も4,000人以上と大企業です。2010年YCombinator卒業。VCだと、Sequoia Capital、Founders Fund、Tiger Global Management、エンジェルだと Peter Thiel や Elon Musk など名だたる投資家が投資している。2022年にIPOも噂される。利用者は、日本だと SmartHR や freee、海外でも Slack や Zoom などが利用しているとされる（HPに載ってます）。

<https://stripe.com/jp>
<https://en.wikipedia.org/wiki/Stripe_(company)>
<https://www.bloomberg.com/news/articles/2021-09-10/stripe-is-said-to-discuss-public-listing-with-bankers-for-2022>

#### 33.1.2. Square

カリフォルニア州サンフランシスコに本社を構えるモバイル決済企業。2009年にジャック・ドーシーとジム・マッケルヴィが設立し、最初のアプリケーションとサービスがスタートしたのは2010年。実は上述のStripeと同じころなんですね。もっと古いイメージがありました。ジャック・ドーシーはTwitterの生みの親である。

対応しているクレジットカードブランドは、Visa、Mastercard、American Express、JCB、Diners Club、Discoverの六種類です。入会金や月額利用料は無料で、決済ごとに3.6％の手数料でStripeと同じ。

#### 33.1.3. PayPal

決済サービスを提供するアメリカの企業。決済手数料は、国内は1件あたり3.6%＋40円、海外は4.1%＋40円、と少しややこしい。（公式サイト内もぱっとみ分かりにくかったです）上述の2社よりも、少し高いようです。

190の国と地域で利用でき、21通貨以上に対応。2011年2月現在、世界中で2億2000万のアカウントが開設されている。 金銭の授受をPayPalが仲介するため、取引先にクレジットカード番号や口座番号を知らせる必要がなく、安全なサービスであると謳われている。

1998年創業で、創業者は、Stripeにも投資している、Peter Thiel や Elon Musk。2002年にeBayに買収されその子会社となっていたが、2015年7月にPayPal Holdings Inc.の社名で独立した。

<https://www.paypal.com/jp/webapps/mpp/home>
<https://ja.wikipedia.org/wiki/PayPal>
<https://wise.com/jp/blog/paypal-all-fees>

## 34. まとめ

自分や仲間用にまとめていたら、たいそうなボリュームになってしまいました。ここまで読んで、すべて知っていた人もなかなか少ないのではないでしょうか？私は正直、ほとんど知りませんでした。

各分野に精通した方にとっては、それぞれの該当箇所は本当に表面しか書いてないと感じると思います。実際、これだけで「分かった」とは言えず、興味ある分野はどんどんインプット・アウトプットをしていってもらいたいです。参考URLや参考図書を読んだり、友人や仕事仲間と話題にしてみたり、社内や社外でライトニングトークや場を用意してみてもいいかもしれません。この記事を読んで、WEBアプリケーションに関わる方にとって、この分野の果てしない広さに触れ、興味のとっかかりになれば幸いです。

少しでもお役に立てたのであれば、スターやLGTM、またはご指摘やご声援をお待ちしております。励みになります。
