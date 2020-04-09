---
title: Como definir o que é nativo de nuvem
description: Conheça os pilares fundamentais que fornecem a base para sistemas nativos em nuvem
author: robvet
ms.date: 08/20/2019
ms.openlocfilehash: 756a2565bd77fcef19a5f15579987836ff0e75a4
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989084"
---
# <a name="defining-cloud-native"></a>Definindo nuvem nativa

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Pare o que está fazendo e mande sms para dez de seus colegas. Peça-lhes para definir o termo "Cloud Native". Boa chance de você ter oito respostas diferentes.

Nativo da nuvem é tudo sobre mudar a maneira como pensamos sobre a construção de sistemas de negócios críticos.

Os sistemas nativos da nuvem são projetados para abraçar mudanças rápidas, em grande escala e resiliência.

A Cloud Native Computing Foundation fornece uma [definição oficial:](https://github.com/cncf/foundation/blob/master/charter.md)

> *As tecnologias nativas da nuvem capacitam as organizações a construir e executar aplicativos escaláveis em ambientes modernos e dinâmicos, como nuvens públicas, privadas e híbridas. Contêineres, linhas de serviço, microsserviços, infra-estrutura imutável e APIs declarativas exemplificam essa abordagem.*

> *Essas técnicas permitem sistemas acoplados vagamente resistentes, gerenciáveis e observáveis. Combinados com automação robusta, eles permitem que os engenheiros façam mudanças de alto impacto com freqüência e previsíveis com labuta mínima.*

Os aplicativos têm se tornado cada vez mais complexos, com os usuários exigindo cada vez mais. Os usuários esperam resposta rápida, recursos inovadores e zero tempo de inatividade. Problemas de desempenho, erros recorrentes e a incapacidade de se mover rapidamente não são mais aceitáveis. Eles se mudarão facilmente para o seu concorrente.

Nativo da nuvem é muito sobre *velocidade* e *agilidade.* Os sistemas de negócios estão evoluindo de permitir capacidades de negócios para armas de transformação estratégica, acelerando a velocidade e o crescimento dos negócios. É imperativo que as ideias se coloquem no mercado imediatamente.

Aqui estão algumas empresas que implementaram essas técnicas. Pense na velocidade, agilidade e escalabilidade que eles alcançaram.

| Empresa | Experiência |
| :-------- | :-------- |
| [Netflix](https://www.infoq.com/news/2013/06/netflix/) | Possui mais de 600 serviços em produção. Implanta cem vezes por dia. |
| [Uber](https://eng.uber.com/micro-deploy/) | Tem mais de 1.000 serviços armazenados em produção. Implanta milhares de construções a cada semana. |
| [WeChat](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf) | Tem mais de 300 serviços em produção. Faz quase 1.000 mudanças por dia. |

Como você pode ver, Netflix, Uber e WeChat expõem sistemas que consistem em centenas de microsserviços independentes. Esse estilo arquitetônico permite que eles respondam rapidamente às condições do mercado. Eles podem atualizar instantaneamente pequenas áreas de uma aplicação ao vivo e complexa e dimensionar individualmente essas áreas conforme necessário.

A velocidade e a agilidade dos nativos da nuvem surgem de uma série de fatores. O mais importante é a infraestrutura em nuvem. Cinco pilares fundamentais adicionais mostrados na Figura 1-3 também fornecem a base para sistemas nativos da nuvem.

![Pilares fundamentais nativos da nuvem](./media/cloud-native-foundational-pillars.png)

**Figura 1-3**. Pilares fundamentais nativos da nuvem

Vamos dar um tempo para entender melhor o significado de cada pilar.

## <a name="the-cloud"></a>A nuvem...

Os sistemas nativos em nuvem aproveitam ao máximo o modelo de serviço em nuvem.

Projetados para prosperar em um ambiente de nuvem dinâmico e virtualizado, esses sistemas fazem uso extensivo da infra-estrutura de computação [platform as a Service (PaaS)](https://azure.microsoft.com/overview/what-is-paas/) e serviços gerenciados. Eles tratam a infra-estrutura subjacente como *descartável* - provisionada em minutos e redimensionada, dimensionada, movida ou destruída sob demanda - via automação.

Considere o conceito de DevOps amplamente aceito de [Pets vs. Cattle](https://medium.com/@Joachim8675309/devops-concepts-pets-vs-cattle-2380b5aab313). Em um data center tradicional, os servidores são tratados como *Pets*: uma máquina física, com um nome significativo e cuidado. Você dimensiona adicionando mais recursos à mesma máquina (dimensionamento). Se o servidor ficar doente, você cuida dele de volta à saúde. Caso o servidor fique indisponível, todos nota.

O modelo de serviço *do Gado* é diferente. Você provisiona cada instância como uma máquina virtual ou recipiente. Eles são idênticos e atribuíram um identificador de sistema como Serviço-01, Serviço-02, e assim por diante. Você dimensiona criando mais deles (dimensionamento). Quando alguém fica indisponível, ninguém nota.

O modelo de gado abrange *infraestrutura imutável.* Os servidores não são reparados ou modificados. Se alguém falhar ou precisar de atualização, ele é destruído e um novo é provisionado – tudo feito via automação.

Os sistemas nativos em nuvem adotam o modelo de serviço cattle. Eles continuam a funcionar à medida que a infra-estrutura entra ou sai sem levar em conta as máquinas sobre as quais estão executando.

A plataforma em nuvem Do Zure suporta esse tipo de infra-estrutura altamente elástica com recursos automáticos de dimensionamento, auto-recuperação e monitoramento.

## <a name="modern-design"></a>Design moderno

Como você projetaria um aplicativo nativo da nuvem? Como seria sua arquitetura? A quais princípios, padrões e melhores práticas você adere? Que infraestrutura e preocupações operacionais seriam importantes?

### <a name="the-twelve-factor-application"></a>A aplicação de doze fatores

Uma metodologia amplamente aceita para a construção de aplicativos baseados em nuvem é a [Aplicação de Doze Fatores](https://12factor.net/). Descreve um conjunto de princípios e práticas que os desenvolvedores seguem para construir aplicativos otimizados para ambientes modernos em nuvem. Atenção especial é dada à portabilidade entre ambientes e automação declarativa.

Embora aplicável a qualquer aplicativo baseado na Web, muitos profissionais o consideram uma base sólida para a construção de aplicativos nativos da nuvem. Sistemas construídos sobre esses princípios podem implantar e escalar rapidamente e adicionar recursos para reagir rapidamente às mudanças de mercado.

A tabela a seguir destaca a metodologia Doze Fatores:

|    |  Fator | Explicação  |
| :-------- | :-------- | :-------- |
| 1 | Base de Código | Uma única base de código para cada microserviço, armazenada em seu próprio repositório. Rastreado com controle de versão, ele pode ser implantado em vários ambientes (QA, Staging, Production). |
| 2 | Dependências | Cada microserviço isola e embala suas próprias dependências, abraçando mudanças sem impactar todo o sistema. |
| 3 | Configurações  | As informações de configuração são movidas para fora do microserviço e externalizadas através de uma ferramenta de gerenciamento de configuração fora do código. A mesma implantação pode se propagar entre ambientes com a configuração correta aplicada.  |
| 4 | Serviços de apoio | Os recursos auxiliares (armazenamentos de dados, caches, corretores de mensagens) devem ser expostos por meio de uma URL endereçada. Ao fazer isso, desvincula o recurso do aplicativo, permitindo que ele seja intercambiável.  |
| 5 | Construir, liberar, executar | Cada liberação deve impor uma separação rigorosa em toda a construção, liberação e execução de estágios. Cada um deve ser marcado com um ID único e suportar a capacidade de reverter. Os modernos sistemas CI/CD ajudam a cumprir esse princípio. |
| 6 | Processos | Cada microserviço deve ser executado em seu próprio processo, isolado de outros serviços em execução. Externalize o estado necessário para um serviço de backup, como um cache distribuído ou um armazenamento de dados. |
| 7 | Vinculação da porta | Cada microserviço deve ser autônomo com suas interfaces e funcionalidades expostas em sua própria porta. Isso proporciona isolamento de outros microserviços. |
| 8 | Simultaneidade | Os serviços são dimensionados através de um grande número de pequenos processos idênticos (cópias) em vez de dimensionar uma única instância grande na máquina mais poderosa disponível. |
| 9 | Descartável | As instâncias de serviço devem ser descartáveis, favorecendo startups rápidas para aumentar as oportunidades de escalabilidade e desligamentos graciosos para deixar o sistema em um estado correto. Os contêineres Docker, juntamente com um orquestrador, satisfazem inerentemente esse requisito. |
| 10 | Paridade de dev/Prod | Mantenha os ambientes em todo o ciclo de vida do aplicativo o mais semelhantepossível, evitando atalhos caros. Aqui, a adoção de contêineres pode contribuir muito promovendo o mesmo ambiente de execução. |
| 11 | Registro em log | Trate os registros gerados por microsserviços como fluxos de eventos. Processe-os com um agregador de eventos e propague os dados para ferramentas de gerenciamento de mineração/log de dados, como o Azure Monitor ou o Splunk e, eventualmente, arquivamento de longo prazo. |
| 12 | Processos de admin | Execute tarefas administrativas/gerenciais como processos pontuais. As tarefas podem incluir limpeza de dados e análises de puxar para um relatório. As ferramentas que executam essas tarefas devem ser invocadas do ambiente de produção, mas separadamente do aplicativo. |

No livro, [Beyond the Twelve-Factor App](https://content.pivotal.io/blog/beyond-the-twelve-factor-app), o autor Kevin Hoffman detalha cada um dos 12 fatores originais (escrito em 2011). Além disso, o livro fornece três fatores adicionais que refletem o design moderno de aplicativos em nuvem.

|    |  Novo Fator | Explicação  |
| :-------- | :-------- | :-------- |
| 13 | API First | Faça de tudo um serviço. Presuma que seu código será consumido por um cliente front-end, gateway ou outro serviço. |
| 14 | Telemetria | Em uma estação de trabalho, você tem uma visibilidade profunda em sua aplicação e seu comportamento. Na nuvem, você não. Certifique-se de que seu projeto inclua a coleta de dados de monitoramento, específicos de domínio e saúde/sistema. |
| 15 | Autenticação/Autorização  | Implementar identidade desde o início. Considere os recursos [RBAC (controle de acesso baseado em função)](https://docs.microsoft.com/azure/role-based-access-control/overview) disponíveis em nuvens públicas.  |

Vamos nos referir a muitos dos mais de 12 fatores neste capítulo e ao longo do livro.

### <a name="critical-design-considerations"></a>Considerações críticas sobre design

Além da orientação fornecida a partir da metodologia de doze fatores, existem várias decisões críticas de design que você deve tomar ao construir sistemas distribuídos.

*Comunicação*

Como os aplicativos front-end do cliente se comunicarão com serviços de núcleo de backup? Você permitirá comunicação direta? Ou, você pode abstrair os serviços back-end com uma fachada de gateway que fornece flexibilidade, controle e segurança?

Como os serviços de núcleo back-end se comunicarão entre si? Você permitirá chamadas HTTP diretas que levam ao acoplamento e impacto no desempenho e agilidade? Ou você pode considerar mensagens dissociadas com tecnologias de fila e tópicos?

A comunicação é coberta em detalhes Capítulo 4, *Padrões de comunicação nativos da nuvem*.

*Resiliência*

Uma arquitetura de microsserviços move seu sistema de comunicação em processo para comunicação de rede. Em um ambiente distribuído, o que você fará quando o Serviço B não estiver respondendo a uma chamada do Serviço A? O que acontece quando o Serviço C se torna temporariamente indisponível e outros serviços chamando-o de pilha e degradando o desempenho do sistema?

A resiliência é abordada em detalhes Capítulo 6, *Resiliência Nativa da Nuvem*.

*Dados distribuídos*

Por design, cada microserviço encapsula seus próprios dados, expondo as operações através de sua interface pública. Se assim for, como você consulta dados ou implementa uma transação em vários serviços?

Os dados distribuídos são cobertos em detalhes Capítulo 5, *Padrões de dados nativos da nuvem*.

*Identidade*

Como seu serviço identificará quem está acessando e quais permissões eles têm?

A identidade é coberta em detalhes Capítulo 8, *Identidade*.

## <a name="microservices"></a>Microsserviços

Sistemas nativos em nuvem adotam microsserviços, um estilo arquitetônico popular para a construção de aplicações modernas.

Construídos como um conjunto distribuído de pequenos serviços independentes que interagem através de um tecido compartilhado, os microserviços compartilham as seguintes características:

- Cada um implementa uma capacidade de negócios específica dentro de um contexto de domínio maior.

- Cada um é desenvolvido de forma autônoma e pode ser implantado de forma independente.

- Cada um é auto-contido encapsulando sua própria tecnologia de armazenamento de dados (SQL, NoSQL) e plataforma de programação.

- Cada um é executado em seu próprio processo e se comunica com outros usando protocolos de comunicação padrão como HTTP/HTTPS, WebSockets ou [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).

- Eles compõem juntos para formar uma candidatura.

A Figura 1-4 contrasta uma abordagem de aplicação monolítica com uma abordagem de microsserviços. Observe como o monólito é composto de uma arquitetura em camadas, que é executada em um único processo. Normalmente consome um banco de dados relacional. A abordagem do microserviço, no entanto, segrega a funcionalidade em serviços independentes que incluem lógica e dados. Cada microserviço hospeda seu próprio datastore.

![Implantação monolítica versus microsserviços](./media/monolithic-vs-microservices.png)

**Figura 1-4.** Implantação monolítica versus microsserviços

Observe como os microserviços promovem o princípio "One Codebase, One Application" da [Aplicação de Doze Fatores,](https://12factor.net/)discutido anteriormente no capítulo.

> *O \#fator 1 especifica "Uma base de código única para cada microserviço, armazenada em seu próprio repositório. Rastreado com controle de versão, ele pode ser implantado em vários ambientes."*

### <a name="why-microservices"></a>Por que os microsserviços?

Os microserviços proporcionam agilidade.

No início do capítulo, comparamos um aplicativo de comércio eletrônico construído como um monólito com o de microsserviços. No exemplo, vimos alguns benefícios claros:

- Cada microserviço tem um ciclo de vida autônomo e pode evoluir independentemente e implantar com freqüência. Você não precisa esperar por uma versão trimestral para implantar um novo recursos ou atualização. Você pode atualizar uma pequena área de um aplicativo complexo com menos risco de interromper todo o sistema.

- Cada microserviço pode ser dimensionado de forma independente. Em vez de dimensionar todo o aplicativo como uma única unidade, você dimensiona apenas os serviços que requerem mais poder de processamento ou largura de banda de rede. Esta abordagem fina para o dimensionamento proporciona um maior controle do seu sistema e ajuda a reduzir os custos globais à medida que você escala partes do seu sistema, não tudo.

Um excelente guia de referência para a compreensão de microserviços é [o .NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/standard/microservices-architecture/). O livro mergulha profundamente no design e arquitetura de microserviços. É um companheiro para uma [arquitetura de referência de microserviço full-stack](https://github.com/dotnet-architecture/eShopOnContainers) disponível como download gratuito da Microsoft.

### <a name="developing-microservices"></a>Desenvolvimento de microsserviços

Microserviços podem ser criados com qualquer plataforma de desenvolvimento moderna.

A plataforma Microsoft .NET Core é uma excelente escolha. Gratuito e de código aberto, possui muitos recursos incorporados para simplificar o desenvolvimento de microserviços. .NET Core é multiplataforma. Os aplicativos podem ser construídos e executados no Windows, macOS e na maioria dos sabores do Linux.

.NET Core tem um alto desempenho e tem pontuado bem em comparação com node.js e outras plataformas concorrentes. Curiosamente, [o TechEmpower](https://www.techempower.com/) conduziu um extenso conjunto de [benchmarks](https://www.techempower.com/benchmarks/#section=data-r17&hw=ph&test=plaintext) de desempenho em muitas plataformas e frameworks de aplicativos web. .NET Core marcou no top 10 - bem acima do Node.js e outras plataformas concorrentes.

.NET Core é mantido pela Microsoft e pela comunidade .NET no GitHub.

## <a name="containers"></a>Contêineres

Hoje em dia, é natural ouvir o termo *container* mencionado em qualquer conversa sobre *nuvem nativa.* No livro, [Cloud Native Patterns](https://www.manning.com/books/cloud-native-patterns), a autora Cornelia Davis observa que: "Os contêineres são um grande facilitador de software nativo na nuvem". A Cloud Native Computing Foundation coloca a contêinerização de microserviços como o primeiro passo em seu [Mapa de Trilha Nativo da Nuvem](https://raw.githubusercontent.com/cncf/trailmap/master/CNCF_TrailMap_latest.png) - orientação para empresas que iniciam sua jornada nativa na nuvem.

Contêiner um microserviço é simples e simples. O código, suas dependências e tempo de execução são embalados em um binário chamado [imagem de contêiner](https://docs.docker.com/glossary/?term=image). As imagens são armazenadas em um [registro de contêiner,](https://caylent.com/container-registries/)que funciona como um repositório ou biblioteca para imagens. Um registro pode ser localizado em seu computador de desenvolvimento, em seu data center ou em uma nuvem pública. O próprio Docker mantém um registro público via [Docker Hub](https://hub.docker.com/). A nuvem do Azure possui um [registro de contêiner](https://azure.microsoft.com/services/container-registry/) para armazenar imagens de contêineres perto das aplicações em nuvem que as executarão.

Quando necessário, você transforma a imagem em uma instância de contêiner em execução. A instância é executada em qualquer computador que tenha um mecanismo [de tempo de execução](https://kubernetes.io/docs/setup/production-environment/container-runtimes/) de contêiner instalado. Você pode ter quantas instâncias do serviço contêiner necessário.

A Figura 1-5 mostra três microsserviços diferentes, cada um em seu próprio contêiner, rodando em um único host.

![Vários contêineres em execução em um host de contêiner](./media/hosting-mulitple-containers.png)

**Figura 1-5**. Vários contêineres em execução em um host de contêiner

Observe como cada contêiner mantém seu próprio conjunto de dependências e tempo de execução, que podem ser diferentes. Aqui, vemos diferentes versões do microserviço Product sendo executados no mesmo host. Cada contêiner compartilha uma fatia do sistema operacional, memória e processador do host subjacente, mas é isolado um do outro.

Observe o quão bem o modelo de contêiner adota o princípio "Dependências" da [Aplicação de Doze Fatores](https://12factor.net/).

> *O \#fator 2 especifica que "Cada microserviço isola e embala suas próprias dependências, abraçando mudanças sem impactar todo o sistema".*

Os contêineres suportam cargas de trabalho do Linux e do Windows. A nuvem Azure abraça abertamente ambos. Curiosamente, é o Linux, não o Windows Server, que se tornou o sistema operacional mais popular no Azure.

Enquanto vários fornecedores de contêineres existem, Docker capturou a maior parte do mercado. A empresa tem dirigido o movimento de contêineres de software. Tornou-se o padrão de fato para embalagem, implantação e execução de aplicativos nativos da nuvem.

### <a name="why-containers"></a>Por que contêineres?

Os contêineres fornecem portabilidade e garantem consistência entre os ambientes. Ao encapsular tudo em um único pacote, você *isola* o microserviço e suas dependências da infra-estrutura subjacente.

Você pode implantar esse mesmo recipiente em qualquer ambiente que tenha o motor de tempo de execução do Docker. As cargas de trabalho em contêiner também eliminam as despesas de pré-configuração de cada ambiente com frameworks, bibliotecas de software e mecanismos de tempo de execução.

Ao compartilhar o sistema operacional subjacente e os recursos do host, os contêineres têm uma pegada muito menor do que uma máquina virtual completa. O tamanho menor aumenta a *densidade*, ou número de microserviços, que um determinado host pode executar de uma só vez.

### <a name="container-orchestration"></a>Orquestração de contêineres

Enquanto ferramentas como o Docker criam imagens e executam contêineres, você também precisa de ferramentas para gerenciá-las. O gerenciamento de contêineres é feito com um programa especial chamado orquestrador de contêineres. Ao operar em escala, a orquestração de contêineres é essencial.

A Figura 1-6 mostra tarefas de gerenciamento que os orquestradores de contêineres fornecem.

![O que os orquestradores de contêineres fazem](./media/what-container-orchestrators-do.png)

**Figura 1-6**. O que os orquestradores de contêineres fazem

A tabela a seguir descreve tarefas comuns de orquestração.

|  Tarefas | Explicação  |
| :-------- | :-------- |
| Agendamento | Provisão automaticamente as instâncias do contêiner.|
| Afinidade/antiafinidade | Provisão de contêineres próximos ou distantes um do outro, ajudando na disponibilidade e no desempenho. |
| Monitoramento da integridade | Detectar e corrigir automaticamente falhas.|
| Failover | Reprovisionamento automático de instância sem falha em máquinas saudáveis.|
| Scaling | Adicione ou remova automaticamente a instância do contêiner para atender à demanda.|
| Rede | Gerencie uma sobreposição de rede para comunicação de contêineres.|
| Descoberta de Serviços | Habilite que os contêineres se localizem entre si.|
| Atualizações sem interrupção | Coordenar upgrades incrementais com implantação de tempo de inatividade zero. Reverter automaticamente mudanças problemáticas.|

Observe como os orquestradores abraçam os princípios de dissídio e simultâneos da [Aplicação de Doze Fatores,](https://12factor.net/)discutidas anteriormente no capítulo.

> *O \#fator 9 especifica que "As instâncias de serviço devem ser descartáveis, favorecendo startups rápidas para aumentar as oportunidades de escalabilidade e desligamentos graciosos para deixar o sistema em um estado correto. Os contêineres Docker, juntamente com um orquestrador, satisfazem inerentemente essa exigência."*

> *O \#fator 8 especifica que "os serviços são dimensionados em um grande número de pequenos processos idênticos (cópias) em vez de dimensionar uma única instância grande na máquina mais poderosa disponível."*

Embora existam vários orquestradores de contêineres, [kubernetes](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/) tornou-se o padrão de fato para o mundo nativo das nuvens. É uma plataforma portátil, extensível e de código aberto para gerenciar cargas de trabalho em contêineres.

Você poderia hospedar sua própria instância de Kubernetes, mas então você seria responsável pelo provisionamento e gerenciamento de seus recursos - o que pode ser complexo. A nuvem do Azure apresenta o Kubernetes como um serviço gerenciado, [o Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/). Um serviço gerenciado permite que você aproveite totalmente seus recursos, sem ter que instalá-lo e mantê-lo.

O Azure Kubernetes Services é coberto em detalhes Capítulo 2, *Dimensionando aplicativos nativos da nuvem*.

## <a name="backing-services"></a>Serviços de apoio

Os sistemas nativos da nuvem dependem de muitos recursos auxiliares diferentes, como armazenamento de dados, corretores de mensagens, monitoramento e serviços de identidade. Esses serviços são conhecidos como [serviços de apoio.](https://12factor.net/backing-services)

 A Figura 1-7 mostra muitos serviços de apoio comuns que os sistemas nativos da nuvem consomem.

![Serviços comuns de apoio](./media/common-backing-services.png)

**Figura 1-7**. Serviços comuns de apoio

Os serviços de apoio promovem o princípio "Apátrida" da [Aplicação de Doze Fatores,](https://12factor.net/)discutida no início do capítulo.

>*O \#fator 6* especifica que: "Cada microserviço deve ser executado em seu próprio processo, isolado de outros serviços em execução. Externalize o estado necessário para um serviço de backup, como um cache distribuído ou um armazenamento de dados."

Você poderia hospedar seus próprios serviços de apoio, mas então você seria responsável pelo licenciamento, provisionamento e gerenciamento desses recursos.

Os provedores de nuvem oferecem uma rica variedade de serviços de *apoio gerenciados.* Em vez de possuir o serviço, você simplesmente o consome. O provedor opera o recurso em escala e assume a responsabilidade pelo desempenho, segurança e manutenção. Monitoramento, redundância e disponibilidade são incorporados ao serviço. Os provedores suportam totalmente seus serviços gerenciados - abra um ticket e eles corritem seu problema.

Os sistemas nativos em nuvem favorecem serviços de backup gerenciados de fornecedores de nuvem. A economia de tempo e trabalho são ótimas. O risco operacional de hospedar o seu próprio e experimentar problemas pode ficar caro rapidamente.

Uma prática recomendada é tratar um serviço de backup como um *recurso conectado,* dinamicamente vinculado a um microserviço com informações (uma URL e credenciais) armazenadas em uma configuração externa. Essa orientação está explicitada no [Aplicativo de Doze Fatores,](https://12factor.net/)discutido no início do capítulo.

>*O \#fator 4* especifica que os serviços de backup "devem ser expostos através de uma URL endereçada. Ao fazer isso, desvincula o recurso do aplicativo, permitindo que ele seja intercambiável."

>*O \#fator 3* especifica que "As informações de configuração são movidas para fora do microserviço e externalizadas através de uma ferramenta de gerenciamento de configuração fora do código."

Com esse padrão, um serviço de backup pode ser anexado e desconectado sem alterações de código. Você pode promover um microserviço de QA para um ambiente de encenação. Você atualiza a configuração de microserviço para apontar os serviços de backup no estágio e injetar as configurações em seu contêiner através de uma variável de ambiente.

Os fornecedores de nuvem fornecem APIs para que você se comunique com seus serviços de apoio proprietários. Essas bibliotecas encapsulam o encanamento e a complexidade. Comunicar-se diretamente com essas APIs acoplará firmemente seu código ao serviço de backup. É uma prática melhor para isolar os detalhes de implementação da API do fornecedor. Introduza uma camada de intermediação ou API intermediária, expondo operações genéricas ao seu código de serviço. Este acoplamento solto permite que você troque um serviço de backup por outro ou mova seu código para uma nuvem pública diferente sem ter que fazer alterações no código de serviço principal.

Os serviços de apoio são discutidos em detalhes Capítulo 5, *Padrões de dados nativos da nuvem*e Capítulo 4, *Padrões de comunicação nativos da nuvem*.

## <a name="automation"></a>Automação

Como você viu, sistemas nativos em nuvem adotam microsserviços, contêineres e design moderno de sistemas para alcançar velocidade e agilidade. Mas isso é só parte da história. Como você provisão os ambientes em nuvem sobre os quais esses sistemas são executados? Como você implanta rapidamente recursos e atualizações de aplicativos? Como você completa o quadro completo?

Insira a prática amplamente aceita de [Infra-estrutura como Código](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), ou IaC.

Com o IaC, você automatiza o provisionamento de plataformas e a implantação de aplicativos. Você essencialmente aplica práticas de engenharia de software, como testes e versionamentos às suas práticas de DevOps. Sua infra-estrutura e implantações são automatizadas, consistentes e repetíveis.

### <a name="automating-infrastructure"></a>Automatizando infra-estrutura

Ferramentas como [o Azure Resource Manager,](https://azure.microsoft.com/documentation/articles/resource-group-overview/)Terraform e a CLI do [Azure](https://docs.microsoft.com/cli/azure/)permitem que você script a infra-estrutura de nuvem que você precisa. Nomes de recursos, locais, capacidades e segredos são parametrizados e dinâmicos. O script é versão e verificado no controle de origem como um artefato do seu projeto. Você invoca o script para prover uma infra-estrutura consistente e repetitiva em ambientes do sistema, como QA, encenação e produção.

Sob o capô, IaC é idempotente, o que significa que você pode executar o mesmo script uma e outra vez sem efeitos colaterais. Se a equipe precisa fazer uma mudança, eles editam e reexecutam o script. Apenas os recursos atualizados são afetados.

No artigo, [What is Infrastructure as Code](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), autor Sam Guckenheimer descreve como: "As equipes que implementam AC podem fornecer ambientes estáveis rapidamente e em escala. As equipes evitam a configuração manual dos ambientes e impõem consistência representando o estado desejado de seus ambientes via código. As implantações de infra-estrutura com IaC são repetíveis e evitam problemas de tempo de execução causados por deriva de configuração ou dependências ausentes. As equipes de DevOps podem trabalhar em conjunto com um conjunto unificado de práticas e ferramentas para fornecer aplicativos e sua infra-estrutura de suporte de forma rápida, confiável e em escala."

### <a name="automating-deployments"></a>Automatizando implantações

O [Aplicativo de Doze Fatores](https://12factor.net/), discutido anteriormente, exige etapas separadas ao transformar o código concluído em um aplicativo em execução.

> *O \#fator 5* especifica que "Cada versão deve impor uma separação rigorosa em toda a construção, liberação e execução de estágios. Cada um deve ser marcado com um ID único e apoiar a capacidade de reverter."

Os modernos sistemas CI/CD ajudam a cumprir esse princípio. Eles fornecem etapas de implantação separadas e ajudam a garantir um código consistente e de qualidade que esteja prontamente disponível para os usuários.

A Figura 1-8 mostra a separação através do processo de implantação.

![Implanta etapas no pipeline CI/CD](./media/build-release-run-pipeline.png)

**Figura 1-8**. Etapas de implantação em um pipeline CI/CD

Na figura anterior, preste especial atenção à separação das tarefas.

O desenvolvedor constrói um recurso em seu ambiente de desenvolvimento, iterando através do que é chamado de "loop interno" de código, execução e depuração. Quando concluído, esse código é *empurrado* para um repositório de código, como GitHub, Azure DevOps ou BitBucket.

O empurrão desencadeia um estágio de construção que transforma o código em um artefato binário. O trabalho é implementado com um gasoduto [de Integração Contínua (CI).](https://martinfowler.com/articles/continuousIntegration.html) Ele constrói, testa e embala automaticamente o aplicativo.

A fase de liberação pega o artefato binário, aplica informações externas de configuração de aplicativos e ambientes e produz uma versão imutável. A liberação é implantada em um ambiente especificado. O trabalho é implementado com um pipeline [de Entrega Contínua (CD).](https://martinfowler.com/bliki/ContinuousDelivery.html) Cada liberação deve ser identificável. Você pode dizer: "Esta implantação está executando a versão 2.1.1 do aplicativo."

Finalmente, o recurso lançado é executado no ambiente de execução de destino. Os lançamentos são imutáveis, o que significa que qualquer alteração deve criar uma nova versão.

Aplicando essas práticas, as organizações evoluíram radicalmente a forma como enviam software. Muitos passaram de lançamentos trimestrais para atualizações sob demanda. O objetivo é pegar problemas no início do ciclo de desenvolvimento quando eles são menos caros para corrigir. Quanto maior a duração entre integrações, mais caros se resolvem os problemas.  Com consistência no processo de integração, as equipes podem cometer mudanças de código com mais freqüência, levando a uma melhor colaboração e qualidade de software.

### <a name="azure-pipelines"></a>Azure Pipelines

A nuvem do Azure inclui um novo serviço de CI/CD intitulado [Azure Pipelines](https://azure.microsoft.com/services/devops/pipelines/), que faz parte da oferta [de DevOps do Azure](https://azure.microsoft.com/services/devops/) mostrada na Figura 1-9.

![Pipelines Azure em DevOps](./media/devops-components.png)

**Figura 1-9**. Ofertas do Azure DevOps

O Azure Pipelines é um serviço em nuvem que combina integração contínua (CI) e entrega contínua (CD). Você pode testar, construir e enviar automaticamente seu código para qualquer alvo.

Você define seu pipeline em código em um arquivo YAML ao lado do resto do código para o seu aplicativo.

- O pipeline é versão com seu código e segue a mesma estrutura de ramificação.
- Você recebe validação de suas alterações através de avaliações de código em solicitações de puxar e políticas de construção de ramificações.
- Cada ramo que você usa pode personalizar a diretiva de compilação modificando o arquivo azure-pipelines.yml.
- O arquivo do pipeline é verificado no controle de versão e pode ser investigado se há algum problema.

O serviço Azure Pipelines suporta a maioria dos provedores de Git e pode gerar pipelines de implantação para aplicativos escritos nas plataformas Linux, macOS ou Windows. Ele inclui suporte para Java, .NET, JavaScript, Python, PHP, Go, XCode e C++.

>[!div class="step-by-step"]
>[Próximo](introduction.md)
>[anterior](candidate-apps.md)
