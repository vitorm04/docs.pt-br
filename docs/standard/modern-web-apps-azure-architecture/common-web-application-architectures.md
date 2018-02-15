---
title: Arquiteturas de aplicativo da web comuns
description: Projetar aplicativos web modernos com ASP.NET Core e Microsoft Azure | arquiteturas de aplicativo da web comuns
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: dc5580d38ac29a5e923a4b7d84f9d7e077d5cdb2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
#<a name="common-web-application-architectures"></a>Arquiteturas de aplicativo da Web comuns

> "Se você acha que boa arquitetura é cara, tente arquitetura incorreta."  
> _-Brian Rodap e Joseph Yoder_

## <a name="summary"></a>Resumo

Os aplicativos .NET mais tradicionais são implantados como unidades correspondente para um executável ou um único aplicativo web em execução dentro de um appdomain único do IIS. Este é o modelo de implantação mais simples e serve muitos aplicativos internos e menores públicos muito bem. No entanto, mesmo devido a essa unidade única de implantação, mais aplicativos de negócios não trivial se beneficiar de uma separação lógica em várias camadas.

## <a name="what-is-a-monolithic-application"></a>O que é um aplicativo monolítico?

Um aplicativo monolítico é aquele que é totalmente independente, em termos de seu comportamento. Ele pode interagir com outros serviços ou armazenamentos de dados durante a execução de suas operações, mas o núcleo de seu comportamento é executado em seu próprio processo e o aplicativo inteiro normalmente é implantado como uma única unidade. Se precisar de um aplicativo desse tipo seja dimensionada horizontalmente, normalmente o aplicativo inteiro é duplicado em vários servidores ou máquinas virtuais.

## <a name="all-in-one-applications"></a>Aplicativos de tudo em um

O menor número possível de projetos de uma arquitetura de aplicativo é um. Nessa arquitetura, toda a lógica do aplicativo está contida em um único projeto, compilada em um único assembly e implantada como uma única unidade.

Um novo projeto ASP.NET Core, se criados no Visual Studio ou da linha de comando, começa com um simple monolito de "tudo em um". Ele contém todos os do comportamento do aplicativo, incluindo a lógica de apresentação, negócios e dados de acesso. Figura 5-1 mostra a estrutura de arquivos de um único projeto de aplicativo.

**Figura 5-1.** Um único projeto de aplicativo do ASP.NET Core

![](./media/image5-1.png)

Em um cenário de único projeto, a separação de preocupações é obtida com o uso de pastas. O modelo padrão inclui pastas separadas para as responsabilidades de padrão MVC de modelos, modos de exibição e os controladores, bem como pastas adicionais para dados e serviços. Nessa disposição, detalhes de apresentação devem ser limitados tanto quanto possível para a pasta de modos de exibição e detalhes de implementação de acesso de dados devem ser limitados a classes mantidos na pasta de dados. Lógica de negócios deve residir em serviços e classes dentro da pasta de modelos.

