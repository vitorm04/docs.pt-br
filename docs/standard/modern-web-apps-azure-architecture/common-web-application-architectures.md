---
title: Arquiteturas comuns de aplicativo Web
description: Projetar aplicativos Web modernos com o ASP.NET Core e o Microsoft Azure | arquiteturas comuns de aplicativo Web
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.openlocfilehash: cb9a1d68d4c7c66c6adab3a5e932ee37c3ea22b0
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106417"
---
# <a name="common-web-application-architectures"></a>Arquiteturas comuns de aplicativo Web

> "Se você acha que uma boa arquitetura é cara, tente usar uma arquitetura ruim."  
> _- Brian Foote e Joseph Yoder_

## <a name="summary"></a>Resumo

A maioria dos aplicativos .NET tradicionais é implantada como unidades individuais correspondentes a um executável ou a um único aplicativo Web em execução em um único AppDomain do IIS. Esse é o modelo de implantação mais simples e atende muito bem a diversos aplicativos internos e públicos menores. No entanto, mesmo considerando essa única unidade de implantação, a maioria dos aplicativos de negócios não triviais se beneficia de uma separação lógica em várias camadas.

## <a name="what-is-a-monolithic-application"></a>O que é um aplicativo monolítico?

Um aplicativo monolítico é aquele que é totalmente autossuficiente, em termos de comportamento. Ele pode interagir com outros serviços ou armazenamentos de dados durante a execução de suas operações, mas o núcleo de seu comportamento é executado em seu próprio processo e o aplicativo inteiro normalmente é implantado como uma única unidade. Se um aplicativo desse tipo precisar ser dimensionado horizontalmente, em geral, o aplicativo inteiro será duplicado em vários servidores ou máquinas virtuais.

## <a name="all-in-one-applications"></a>Aplicativos todos-em-um

O menor número possível de projetos para uma arquitetura de aplicativo é um. Nessa arquitetura, toda a lógica do aplicativo está contida em um único projeto, compilada em um único assembly e implantada como uma única unidade.

Um novo projeto ASP.NET Core, seja ele criado no Visual Studio ou por meio da linha de comando, começa como um simples monólito "todos-em-um". Ele contém todo o comportamento do aplicativo, incluindo a lógica de apresentação, de negócios e de acesso a dados. A Figura 5-1 mostra a estrutura de arquivos de um aplicativo de projeto único.

**Figura 5-1.** Um aplicativo ASP.NET Core de projeto único

![](./media/image5-1.png)

Em um cenário de projeto único, a separação de interesses é obtida com o uso de pastas. O modelo padrão inclui pastas separadas para as responsabilidades do padrão MVC de Modelos, Exibições e Controladores, bem como pastas adicionais para Dados e Serviços. Nessa disposição, os detalhes de apresentação devem ser limitados tanto quanto possível à pasta Views e os detalhes de implementação de acesso a dados devem ser limitados às classes mantidas na pasta Data. A lógica de negócios deve residir nos serviços e nas classes dentro da pasta Models.

