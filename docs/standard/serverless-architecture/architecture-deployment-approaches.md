---
title: Abordagens de implantação de arquitetura - aplicativos sem servidor
description: Um guia para arquiteturas empresariais de maneiras diferentes são implantados na nuvem, com a comparação entre IaaS, PaaS, contêineres e sem servidor.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 6566971d8984ec046b8b5fa2db295c1d48c30b20
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2018
ms.locfileid: "49369602"
---
# <a name="architecture-deployment-approaches"></a>Abordagens de implantação de arquitetura

Independentemente da arquitetura pode variar a abordagem usada para criar um aplicativo de negócios, a implementação ou implantação desses aplicativos. As empresas hospedam aplicativos em todo o hardware físico para as funções sem servidor.

## <a name="n-tier-applications"></a>aplicativos de n camadas

O [padrão de arquitetura de N camadas](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier) é uma arquitetura madura e simplesmente se refere a aplicativos que separam várias camadas lógicas em camadas físicas separadas. Arquitetura de N camadas é uma implementação física da arquitetura de N camadas. A implementação mais comum dessa arquitetura inclui:

* Uma camada de apresentação, por exemplo um aplicativo web.
* Uma API ou dados de camada de acesso, como uma API REST.
* Uma camada de dados, como um banco de dados SQL.

![Arquitetura de N camadas](./media/n-tier-architecture.png)

Soluções de N camadas têm as seguintes características:

* Projetos normalmente são alinhados com as camadas.
* Testes podem ser abordadas diferente pela camada.
* Camadas fornecem camadas de abstração, por exemplo, a camada de apresentação é normalmente precisa saber os detalhes da implementação da camada de dados.
* Normalmente, as camadas apenas interagem com camadas adjacentes.
* Versões geralmente são gerenciadas no projeto e, portanto, a camada, nível. Uma simple alteração de API pode exigir uma nova versão de uma camada intermediária inteira.

Essa abordagem oferece vários benefícios, incluindo:

* Isolamento do banco de dados (geralmente o front-end não tem acesso direto para o banco de dados back-end).
* Reutilizar da API (por exemplo, móveis, área de trabalho e os clientes de aplicativo web podem reutilizar as mesmas APIs).
* Capacidade de escalar horizontalmente camadas independentes uns dos outros.
* Isolamento de refatoração: uma camada pode ser Refatorada sem afetar outras camadas.

## <a name="on-premises-and-infrastructure-as-a-service-iaas"></a>Locais e infraestrutura como serviço (IaaS)

A abordagem tradicional para hospedagem de aplicativos requer hardware de comprar e gerenciar todas as instalações de software, incluindo o sistema operacional. Originalmente envolvidos centros de dados cara e o hardware físico. Os desafios que acompanham o hardware físico de operação são muitos, incluindo:

* A necessidade de comprar em excesso para "apenas no caso de" ou cenários de demanda de pico.
* Protegendo o acesso físico ao hardware.
* Responsabilidade por falha de hardware (como falha de disco).
* Resfriamento.
* Configurar roteadores e balanceadores de carga.
* Redundância de energia.
* Protegendo o acesso ao software.

![Abordagem IaaS](./media/iaas-approach.png)

Virtualização de hardware, por meio de "máquinas virtuais" permite que a infraestrutura como serviço (IaaS). Máquinas de host são particionadas com eficiência para fornecer recursos para instâncias de alocações para sua própria memória, CPU e armazenamento. A equipe provisiona as VMs necessárias e configura o acesso ao armazenamento e redes associadas.

Para obter mais informações, consulte [arquitetura de referência de N camadas de máquina de virtual](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier).

