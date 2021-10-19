# teste

> "Node.js is:
> a JavaScript runtime built on Chrome`s V8 Javascript engine;
> uses an event-driven, asynchronous non-blocking I/O model;
> operates on a single thread event loop."

Genericamente falando, qualquer coisa relacionada a computation é síncrona; E todo processamento relacionado com entrada, saída e tempo é assíncrona.

Bloqueante se refere a operação que só permite que uma nova operação seja iniciada quanto esta seja terminada.

Callback é uma função passada como argumento de outra função, podendo ser chamada de dentro desta outra função para executar alguma ação. A chamada pode síncrona ou assíncrona.

Uma aplicação orientada a eventos responde a ações geradas pelo usuário ou sistema.

## Why Node?

O argumento do criador, Ryan Dahl, é que o padrão de manipulação de entrada e saída na época era de maneira síncrona, o que bloqueava o processo inteiro desnecessariamente. Perdendo a capacidade de ser multi tarefa. Ao invés de utilizar um modelo multi thread, Dahl propôs que cada requisição fosse tratada em uma thread, em um event-loop e com um I/O não bloqueante.

O event-loop é o que permite o Node.js executa operações não bloqueantes de entrada e saída, apesar do JavaScript ser single-thread.The loop, which runs on the same thread as the JavaScript code, grabs a task from the code and executes it. If the task is async or an I/O operation the loop offloads it to the system kernel, like in the case for new connections to the server, or to a thread pool, like file system related operations. The loop then grabs the next task and executes it.

Since most modern kernels are multi-threaded, they can handle multiple operations executing in the background. When one of these operations completes (this is an event), the kernel tells Node.js so that the appropriate callback (the one that depended on the operation completing) may be added to the poll queue to eventually be executed. Node keeps track of unfinished async operations, and the event loop keeps looping to check if they are finished until all of them are.

Dado esse histórico, Node se sai bem em situações onde há um intenso volume de entrada e saídas de informações, exigindo da aplicação velocidade, escalabilidade ao tratar de conexões concorrentes. Exemplos, variam de streaming de música e vídeo, jogos, aplicatiovos em tempo real, ferramentas de colaboração, aplicações de investimento.

Node.js pode não ser a melhor escolha para operações que utilizam intensamente a CPU. Nesse cenário, o modelo tradicional de threads pode perfomar melhor.

## Referências

[Node.js: what it is, when and how to use it, and why you should (FreeCodeCamp)](https://www.freecodecamp.org/news/node-js-what-when-where-why-how-ab8424886e2/)

### Na fila para ler / assistir

[Ryan Dahl - Original Node.js Presentation](https://www.youtube.com/watch?v=ztspvPYybIY)
[Ryan Dahl - 10 things I regret about Node.js](https://www.youtube.com/watch?v=M3BM9TB-8yA)
[Node.js Interview: 4 Questions with Creator Ryan Dahl](https://www.bizjournals.com/boston/inno/stories/news/2011/01/31/nodejs-interview-4-questions-with-creator-ryan.html)
[Documentação do Node.js sobre Event Loop](https://nodejs.org/de/docs/guides/event-loop-timers-and-nexttick/#what-is-the-event-loop)
[Documentação sobre Blocking x Non-Blocking](https://nodejs.org/en/docs/guides/blocking-vs-non-blocking/)
[Node.js About Page](https://nodejs.org/en/about/)
[Node.js Explained](https://www.youtube.com/watch?v=L0pjVcIsU6A)
[What the heck is the event loop anyway?](https://www.youtube.com/watch?v=8aGhZQkoFbQ)
[In the Loop](https://www.youtube.com/watch?v=cCOL7MC4Pl0)
[Everything you need to know about node.js - Event Loop](https://www.youtube.com/watch?v=PNa9OMajw9w)
[A deep dive into libuv](https://www.youtube.com/watch?v=sGTRmPiXD4Y)
[Site dedicado ao Call Back Hell](callbackhell.com)
[Discussão no Stack Overflow sobre Blocking x Non-Blocking](https://stackoverflow.com/questions/10570246/what-is-non-blocking-or-asynchronous-i-o-in-node-js)
[A history of Node.js](https://builtinnode.com/2019/05/04/a-history-of-node-js/)
[O que é o inferno dos callbacls?](https://pt.stackoverflow.com/questions/188656/o-que-%C3%A9-o-inferno-dos-callbacks)
[Anatomy of an HTTP Transaction](https://nodejs.org/en/docs/guides/anatomy-of-an-http-transaction/)
[Debugging Guide](https://nodejs.org/en/docs/guides/debugging-getting-started/)
[asynchronous vs non-blocking](https://stackoverflow.com/questions/2625493/asynchronous-vs-non-blocking)