Embora simples, a solução de projeto único monolítica apresenta algumas desvantagens. À medida que aumenta de tamanho e a complexidade do projeto, o número de arquivos e pastas continuará crescendo. Questões de interface do usuário (modelos, modos de exibição, controladores) residem em várias pastas, que não sejam agrupadas em ordem alfabética. Esse problema só é pior quando outras construções de nível de interface do usuário, como filtros ou ModelBinders, são adicionadas em suas próprias pastas. Lógica de negócios é espalhada entre as pastas de modelos e serviços, e não há nenhuma indicação clara dos quais classes nas quais pastas depende de quais outros. Esta falta de organização no nível de projeto frequentemente leva a [código espaguete](http://deviq.com/spaghetti-code/).

Para resolver esses problemas, aplicativos geralmente evoluem em soluções multiprojetos, onde cada projeto é considerado a residir em um determinado *camada* do aplicativo.

## <a name="what-are-layers"></a>Quais são as camadas?

Conforme os aplicativos crescem em complexidade, uma maneira de gerenciar essa complexidade é dividir o aplicativo de acordo com suas responsabilidades ou dúvidas. Isso segue a separação do princípio de preocupações e pode ajudar a manter uma base de código crescente organizado de forma que os desenvolvedores podem localizar facilmente onde determinadas funcionalidades é implementada. Arquitetura em camadas oferece inúmeras vantagens além apenas a organização do código, embora.

Organizando código em camadas, a funcionalidade de baixo nível comuns pode ser reutilizada em todo o aplicativo. Essa reutilização é útil porque significa que menos código precisa ser gravada e como ele pode permitir que o aplicativo padronizar em uma única implementação, seguir o princípio seco.

Com uma arquitetura em camadas, aplicativos podem impor restrições nos quais camadas podem se comunicar com outras camadas. Isso ajuda a alcançar o encapsulamento. Quando uma camada é alterada ou substituída, somente as camadas que trabalham com ele devem ser afetadas. Limitando que camadas dependem na qual as outras camadas, o impacto das alterações podem ser reduzidas para que uma única alteração não afeta o aplicativo inteiro.

Camadas (e ao encapsulamento) fazer muito mais fácil substituir a funcionalidade dentro do aplicativo. Por exemplo, um aplicativo inicialmente pode usar seu próprio banco de dados do SQL Server para a persistência, mas posteriormente, pode optar por usar uma estratégia de persistência baseado em nuvem, ou um por trás de uma API da web. Se o aplicativo foi encapsulado corretamente sua implementação de persistência em uma camada de lógica, essa camada específica do SQL Server pode ser substituída por um novo Implementando a mesma interface pública.

O potencial de troca de implementações em resposta a alterações futuras em requisitos, além de camadas de aplicativos podem também tornar mais fácil alternar implementações para fins de teste. Em vez de escrever testes que operam em relação a camada de dados reais ou uma camada de interface do usuário do aplicativo, essas camadas podem ser substituídas em tempo de teste com implementações de falsas que fornecem conhecidas respostas a solicitações. Isso geralmente faz testes muito mais fácil de escrever e muito mais rápido executar quando comparado ao executar testes novamente infraestrutura real do aplicativo.

Disposição lógica é uma técnica comum para melhorar a organização do código em aplicativos de software corporativos, e há várias maneiras em que o código pode ser organizado em camadas.

> [!NOTE]
> *Camadas* representar uma separação lógica dentro do aplicativo. Se a lógica do aplicativo é fisicamente distribuída para separar processos ou servidores, esses destinos de implantação física separada são chamados de *camadas*. É possível e bastante comum, para que um aplicativo de N camadas que é implantado em uma única camada.

## <a name="traditional-n-layer-architecture-applications"></a>Aplicativos tradicionais de arquitetura de "camada N"

A organização mais comuns de lógica de aplicativo em camadas mostrada na Figura 5-2.

**Figura 5-2.** Camadas de aplicativo típico.

![](./media/image5-2.png)

Essas camadas são frequentemente abreviadas como interface de usuário, BLL (camada de lógica de negócios) e a DAL (camada de acesso a dados). Usando essa arquitetura, os usuários fazem solicitações por meio da camada de interface do usuário, que interage com o BLL. BLL, por sua vez, pode chamar a DAL para solicitações de acesso de dados. A camada de interface do usuário não deve fazer todas as solicitações para a DAL diretamente, nem deve interagir com persistência diretamente por outros meios. Da mesma forma, BLL só deve interagir com persistência por meio da DAL. Dessa forma, cada camada tem sua própria responsabilidade bem conhecida.

Uma desvantagem dessa abordagem em camadas tradicional é que as dependências de tempo de compilação é executado da parte superior até a parte inferior. Ou seja, a camada de interface do usuário depende BLL, que depende da DAL. Isso significa que o BLL, que geralmente contém a lógica mais importante no aplicativo, é dependente em detalhes de implementação de acesso de dados (e geralmente a existência de um banco de dados). Testar a lógica de negócios em tal arquitetura pode ser difícil, que requerem um banco de dados de teste. O princípio de inversão de dependência pode ser usado para resolver esse problema, como você verá na próxima seção.

Figura 5-3 mostra uma solução de exemplo, dividir o aplicativo em três projetos responsabilidade (ou camada).

**Figura 5-3.** Um simples aplicativo monolítico com três projetos.

![](./media/image5-3.png)

Embora este aplicativo usa vários projetos para fins de organização, ainda está sendo implantado como uma única unidade e seus clientes irão interagir com ele como um aplicativo web única. Isso permite que o processo de implantação muito simples. Figura 5-4 mostra como esse é um aplicativo pode ser hospedado usando o Windows Azure.

![](./media/image5-4.png)

**Figura 5-4.** Implantação simples do aplicativo Web do Azure

Como o aplicativo precisa crescer, soluções de implantação mais robusta e complexas podem ser necessárias. Figura 5-5 mostra um exemplo de um plano de implantação mais complexo que oferece suporte a recursos adicionais.

![](./media/image5-5.png)

**Figura 5-5.** Implantando um aplicativo web para um serviço de aplicativo do Azure

Internamente, a organização do projeto em vários projetos com base em responsabilidade melhora a facilidade de manutenção do aplicativo.

Essa unidade pode ser dimensionada ou para aproveitar a escalabilidade de sob demanda com base em nuvem. Esse é o processo adicionando adicional da CPU, memória, espaço em disco ou outros recursos para os servidores de hospedagem de seu aplicativo. Expansão significa adicionar mais instâncias desses servidores, sejam esses servidores físicos ou máquinas virtuais. Quando seu aplicativo é hospedado em várias instâncias, um balanceador de carga é usado para atribuir solicitações para instâncias individuais do aplicativo.

A abordagem mais simples para dimensionar um aplicativo web no Azure é configurar manualmente a escala no plano de serviço de aplicativo do aplicativo. Figura 5-6 mostram a tela apropriada do painel do Azure para configurar quantas instâncias estão atendendo a um aplicativo.

![](./media/image5-6.png)

**Figura 5-6.** Plano de serviço de aplicativo escala no Azure.

## <a name="clean-architecture"></a>Arquitetura de limpeza

Aplicativos que siga o princípio de inversão de dependência, bem como os princípios de Design Domain-Driven (DDD) tendem a chegar a uma arquitetura semelhante. Essa arquitetura passou por muitos nomes ao longo dos anos. Um dos nomes era Hexagonal arquitetura, seguido por adaptadores e portas. Mais recentemente, ele é citado como o [transparência arquitetura](http://jeffreypalermo.com/blog/the-onion-architecture-part-1/) ou [arquitetura limpa](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html). É este último nome, arquitetura normal, que é usado como base para descrever a arquitetura deste livro eletrônico.

> [!NOTE]
> O termo que limpa arquitetura pode ser aplicada a aplicativos que são criados usando os princípios de DDD, bem como os que não são criados usando DDD. No caso anterior, essa combinação pode ser chamada como "Arquitetura de DDD limpa".

Arquitetura limpa coloca o modelo de aplicativo e lógica de negócios no centro do aplicativo. Em vez de ter lógica de negócios que dependem de acesso a dados ou outros problemas de infraestrutura, essa dependência é invertida: detalhes de implementação e infraestrutura dependem do núcleo do aplicativo. Isso é feito definindo abstrações ou interfaces no núcleo do aplicativo, em seguida, são implementados por tipos definidos na camada de infraestrutura. Uma maneira comum de visualizar essa arquitetura é usar uma série de círculos concêntricas, semelhantes a uma transparência. Figura 5-X mostra um exemplo desse estilo de arquitetura representação.

![](./media/image5-7.png)

**Figura 5-7.** Arquitetura de limpeza. exibição de transparência

Neste diagrama, as dependências de fluxo para o círculo interno. Assim, você pode ver que o núcleo do aplicativo (que utiliza seu nome de sua posição no núcleo do diagrama) não tem dependências em outras camadas do aplicativo. No centro da parte são as interfaces e as entidades do aplicativo. Fora, mas ainda no núcleo do aplicativo, são serviços de domínio, que normalmente implementam interfaces definidas no círculo interno. Fora do núcleo do aplicativo, a Interface do usuário e as camadas de infraestrutura dependem no núcleo do aplicativo, mas não em si (necessariamente).

Figura 5-X mostra um diagrama de camada horizontal mais tradicional que melhor reflete a dependência entre a interface do usuário e outras camadas.

![](./media/image5-8.png)

**Figura 5-8.** Arquitetura de limpeza. exibição de camada horizontal

Observe que as setas sólidas representam as dependências de tempo de compilação, enquanto a seta tracejada representa uma dependência somente de tempo de execução. Usando a arquitetura de limpeza, a camada de interface do usuário funciona com interfaces definidas no núcleo do aplicativo em tempo de compilação e idealmente não deve ter conhecimento dos tipos de implementação definida na camada de infraestrutura. Em tempo de execução, no entanto, esses tipos de implementação serão necessários para o aplicativo a ser executado, portanto, precisam estar presentes e com fio até as interfaces de núcleo do aplicativo por meio de injeção de dependência.

Figura 5-9 mostra uma exibição mais detalhada da arquitetura de um aplicativo ASP.NET Core quando criado seguindo essas recomendações.

![Arquitetura do ASPNET principal](./media/image5-9.png)

**Figura 5-9.** Diagrama de arquitetura do ASP.NET Core arquitetura limpa a seguir.

Como o núcleo do aplicativo não depender de infraestrutura, é muito fácil de escrever testes de unidade automatizados para essa camada. Números de 5 a 10 e 11 5 mostram como testes se encaixam nesta arquitetura.

![UnitTestCore](./media/image5-10.png)

**Figura 5-10.** Testes de unidade principal do aplicativo em isolamento.

![IntegrationTests](./media/image5-11.png)

**Figura 5-11.** Teste de integração, implementações de infraestrutura com dependências externas.

Como a camada de interface do usuário não tem nenhuma dependência direta em tipos definidos no projeto de infra-estrutura, da mesma forma é muito fácil alternar implementações, para facilitar o teste ou em resposta a alterações de requisitos de aplicativo. Uso interno do ASP.NET Core e o suporte para injeção de dependência torna essa arquitetura a maneira mais apropriada para aplicativos monolítico incomum de estrutura.

Para aplicativos monolíticos os projetos de aplicativo principal, infraestrutura e Interface do usuário são todos executados como um único aplicativo. A arquitetura de tempo de execução do aplicativo poderia ser algo como a Figura 5-12.

![Arquitetura de núcleo ASPNET 2](./media/image5-12.png)

**Figura 5-12.** Arquitetura de tempo de execução de um aplicativo ASP.NET Core do exemplo.

### <a name="organizing-code-in-clean-architecture"></a>Organização de código em arquitetura de limpeza

Em uma solução de arquitetura limpa, cada projeto tem responsabilidades claras. Como tal, determinados tipos pertencerão em cada projeto e com frequência, você encontrará pastas correspondentes a esses tipos de projeto apropriado.

O núcleo do aplicativo contém o modelo de negócios, que inclui entidades, serviços e interfaces. Essas interfaces incluem abstrações para operações que serão executadas usando a infraestrutura, como acesso a dados, acesso de sistema de arquivos, chamadas de rede, etc. Às vezes, serviços ou interfaces definidas nesta camada precisará trabalhar com tipos de entidade não que não têm dependências em infraestrutura ou de interface do usuário. Eles podem ser definidos como objetos de transferência de dados simples (DTOs).

> ### <a name="application-core-types"></a>Tipos de núcleo do aplicativo
> -   Entidades (classes de modelo comercial que persistem)
> -   Interfaces
> -   Serviços
> -   DTOs

O projeto de infra-estrutura normalmente inclui implementações de acesso de dados. Um aplicativo web ASP.NET Core típico, isso incluirá DbContext Entity Framework, quaisquer migrações de núcleo de EF que foram definidas e classes de implementação de acesso de dados. A maneira mais comum de abstrair o código de implementação de acesso de dados é através do uso do [padrão de design do repositório](http://deviq.com/repository-pattern/).

Além das implementações de acesso de dados, o projeto de infra-estrutura deve conter implementações de serviços devem interagir com as questões de infraestrutura. Esses serviços devem implementar interfaces definidas no núcleo do aplicativo e então infraestrutura deve ter uma referência ao projeto de aplicativo principal.

> ### <a name="infrastructure-types"></a>Tipos de infraestrutura
> -   Tipos de núcleo EF (DbContext, migrações)
> -   Tipos de implementação de acesso de dados (repositórios)
> -   Serviços de infraestrutura específicos (FileLogger, SmtpNotifier, etc.)

A camada de interface do usuário em um aplicativo MVC do ASP.NET Core será o ponto de entrada para o aplicativo e será um projeto MVC do ASP.NET Core. Este projeto deve fazer referência do projeto de aplicativo principal e seus tipos devem interagir com a infraestrutura estritamente por meio de interfaces definidas no núcleo do aplicativo. Nenhum instanciação direta de (ou estáticas chamadas para) tipos de camada de infraestrutura devem ser permitidos na camada de interface do usuário.

> ### <a name="ui-layer-types"></a>Tipos de camada de interface do usuário
> -   Controladores
> -   Filtros
> -   Exibições
> -   ViewModels
> -   Inicialização

A classe de inicialização é responsável por configurar o aplicativo e para a conexão dos tipos de implementação para interfaces, permitindo que a injeção de dependência funcionar corretamente em tempo de execução.

> [!NOTE]
> Para conectar a injeção de dependência no ConfigureServices no arquivo Startup.cs do projeto da interface do usuário, o projeto talvez seja necessário para a referência ao projeto de infra-estrutura. Essa dependência pode ser eliminada, mais facilmente usando um contêiner de DI personalizado. Para os fins deste exemplo, a abordagem mais simples é permitir que o projeto de interface do usuário para a referência ao projeto de infra-estrutura.

## <a name="monolithic-applications-and-containers"></a>Contêineres e aplicativos monolíticos 

Você pode criar um único e monolítico implantação baseada em aplicativo ou serviço Web e implantá-lo como um contêiner. Dentro do aplicativo, ele pode não ser monolítico mas organizados em várias bibliotecas, componentes ou camadas. Externamente é um único contêiner como um único processo, o único aplicativo web ou o único serviço.

Para gerenciar esse modelo, você deve implantar um único contêiner para representar o aplicativo. Para dimensionar, basta adicione cópias adicionais com um balanceador de carga na frente. A simplicidade é proveniente do gerenciamento de uma única implantação em um único contêiner ou VM.

![](./media/image5-13.png)

Você pode incluir vários componentes/bibliotecas ou camadas internas dentro de cada contêiner, conforme ilustrado na Figura 5-X. Mas, após a entidade de segurança do contêiner de *"um contêiner executa uma ação e faz isso em um processo*", o monolítico padrão pode ser um conflito.

A desvantagem dessa abordagem é fornecido se/quando o aplicativo cresce, solicitá-la para dimensionar. Se o aplicativo inteiro em escala, não é realmente um problema. No entanto, na maioria dos casos, algumas partes do aplicativo são os pontos de restrição que exigem dimensionamento, enquanto outros componentes são menos usado.

Usando o exemplo de comércio eletrônico típico; o que você provavelmente precisará escalar é o componente de informações do produto. Muitos clientes mais procurem produtos de comprá-las. Mais clientes usam seu carrinho de usar o pipeline de pagamento. Os clientes menos adicionem comentários ou exibam seu histórico de compra. E você provavelmente tem apenas uma série de funcionários, em uma única região, o que precisa para gerenciar o conteúdo e campanhas de marketing. Dimensionando o design monolítico, todo o código é implantado várias vezes.

Além de escala tudo problemas, alterações em um único componente requerem teste completa de todo o aplicativo e uma reimplantação completa de todas as instâncias.

A abordagem monolítica é comum, e muitas organizações estão desenvolvendo com esta abordagem de arquitetura. Muitos estão com bom resultados suficientes, enquanto outros estão atingindo os limites. Muitos criados seus aplicativos nesse modelo, porque as ferramentas e infraestrutura eram muito difíceis criar arquiteturas orientada a serviços (SOA), e eles não veem a necessidade - até que o aplicativo aumentou. Se você achar que está atingindo os limites da abordagem monolítico, dividindo o aplicativo para habilitá-lo aproveitar melhor microservices e contêineres pode ser a próxima etapa lógica.

![](./media/image5-14.png)

Implantando aplicativos monolíticos no Microsoft Azure pode ser obtida usando VMs dedicadas para cada instância. Usando [conjuntos de escala de VM do Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), você pode facilmente dimensionar as VMs. [Serviços de aplicativo do Azure](https://azure.microsoft.com/services/app-service/) pode executar aplicativos monolíticos e expandir facilmente instâncias sem a necessidade de gerenciar as VMs. Serviços de aplicativo do Azure pode executar instâncias únicas de contêineres do Docker, simplificando a implantação. Usando o Docker, você pode implantar uma única VM como um host Docker e executar várias instâncias. Usando o balanceador do Azure, conforme mostrado na Figura 5-14, você pode gerenciar a escala.

A implantação em vários hosts pode ser gerenciada com as técnicas tradicionais de implantação. Os hosts de Docker podem ser gerenciados com comandos como **docker executar** executada manualmente ou através da automação, como os pipelines de entrega contínua (CD).

### <a name="monolithic-application-deployed-as-a-container"></a>Aplicativo monolítico implantado como um contêiner

Há benefícios do uso de contêineres para gerenciar implantações de aplicativo monolítico. Dimensionamento de instâncias de contêineres é muito mais rápido e mais fácil do que a implantação de VMs adicionais. Mesmo ao usar conjuntos de escala de VM para dimensionar VMs, eles levar tempo para a instância. Quando implantado como instâncias de aplicativo, a configuração do aplicativo é gerenciada como parte da VM.

Implantando atualizações como imagens do Docker é muito mais rápida e eficiente de rede. Imagens do docker geralmente iniciam em segundos, acelerando distribuições. Subdividir uma instância de Docker é tão fácil quanto emitir um **stop docker** comando, normalmente Concluindo em menos de um segundo.

Como contêineres são inerentemente imutáveis por design, você nunca precisa se preocupar sobre VMs corrompidas, enquanto os scripts de atualização podem esquecer de conta para alguma configuração específica ou o restante do arquivo no disco.

Enquanto monolíticos aplicativos podem se beneficiar do Docker, interrompendo o aplicativo monolítico em sistemas sub que pode ser expandida, desenvolvidos e implantados individualmente pode ser o ponto de entrada para o território de microservices.

> ### <a name="references--common-web-architectures"></a>Referências – comum arquiteturas de Web
> - **A arquitetura de limpeza**  
> <https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html>
> - **A arquitetura de transparência**  
> <http://jeffreypalermo.com/blog/the-onion-architecture-part-1/>
> - **O padrão de repositório**  
> <http://deviq.com/repository-pattern/>
> - **Exemplo de solução de limpeza de arquitetura**  
> <https://github.com/ardalis/cleanarchitecture>
> - **A arquitetura de livro eletrônico Microservices** <http://aka.ms/MicroservicesEbook>

>[!div class="step-by-step"]
[Anterior] (arquitetura-principles.md) [Avançar] (comum-cliente-lado-web-technologies.md)