Embora muitas preocupações de endereço de virtualização e infraestrutura como serviço (IaaS), ele ainda deixa muita responsabilidade nas mãos da equipe de infraestrutura. A equipe mantém versões de sistema operacional, aplica os patches de segurança e instala as dependências de terceiros em computadores de destino. Aplicativos muitas vezes se comportam diferentemente em computadores de produção em comparação comparadas o ambiente de teste. Problemas podem surgir devido a versões de dependência diferentes e/ou níveis de SKU do sistema operacional. Embora muitas organizações implantam aplicativos de N camadas para esses destinos, muitas empresas se beneficiar da implantação para um modelo nativo de nuvem mais como [plataforma como serviço](#platform-as-a-service-paas). Arquiteturas de microsserviços são um desafio maior devido aos requisitos para escalar horizontalmente para elasticidade e resiliência.

Para obter mais informações, consulte [máquinas virtuais](https://docs.microsoft.com/azure/virtual-machines/).

## <a name="platform-as-a-service-paas"></a>Plataforma como serviço (PaaS)

Plataforma como serviço (PaaS) oferece configurado soluções que os desenvolvedores podem conectar diretamente em. PaaS é outro termo para hospedagem gerenciados. Ele elimina a necessidade de gerenciar o sistema operacional base, patches de segurança e em muitos casos as dependências de terceiros. Exemplos de plataformas de aplicativos web, bancos de dados, e o back-ends móveis.

PaaS resolve os desafios comuns para o IaaS. PaaS permite que o desenvolvedor se concentre no esquema de banco de dados ou de código em vez de como ele é implantado. Benefícios do PaaS:

* Paga para usar os modelos que eliminam a sobrecarga de investir em máquinas ociosas.
* Direcione a implantação e DevOps aprimorado, integração contínua (CI) e pipelines de entrega contínua (CD).
* Atualizações automáticas, atualizações e patches de segurança.
* Expansão através dos botões e escalar verticalmente (escala elástica).

A principal desvantagem de PaaS, tradicionalmente, tem sido bloqueio de fornecedor. Por exemplo, alguns provedores de PaaS apenas dar suporte a ASP.NET, Node. js, ou outras plataformas e idiomas específicos. Produtos como o serviço de aplicativo do Azure foram desenvolvidos para tratar várias plataformas e dar suporte a uma variedade de linguagens e estruturas para hospedar aplicativos web.

![Plataforma como uma arquitetura de serviço](./media/paas-architecture.png)

## <a name="software-as-a-service-saas"></a>Software como serviço (SaaS)

Software como um serviço ou SaaS é centralmente hospedado e disponível sem instalação local ou provisionamento. SaaS normalmente é hospedado sobre o PaaS como plataforma para a implantação de software. SaaS fornece serviços para executar e conectar-se com o software existente. SaaS costuma ser vertical específico e do setor. O SaaS normalmente é licenciado e normalmente fornece um modelo cliente/servidor. Ofertas de SaaS mais modernas usam aplicativos baseados na web para o cliente. As empresas normalmente consideram SaaS como uma solução de negócios para ofertas de licença. Ele geralmente não é implementado como consideração de arquitetura para escalabilidade e capacidade de manutenção de um aplicativo. Na verdade, a maioria das soluções de SaaS são criados em IaaS, PaaS e/ou sem servidor back-ends.

Saiba mais sobre SaaS por meio de um [aplicativo de exemplo](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app).

## <a name="containers-and-functions-as-a-service-faas"></a>Contêineres e funções como um serviço (FaaS)

Contêineres são uma solução interessante que permite os benefícios de PaaS como sem a sobrecarga de IaaS. Um contêiner é essencialmente um tempo de execução que contém os itens essenciais necessários para executar um aplicativo exclusivo. A parte do kernel ou o núcleo do sistema operacional do host e serviços, como armazenamento são compartilhados entre um host. O kernel compartilhado permite que os contêineres ser leve (alguns são meros megabytes em tamanho, em comparação comparada o tamanho de gigabyte de típicos máquinas de virtuais). Com hosts que já esteja em execução, contêineres podem ser iniciados rapidamente, facilitando a alta disponibilidade. A capacidade de girar contêineres rapidamente também fornece camadas adicionais de resiliência. O docker é uma das implementações mais populares de contêineres.

Benefícios dos contêineres incluem:

* Leve e portátil
* Independente para que não haja necessidade de instalar as dependências
* Fornecer um ambiente consistente, independentemente do host (executa exatamente as mesmas em um laptop como em um servidor de nuvem)
* Pode ser provisionado rapidamente para escala horizontal
* Pode ser reiniciado rapidamente para se recuperar de falha

Um contêiner é executado em um host do contêiner (que por sua vez, podem ser executados em uma máquina bare-metal ou uma máquina virtual). Vários contêineres ou instâncias dos mesmos contêineres podem executar em um único host. Para failover true e resiliência, contêineres devem ser dimensionados em hosts.

Para obter mais informações sobre contêineres do Docker, consulte [o que é Docker](../microservices-architecture/container-docker-introduction/docker-defined.md)?

Gerenciar contêineres em hosts normalmente requer uma ferramenta de orquestração, como Kubernetes. Configurar e gerenciar soluções de orquestração podem adicionar uma sobrecarga adicional e complexidade aos projetos. Felizmente, muitos provedores de nuvem fornecem serviços de orquestração por meio de Soluções PaaS para simplificar o gerenciamento de contêineres.

A imagem a seguir ilustra um exemplo de instalação do Kubernetes. O endereço de nós na instalação do scale out e o failover. Eles são executados Docker instâncias de contêiner que são gerenciadas pelo servidor mestre. O *kubelet* é o cliente que retransmite comandos do Kubernetes para Docker.

![Kubernetes](./media/kubernetes-example.png)

Para obter mais informações sobre a orquestração, consulte [Kubernetes no Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes).

Funções como um serviço (FaaS) é um serviço de contêiner especializado que é semelhante sem servidor. Uma implementação específica de FaaS, chamado [OpenFaaS](https://github.com/openfaas/faas), fica na parte superior de contêineres para fornecer funcionalidades sem servidor. OpenFaaS fornece modelos que todas as dependências de contêiner necessárias para executar um trecho de código do pacote. Usando modelos simplifica o processo de implantação do código como uma unidade funcional. OpenFaaS tem como alvo as arquiteturas que já incluam contêineres e orquestradores porque ele pode usar a infraestrutura existente. Embora isso forneça funcionalidade sem servidor, especificamente requer que você usar o Docker e um orquestrador.

## <a name="serverless"></a>Sem servidor

Uma arquitetura sem servidor fornece uma separação clara entre o código e seu ambiente de hospedagem. Implementar o código em um *função* que é invocada por um *gatilho*. Depois que essa função é encerrada, todos os seus recursos necessários podem ser liberados. O gatilho pode ser manual, um processo de tempo, uma solicitação HTTP ou um upload de arquivo. O resultado do gatilho é a execução de código. Embora as plataformas sem servidor variem, mais fornecem acesso a APIs e associações predefinidas para simplificar tarefas como gravar em um banco de dados ou enfileiramento resultados.

Sem servidor é uma arquitetura que depende extremamente afastar o ambiente de host para se concentrar no código. Ele pode ser considerado *menos server*.

Soluções de contêiner fornecem existente de desenvolvedores criem scripts para publicar código sem servidor pronto para imagens. Outras implementações usam soluções de PaaS existentes para fornecer uma arquitetura escalonável.

A abstração significa que a equipe de DevOps não precisa provisionar ou gerenciar servidores, nem contêineres específicos. O código de hosts de plataforma sem servidor, como scripts ou executáveis empacotados criado com um SDK relacionado e aloca os recursos necessários para o código dimensionar.

A ilustração a seguir mostra quatro componentes sem servidor. Uma solicitação HTTP faz com que o código de API de check-out seja executado. A API de check-out insere o código em um banco de dados e a inserção dispara várias outras funções para executar para realizar tarefas como tarefas de computação e concluir o pedido.

![Implementação sem servidor](./media/serverless-implementation.png)

As vantagens do uso sem servidor incluem:

* **Alta densidade.** Muitas instâncias do mesmo código sem servidor podem executar no mesmo host em comparação comparado contêineres ou máquinas virtuais. A escala de instâncias em vários hosts de expansão e resiliência.
* **Microcobrança**. Lista de provedores mais sem servidor com base em execuções sem servidor, permitindo economia de custos grande em determinados cenários.
* **Escala instantânea**. Sem servidor pode ser dimensionado de acordo com as cargas de trabalho automaticamente e rapidamente.
* **Tempo de colocação no mercado mais rápido** os desenvolvedores se concentrem no código e implantar diretamente para a plataforma sem servidor. Componentes podem ser liberados independentemente uns dos outros.

Sem servidor é discutido com mais frequência no contexto de computação, mas também pode aplicar aos dados. Por exemplo, [SQL do Azure](https://docs.microsoft.com/azure/sql-database) e [Cosmos DB](https://docs.microsoft.com/azure/cosmos-db) fornecem bancos de dados de nuvem que não exigem que você configure as máquinas de host ou clusters. Este livro se concentra na computação sem servidor.

## <a name="summary"></a>Resumo

Há uma ampla gama de opções disponíveis para arquitetura, inclusive uma abordagem híbrida. Sem servidor simplifica a abordagem, o gerenciamento e o custo dos recursos de aplicativo às custas de controle e portabilidade. No entanto, muitas plataformas sem servidor expor a configuração para ajudar a ajustar a solução. Boas práticas de programação também podem levar a um código mais portátil e menos bloqueio na plataforma sem servidor. A tabela a seguir ilustra as abordagens de arquitetura lado a lado. Escolha sem servidor com base em seu dimensionamento necessidades, se você deseja gerenciar o tempo de execução e como é possível dividir suas cargas de trabalho em componentes pequenos. Você saberá mais sobre os desafios potenciais com sem servidor e outros pontos de decisão no próximo capítulo.

|         |IaaS     |PaaS     |Contêiner|Sem servidor|
|---------|---------|---------|---------|----------|
|**Ajustar Escala**|VM       |Instância |Aplicativo      |Função  |
|**Abstrai**|Hardware|Plataforma|Sistema operacional de Host|Tempo de execução   |
|**Unidade** |VM       |Projeto  |Image    |Código      |
|**Tempo de Vida**|meses|Dias para meses|Minutos a dias|Milissegundos de minutos|
|**responsabilidade**|Aplicativos, dependências, tempo de execução e sistema operacional|Aplicativos e dependências|Aplicativos, dependências e tempo de execução|Função

* **Escala** refere-se à unidade que é usada para dimensionar o aplicativo
* **Abstrai** refere-se para a camada que é abstraída pela implementação
* **Unidade** refere-se ao escopo do que é implantado
* **Tempo de vida** refere-se ao tempo de execução típico de uma instância específica
* **Responsabilidade** refere-se à sobrecarga para compilar, implantar e manter o aplicativo

O próximo capítulo se concentrar em arquitetura sem servidor, casos de uso e padrões de design.

## <a name="recommended-resources"></a>Recursos recomendados

* [Guia de arquitetura de aplicativo do Azure](https://docs.microsoft.com/azure/architecture/guide/)
* [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db)
* [SQL do Azure](https://docs.microsoft.com/azure/sql-database)
* [Padrão de arquitetura de N camadas](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier)
* [Kubernetes no Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes)
* [Microsserviços](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)
* [Arquitetura de referência de N camadas de máquina virtual](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)
* [Máquinas virtuais](https://docs.microsoft.com/azure/virtual-machines/)
* [O que é o Docker?](../microservices-architecture/container-docker-introduction/docker-defined.md)
* [Aplicativo da Wingtip Tickets SaaS](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)

>[!div class="step-by-step"]
[Anterior](architecture-approaches.md)
[Próximo](serverless-architecture.md)