Embora simples, a solução monolítica de projeto único traz algumas desvantagens. À medida que o tamanho e a complexidade do projeto aumentam, o número de arquivos e pastas continuará crescendo também. Os interesses de interface do usuário (modelos, exibições, controladores) residem em várias pastas, que não são agrupadas em ordem alfabética. Esse problema só fica pior quando constructos adicionais no nível da interface do usuário, como Filters ou ModelBinders, são adicionados em suas próprias pastas. A lógica de negócios é distribuída entre as pastas Models e Services e não há nenhuma indicação clara de quais classes em quais pastas devem depender de qual delas. Essa falta de organização no nível do projeto costuma levar ao [código espaguete](http://deviq.com/spaghetti-code/).

Para resolver esses problemas, os aplicativos geralmente evoluem para soluções de vários projetos, em que cada projeto é considerado um residente de determinada *camada* do aplicativo.

## <a name="what-are-layers"></a>O que são camadas?

Conforme os aplicativos aumentam em complexidade, uma maneira de gerenciar essa complexidade é dividir o aplicativo de acordo com suas responsabilidades ou interesses. Isso segue a separação do princípio de interesses e pode ajudar a manter organizada uma base de código em expansão, de modo que os desenvolvedores possam encontrar com facilidade o local em que determinada funcionalidade foi implementada. Apesar disso, a arquitetura em camadas oferece inúmeras vantagens, além de apenas a organização do código.

Com a organização do código em camadas, a funcionalidade comum de baixo nível pode ser reutilizada em todo o aplicativo. Essa reutilização é útil porque isso significa que menos código precisa ser escrito e porque ela pode permitir que o aplicativo seja padronizado em uma única implementação, seguindo o princípio DRY.

Com uma arquitetura em camadas, os aplicativos podem impor restrições sobre quais camadas podem se comunicar com outras camadas. Isso ajuda na obtenção do encapsulamento. Quando uma camada é alterada ou substituída, somente as camadas que trabalham com ela devem ser afetadas. Ao limitar quais camadas dependem de outras camadas, o impacto das alterações pode ser reduzido, de modo que uma única alteração não afete todo o aplicativo.

As camadas (e o encapsulamento) facilitam grande parte da substituição da funcionalidade dentro do aplicativo. Por exemplo, um aplicativo inicialmente pode usar seu próprio banco de dados do SQL Server para persistência, mas, posteriormente, pode optar por usar uma estratégia de persistência baseada em nuvem ou uma protegida por uma API Web. Se o aplicativo encapsulou corretamente sua implementação de persistência em uma camada lógica, essa camada específica do SQL Server pode ser substituída por uma nova que implementa a mesma interface pública.

Além do potencial de alternância de implementações em resposta a alterações futuras nos requisitos, as camadas de aplicativo também podem facilitar a alternância de implementações para fins de teste. Em vez da necessidade de gravar testes que operam na camada de dados reais ou na camada de interface do usuário do aplicativo, essas camadas podem ser substituídas em tempo de teste com implementações fictícias que fornecem respostas conhecidas a solicitações. Isso geralmente facilita e agiliza muito a gravação e a execução de testes quando comparado à execução de testes novamente na infraestrutura real do aplicativo.

A disposição em camadas lógicas é uma técnica comum para melhorar a organização do código em aplicativos de software empresariais, e há várias maneiras pelas quais o código pode ser organizado em camadas.

> [!NOTE]
> As *camadas* representam uma separação lógica dentro do aplicativo. Caso a lógica do aplicativo seja fisicamente distribuída em servidores ou processos separados, esses destinos de implantação física separados são chamados de *camadas*. É possível, e bastante comum, ter um aplicativo de N-Camadas que é implantado em uma única camada.

## <a name="traditional-n-layer-architecture-applications"></a>Aplicativos tradicionais da arquitetura de "N Camadas"

A organização mais comum da lógica do aplicativo em camadas é mostrada na Figura 5-2.

**Figura 5-2.** Camadas de aplicativo típicas.

![](./media/image5-2.png)

Essas camadas são frequentemente abreviadas como interface do usuário, BLL (Camada de Lógica de Negócios) e DAL (Camada de Acesso a Dados). Usando essa arquitetura, os usuários fazem solicitações por meio da camada de interface do usuário, que interage com a BLL. A BLL, por sua vez, pode chamar a DAL para solicitações de acesso a dados. A camada de interface do usuário não deve fazer solicitações à DAL diretamente nem deve interagir com persistência diretamente por outros meios. Da mesma forma, a BLL só deve interagir com persistência por meio da DAL. Assim, cada camada tem sua própria responsabilidade conhecida.

Uma desvantagem dessa abordagem tradicional de disposição em camadas é que as dependências em tempo de compilação são executadas de cima para baixo. Ou seja, a camada de interface do usuário depende da BLL, que depende da DAL. Isso significa que a BLL, que normalmente contém a lógica mais importante no aplicativo, depende dos detalhes de implementação de acesso a dados (e geralmente da existência de um banco de dados). O teste da lógica de negócios em uma arquitetura como essa costuma ser difícil, exigindo um banco de dados de teste. O princípio da inversão de dependência pode ser usado para resolver esse problema, como você verá na próxima seção.

A Figura 5-3 mostra uma solução de exemplo, que divide o aplicativo em três projetos por responsabilidade (ou camada).

**Figura 5-3.** Um aplicativo monolítico simples com três projetos.

![](./media/image5-3.png)

Embora esse aplicativo use vários projetos para fins de organização, ele ainda é implantado como uma única unidade e seus clientes interagirão com ele como um único aplicativo Web. Isso possibilita um processo de implantação muito simples. A Figura 5-4 mostra como um aplicativo desse tipo pode ser hospedado por meio do Microsoft Azure.

![](./media/image5-4.png)

**Figura 5-4.** Implantação simples do Aplicativo Web do Azure

Conforme o aplicativo precisar ser aumentado, soluções de implantação mais robustas e complexas poderão ser necessárias. A Figura 5-5 mostra um exemplo de um plano de implantação mais complexo compatível com funcionalidades adicionais.

![](./media/image5-5.png)

**Figura 5-5.** Implantando um aplicativo Web em um Serviço de Aplicativo do Azure

Internamente, a organização desse projeto em vários projetos com base na responsabilidade melhora a facilidade de manutenção do aplicativo.

Essa unidade pode ser escalada verticalmente ou expandida para aproveitar a escalabilidade sob demanda baseada em nuvem. Escalar verticalmente significa adicionar mais CPU, memória, espaço em disco ou outros recursos aos servidores que hospedam o aplicativo. Escalar horizontalmente significa adicionar mais instâncias desses servidores, sejam servidores físicos, sejam máquinas virtuais. Quando o aplicativo é hospedado em várias instâncias, um balanceador de carga é usado para atribuir solicitações a instâncias individuais do aplicativo.

A abordagem mais simples para dimensionar um aplicativo Web no Azure é configurar o dimensionamento manualmente no Plano do Serviço de Aplicativo do aplicativo. A Figura 5-6 mostra a tela apropriada do painel do Azure para configurar a quantidade de instâncias que atendem um aplicativo.

![](./media/image5-6.png)

**Figura 5-6.** Dimensionamento do Plano do Serviço de Aplicativo no Azure.

## <a name="clean-architecture"></a>Arquitetura limpa

Os aplicativos que seguem o Princípio da Inversão de Dependência, bem como os princípios de DDD (Design Controlado por Domínio), tendem a chegar a uma arquitetura semelhante. Essa arquitetura foi conhecida por muitos nomes ao longo dos anos. Um dos primeiros nomes foi Arquitetura Hexagonal, seguido por Portas e Adaptadores. Mais recentemente, ela é citada como a [Arquitetura Cebola](http://jeffreypalermo.com/blog/the-onion-architecture-part-1/) ou [Arquitetura Limpa](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html). É esse último nome, Arquitetura Limpa, que é usado como base para descrever a arquitetura neste livro eletrônico.

> [!NOTE]
> O termo Arquitetura Limpa pode ser aplicado a aplicativos criados com os Princípios de DDD, bem como os que não são criados com o DDD. No caso anterior, essa combinação pode ser chamada de "Arquitetura de DDD Limpa".

A arquitetura limpa coloca a lógica de negócios e o modelo de aplicativo no centro do aplicativo. Em vez de fazer com que a lógica de negócios dependa do acesso a dados ou de outros interesses da infraestrutura, essa dependência é invertida: os detalhes de implementação e a infraestrutura dependem do Núcleo do Aplicativo. Isso é feito pela definição de abstrações, ou interfaces, no Núcleo do Aplicativo, que, em seguida, são implementadas por tipos definidos na camada de infraestrutura. Uma maneira comum de visualizar essa arquitetura é usar uma série de círculos concêntricos, semelhantes a uma cebola. A Figura 5-X mostra um exemplo desse estilo de representação de arquitetura.

![](./media/image5-7.png)

**Figura 5-7.** Arquitetura Limpa; exibição de cebola

Nesse diagrama, as dependências fluem para o círculo interno. Assim, você pode ver que o Núcleo do Aplicativo (que ganha seu nome devido à posição no núcleo desse diagrama) não tem dependências de outras camadas de aplicativo. Bem no centro estão as entidades e as interfaces do aplicativo. Fora dele, mas ainda no Núcleo do Aplicativo, estão os serviços de domínio, que normalmente implementam interfaces definidas no círculo interno. Fora do Núcleo do Aplicativo, as camadas de Interface do Usuário e de Infraestrutura dependem do Núcleo do Aplicativo, mas não (necessariamente) entre si.

A Figura 5-X mostra um diagrama de camada horizontal mais tradicional que reflete melhor a dependência entre a interface do usuário e outras camadas.

![](./media/image5-8.png)

**Figura 5-8.** Arquitetura Limpa; exibição de camada horizontal

Observe que as setas sólidas representam as dependências em tempo de compilação, enquanto a seta tracejada representa uma dependência somente em tempo de execução. Usando a arquitetura limpa, a camada de interface do usuário funciona com as interfaces definidas no Núcleo do Aplicativo em tempo de compilação. O ideal é que ela não tenha conhecimento dos tipos de implementação definidos na camada de infraestrutura. No entanto, em tempo de execução, esses tipos de implementação serão necessários para a execução do aplicativo e, portanto, precisarão estar presentes e conectados às interfaces do Núcleo do Aplicativo por meio da injeção de dependência.

A Figura 5-9 mostra uma exibição mais detalhada da arquitetura de um aplicativo ASP.NET Core quando criado seguindo essas recomendações.

![Arquitetura do ASP.NET Core](./media/image5-9.png)

**Figura 5-9.** Diagrama da arquitetura do ASP.NET Core que segue a Arquitetura Limpa.

Como o Núcleo do Aplicativo não depende da Infraestrutura, é muito fácil gravar testes de unidade automatizados para essa camada. A Figuras 5-10 e 5-11 mostram como os testes se enquadram nessa arquitetura.

![UnitTestCore](./media/image5-10.png)

**Figura 5-10.** Realizando o teste de unidade do Núcleo do Aplicativo em isolamento.

![IntegrationTests](./media/image5-11.png)

**Figura 5-11.** Realizando o teste de integração de implementações de Infraestrutura com dependências externas.

Como a camada de interface do usuário não tem nenhuma dependência direta dos tipos definidos no projeto de Infraestrutura, da mesma forma, é muito fácil alternar entre implementações, a fim de facilitar o teste ou em resposta a alterações nos requisitos do aplicativo. O uso interno do ASP.NET Core e o suporte à injeção de dependência torna essa arquitetura a maneira mais apropriada de estruturar aplicativos monolíticos não triviais.

Em aplicativos monolíticos, os projetos de Núcleo do Aplicativo, Infraestrutura e Interface do Usuário são todos executados como um único aplicativo. A arquitetura do aplicativo em tempo de execução pode ser semelhante à Figura 5-12.

![Arquitetura do ASP.NET Core 2](./media/image5-12.png)

**Figura 5-12.** Arquitetura em tempo de execução de um aplicativo ASP.NET Core de exemplo.

### <a name="organizing-code-in-clean-architecture"></a>Organizando o código na Arquitetura Limpa

Em uma solução de Arquitetura Limpa, cada projeto tem responsabilidades bem-definidas. Dessa forma, alguns tipos pertencerão a cada projeto e, com frequência, você encontrará pastas correspondentes a esses tipos no projeto apropriado.

O Núcleo do Aplicativo contém o modelo de negócios, que inclui entidades, serviços e interfaces. Essas interfaces incluem abstrações para operações que serão executadas por meio da Infraestrutura, como acesso a dados, acesso ao sistema de arquivos, chamadas de rede, etc. Às vezes, as interfaces ou os serviços definidos nessa camada precisarão trabalhar com tipos que não são de entidade que não têm dependências na interface do usuário ou na Infraestrutura. Eles podem ser definidos como DTOs (Objetos de Transferência de Dados) simples.

> ### <a name="application-core-types"></a>Tipos de Núcleo do Aplicativo
> -   Entidades (classes de modelo de negócios que são persistidas)
> -   Interfaces
> -   Serviços
> -   DTOs

O projeto de Infraestrutura normalmente incluirá implementações de acesso a dados. Em um aplicativo Web ASP.NET Core típico, isso incluirá o DbContext do Entity Framework, as Migrações do EF Core que foram definidas e as classes de implementação de acesso a dados. A maneira mais comum de abstrair o código de implementação de acesso a dados é pelo uso do [padrão de design de Repositório](http://deviq.com/repository-pattern/).

Além das implementações de acesso a dados, o projeto de Infraestrutura deve conter implementações de serviços que devem interagir com os interesses de infraestrutura. Esses serviços devem implementar as interfaces definidas no Núcleo do Aplicativo e, portanto, a Infraestrutura deve ter uma referência ao projeto de Núcleo do Aplicativo.

> ### <a name="infrastructure-types"></a>Tipos de infraestrutura
> -   Tipos do EF Core (DbContext, Migrações)
> -   Tipos de implementação de acesso a dados (Repositórios)
> -   Serviços específicos a uma infraestrutura (FileLogger, SmtpNotifier, etc.)

A camada de interface do usuário em um aplicativo ASP.NET Core MVC será o ponto de entrada para o aplicativo e será um projeto ASP.NET Core MVC. Esse projeto deve referenciar o projeto de Núcleo do Aplicativo e seus tipos devem interagir com a infraestrutura estritamente por meio das interfaces definidas no Núcleo do Aplicativo. Nenhuma criação de instância direta de tipos de camada de infraestrutura (ou chamadas estáticas a esses tipos) deve ser permitida na camada de interface do usuário.

> ### <a name="ui-layer-types"></a>Tipos de camada de interface do usuário
> -   Controladores
> -   Filtros
> -   Exibições
> -   ViewModels
> -   Inicialização

A classe Startup é responsável por configurar o aplicativo e conectar os tipos de implementação às interfaces, permitindo que a injeção de dependência funcione corretamente em tempo de execução.

> [!NOTE]
> Para conectar a injeção de dependência em ConfigureServices no arquivo Startup.cs do projeto de interface do usuário, o projeto poderá precisar referenciar o projeto de Infraestrutura. Essa dependência pode ser eliminada com mais facilidade por meio de um contêiner de DI personalizado. Para as finalidades desta amostra, a abordagem mais simples é permitir que o projeto de interface do usuário referencie o projeto de Infraestrutura.

## <a name="monolithic-applications-and-containers"></a>Contêineres e aplicativos monolíticos 

Você pode criar um Aplicativo ou Serviço Web baseado em uma implantação única e monolítica e implantá-lo como um contêiner. Dentro do aplicativo, ele pode não ser monolítico, mas organizados em várias bibliotecas, componentes ou camadas. Externamente, ele é um único contêiner, como um único processo, um único aplicativo Web ou um único serviço.

Para gerenciar esse modelo, implante um contêiner único para representar o aplicativo. Para dimensionar, basta adicionar mais cópias com um balanceador de carga na frente. A simplicidade está em gerenciar um a implantação única em um contêiner ou VM único.

![](./media/image5-13.png)

É possível incluir vários componentes/bibliotecas ou camadas internas em cada contêiner, conforme ilustrado na Figura 5-X. Mas, seguindo o princípio de contêiner de *"um contêiner executa uma ação e faz isso em um processo*", o padrão monolítico pode gerar um conflito.

O ponto negativo dessa abordagem ficará evidente se ou quando o aplicativo crescer e for necessário dimensioná-lo. Se o aplicativo inteiro for dimensionado, isso não será realmente um problema. Entretanto, na maioria dos casos, apenas algumas partes do aplicativo são os pontos de redução que exigem dimensionamento, enquanto outros componentes são menos utilizados.

Usando o exemplo de comércio eletrônico típico: o que você provavelmente precisa dimensionar é o componente de informações do produto. Uma quantidade muito maior de clientes procura produtos em vez de comprá-los. Mais clientes usam o carrinho em vez do pipeline de pagamento. Menos clientes fazem comentários ou exibem o histórico de compras. E você provavelmente tem apenas um grupo de funcionários, em uma única região, que precisa gerenciar o conteúdo e as campanhas de marketing. Ao dimensionar o design monolítico, todo o código é implantado várias vezes.

Além do problema do dimensionamento de tudo, a alteração de um único componente exige um novo teste completo de todo o aplicativo e uma reimplantação completa de todas as instâncias.

A abordagem monolítica é comum e muitas organizações estão desenvolvendo aplicativos com essa abordagem de arquitetura. Muitas estão tendo resultados bons o suficiente, enquanto outras estão atingindo os limites. Muitas criaram seus aplicativos nesse modelo, porque as ferramentas e a infraestrutura eram muito difíceis de criar arquiteturas SOA, e elas não viam a necessidade – até que o aplicativo cresceu. Se você acreditar que está atingindo os limites da abordagem monolítica, a divisão do aplicativo para permitir que ele aproveite melhor os contêineres e os microsserviços poderá ser a próxima etapa lógica.

![](./media/image5-14.png)

A implantação de aplicativos monolíticos no Microsoft Azure pode ser feita por meio de VMs dedicadas para cada instância. Com os [Conjuntos de Dimensionamento de VMs do Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), você pode dimensionar as VMs com facilidade. Os [Serviços de Aplicativos do Azure](https://azure.microsoft.com/services/app-service/) podem executar aplicativos monolíticos e dimensionar instâncias com facilidade, sem a necessidade de gerenciar as VMs. Os Serviços de Aplicativos do Azure também podem executar instâncias únicas de contêineres do Docker, simplificando a implantação. Usando o Docker, você pode implantar uma única VM como um host do Docker e executar várias instâncias. Usando o balanceador do Azure, conforme mostrado na Figura 5-14, você pode gerenciar o dimensionamento.

A implantação em vários hosts pode ser gerenciada com técnicas de implantação tradicionais. Os hosts do Docker podem ser gerenciados manualmente com comandos como **docker run** executados manualmente ou por meio da automação, como os pipelines de CD (Entrega Contínua).

### <a name="monolithic-application-deployed-as-a-container"></a>Aplicativo monolítico implantado como um contêiner

Há benefícios no uso de contêineres para gerenciar implantações de aplicativos monolíticos. O dimensionamento das instâncias de contêineres é muito mais rápido e fácil do que a implantação de VMs adicionais. Mesmo ao usar Conjuntos de Dimensionamento de VMs para dimensionar VMs, a criação de instância das VMs é demorada. Quando implantada como instâncias de aplicativo, a configuração do aplicativo é gerenciada como parte da VM.

Implantar atualizações como imagens do Docker é muito mais rápido e eficiente em termos de rede. As Imagens do Docker costumam ser iniciadas em segundos, o que agiliza as distribuições. Desmontar uma instância do Docker é tão fácil quanto emitir um comando **docker stop** e geralmente leva menos de um segundo.

Como os contêineres são inerentemente imutáveis por design, você nunca precisa se preocupar com VMs corrompidas, enquanto os scripts de atualização podem esquecer de levar em conta alguma configuração específica ou um arquivo deixado no disco.

Embora os aplicativos monolíticos possam se beneficiar com o Docker, a divisão do aplicativo monolítico em subsistemas que podem ser dimensionados, desenvolvidos e implantados individualmente pode ser o ponto de entrada para o realm de microsserviços.

> ### <a name="references--common-web-architectures"></a>Referências – Arquiteturas comuns da Web
> - **A Arquitetura Limpa**  
> <https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html>
> - **A Arquitetura Cebola**  
> <http://jeffreypalermo.com/blog/the-onion-architecture-part-1/>
> - **O Padrão de Repositório**  
> <http://deviq.com/repository-pattern/>
> - **Amostra de solução de Arquitetura Limpa**  
> <https://github.com/ardalis/cleanarchitecture>
> - **Livro eletrônico Architecting Microservices** <http://aka.ms/MicroservicesEbook>

>[!div class="step-by-step"]
[Anterior](architectural-principles.md)
[Próximo](common-client-side-web-technologies.md)
