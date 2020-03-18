---
title: Abordagens de implantação de arquitetura - Aplicativos sem servidor
description: Um guia para diferentes maneiras pelas quais as arquiteturas corporativas são implantadas na nuvem, com comparação entre IaaS, PaaS, containers e sem servidor.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: c745a4eb1c6f4a00bf139100b02f31cf3327d01e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522734"
---
# <a name="architecture-deployment-approaches"></a>Abordagens de implantação de arquitetura

Independentemente da abordagem de arquitetura usada para projetar um aplicativo de negócios, a implementação ou a implantação desses aplicativos podem variar. As empresas hospedam aplicativos em tudo, desde hardware físico até funções sem servidor.

## <a name="n-tier-applications"></a>Aplicativos N-Tier

O [padrão de arquitetura N-Tier](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier) é uma arquitetura madura e simplesmente se refere a aplicativos que separam várias camadas lógicas em camadas físicas separadas. A arquitetura N-Tier é uma implementação física da arquitetura N-Layer. A implementação mais comum desta arquitetura inclui:

- Um nível de apresentação, por exemplo, um aplicativo web.
- Uma API ou um nível de acesso a dados, como uma API REST.
- Um nível de dados, como um banco de dados SQL.

![Arquitetura n-tier](./media/n-tier-architecture.png)

As soluções n-tier têm as seguintes características:

- Os projetos são tipicamente alinhados com níveis.
- Os testes podem ser abordados de forma diferente por nível.
- Os níveis fornecem camadas de abstração, por exemplo, o nível de apresentação é tipicamente ignorante dos detalhes de implementação do nível de dados.
- Normalmente, as camadas só interagem com camadas adjacentes.
- Os lançamentos são frequentemente gerenciados no projeto e, portanto, nível, nível. Uma simples alteração de API pode exigir uma nova versão de um nível médio inteiro.

Essa abordagem oferece vários benefícios, incluindo:

- Isolamento do banco de dados (muitas vezes o front-end não tem acesso direto ao back-end do banco de dados).
- A reutilização da API (por exemplo, clientes de aplicativos móveis, desktop e web podem reutilizar as mesmas APIs).
- Capacidade de escalar níveis independentes uns dos outros.
- Refatoração do isolamento: um nível pode ser refatorado sem impactar outros níveis.

## <a name="on-premises-and-infrastructure-as-a-service-iaas"></a>Local e Infra-estrutura como serviço (IaaS)

A abordagem tradicional para hospedar aplicativos requer a compra de hardware e o gerenciamento de todas as instalações de software, incluindo o sistema operacional. Originalmente, isso envolvia data centers caros e hardware físico. Os desafios que vêm com o hardware físico operacional são muitos, incluindo:

- A necessidade de comprar excessos para "apenas no caso" ou cenários de pico de demanda.
- Garantindo acesso físico ao hardware.
- Responsabilidade pela falha de hardware (como falha de disco).
- Refrigeração.
- Configurando roteadores e balanceadores de carga.
- Redundância de energia.
- Garantindo acesso ao software.

![Abordagem iaaS](./media/iaas-approach.png)

A virtualização do hardware, por meio de "máquinas virtuais", permite a Infra-estrutura como serviço (IaaS). As máquinas host são efetivamente particionadas para fornecer recursos a instâncias com alocações para sua própria memória, CPU e armazenamento. A equipe disponibiliza as VMs necessárias e configura as redes associadas e o acesso ao armazenamento.

Para obter mais informações, consulte [a arquitetura de referência n-tier da máquina virtual](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier).

Embora a virtualização e a Infraestrutura como Serviço (IaaS) abordem muitas preocupações, ainda deixa muita responsabilidade nas mãos da equipe de infraestrutura. A equipe mantém versões do sistema operacional, aplica patches de segurança e instala dependências de terceiros nas máquinas de destino. Os aplicativos geralmente se comportam de forma diferente nas máquinas de produção em comparação com o ambiente de teste. Os problemas surgem devido a diferentes versões de dependência e/ou níveis de SKU do SISTEMA OPERACIONAL. Embora muitas organizações implantem aplicativos N-Tier para esses alvos, muitas empresas se beneficiam de implantar em um modelo nativo mais cloud, como [o Platform as a Service](#platform-as-a-service-paas). Arquiteturas com microsserviços são mais desafiadoras devido aos requisitos de escala para elasticidade e resiliência.

Para obter mais informações, consulte [máquinas virtuais](https://docs.microsoft.com/azure/virtual-machines/).

## <a name="platform-as-a-service-paas"></a>PaaS (plataforma como serviço)

Platform as a Service (PaaS) oferece soluções configuradas que os desenvolvedores podem conectar diretamente. PaaS é outro termo para hospedagem gerenciada. Elimina a necessidade de gerenciar o sistema operacional base, patches de segurança e, em muitos casos, quaisquer dependências de terceiros. Exemplos de plataformas incluem aplicativos web, bancos de dados e back ends móveis.

O PaaS aborda os desafios comuns ao IaaS. O PaaS permite que o desenvolvedor se concentre no esquema de código ou banco de dados, em vez de como ele é implantado. Os benefícios do PaaS incluem:

- Pague por modelos de uso que eliminem a sobrecarga de investir em máquinas ociosas.
- Implantação direta e devOps aprimorados, integração contínua (CI) e gasodutos de entrega contínua (CD).
- Atualizações automáticas, atualizações e patches de segurança.
- Escala e escala do botão de pressão (escala elástica).

A principal desvantagem do PaaS tradicionalmente tem sido o bloqueio do fornecedor. Por exemplo, alguns provedores paaS só suportam ASP.NET, Node.js ou outros idiomas e plataformas específicas. Produtos como o Azure App Service evoluíram para atender a várias plataformas e suportar uma variedade de idiomas e frameworks para hospedagem de aplicativos web.

![Plataforma como arquitetura de serviços](./media/paas-architecture.png)

## <a name="software-as-a-service-saas"></a>SaaS (software como serviço)

O software as a Service ou SaaS está centralmente hospedado e disponível sem instalação ou provisionamento local. O SaaS muitas vezes é hospedado no topo do PaaS como uma plataforma para implantação de software. O SaaS fornece serviços para executar e conectar-se com o software existente. O SaaS é muitas vezes específico da indústria e vertical. O SaaS é frequentemente licenciado e normalmente fornece um modelo cliente/servidor. A maioria das ofertas saas modernas usam aplicativos baseados na Web para o cliente. As empresas normalmente consideram a SaaS como uma solução de negócios para ofertas de licenças. Muitas vezes não é implementado como uma consideração de arquitetura para escalabilidade e manutenção de um aplicativo. De fato, a maioria das soluções SaaS são construídas em extremidades traseiras IaaS, PaaS e/ou sem servidor.

Saiba mais sobre o SaaS através de uma [aplicação de amostra](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app).

## <a name="containers-and-functions-as-a-service-faas"></a>Contêineres e Funções como Serviço (FaaS)

Os contêineres são uma solução interessante que permite benefícios semelhantes ao PaaS sem a sobrecarga do IaaS. Um contêiner é essencialmente um tempo de execução que contém os essenciais necessários para executar uma aplicação única. O kernel ou parte central do sistema operacional host e serviços como armazenamento são compartilhados em um host. O kernel compartilhado permite que os recipientes sejam leves (alguns são meros megabytes em tamanho, em comparação com o tamanho do gigabyte de máquinas virtuais típicas). Com os hosts já em execução, os contêineres podem ser iniciados rapidamente, facilitando alta disponibilidade. A capacidade de girar os contêineres rapidamente também fornece camadas extras de resiliência. Docker é uma das implementações mais populares de contêineres.

Os benefícios dos contêineres incluem:

- Leve e portátil
- Autônomo, portanto, não há necessidade de instalar dependências
- Forneça um ambiente consistente independentemente do host (é executado exatamente o mesmo em um laptop como em um servidor na nuvem)
- Pode ser provisionado rapidamente para a saída de escala
- Pode ser reiniciado rapidamente para se recuperar da falha

Um contêiner é executado em um host de contêiner (que, por sua vez, pode funcionar em uma máquina de metal nu ou em uma máquina virtual). Vários contêineres ou instâncias dos mesmos contêineres podem ser executados em um único host. Para o verdadeiro failover e resiliência, os contêineres devem ser dimensionados entre os hosts.

Para obter mais informações sobre os contêineres Docker, consulte [O que é Docker](../microservices/container-docker-introduction/docker-defined.md).

Gerenciar contêineres em hosts normalmente requer uma ferramenta de orquestração, como kubernetes. A configuração e o gerenciamento de soluções de orquestração podem adicionar sobrecarga e complexidade adicionais aos projetos. Felizmente, muitos provedores de nuvem fornecem serviços de orquestração através de soluções PaaS para simplificar o gerenciamento de contêineres.

A imagem a seguir ilustra um exemplo de instalação do Kubernetes. Os nós na escala de endereço de instalação e failover. Eles executam instâncias de contêiner Docker gerenciadas pelo servidor mestre. O *kubelet* é o cliente que retransmite comandos de Kubernetes para Docker.

![Kubernetes](./media/kubernetes-example.png)

Para obter mais informações sobre orquestração, consulte [Kubernetes no Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes).

Functions as a Service (FaaS) é um serviço especializado de contêineres que é semelhante ao sem servidor. Uma implementação específica do FaaS, chamada [OpenFaaS,](https://github.com/openfaas/faas)fica em cima de contêineres para fornecer recursos sem servidor. O OpenFaaS fornece modelos que embalam todas as dependências de contêineres necessárias para executar um pedaço de código. O uso de modelos simplifica o processo de implantação do código como uma unidade funcional. O OpenFaaS tem como alvo arquiteturas que já incluem contêineres e orquestradores porque pode usar a infra-estrutura existente. Embora forneça funcionalidade sem servidor, ele especificamente exige que você use Docker e um orquestrador.

## <a name="serverless"></a>Sem servidor

Uma arquitetura sem servidor fornece uma clara separação entre o código e seu ambiente de hospedagem. Você implementa código em uma *função* que é invocada por um *gatilho*. Depois que essa função sair, todos os recursos necessários podem ser liberados. O gatilho pode ser manual, um processo cronometrado, uma solicitação HTTP ou um upload de arquivo. O resultado do gatilho é a execução do código. Embora as plataformas sem servidor variem, a maioria fornece acesso a APIs e vinculações pré-definidas para simplificar tarefas como escrever em um banco de dados ou fazer filas.

Serverless é uma arquitetura que depende muito da abstração do ambiente host para se concentrar no código. Pode ser considerado como *menos servidor.*

As soluções de contêiner fornecem aos desenvolvedores scripts de compilação existentes para publicar código para imagens prontas para servidor. Outras implementações utilizam soluções PaaS existentes para fornecer uma arquitetura escalável.

A abstração significa que a equipe de DevOps não precisa provisionar ou gerenciar servidores, nem contêineres específicos. A plataforma sem servidor hospeda código, seja como script ou executáveis empacotados construídos com um SDK relacionado, e aloca os recursos necessários para que o código seja dimensionado.

Os diagramas de ilustração a seguir quatro componentes sem servidor. Uma solicitação HTTP faz com que o código da API de checkout seja executado. A API checkout insere o código em um banco de dados, e a inserção aciona várias outras funções para executar tarefas como tarefas de computação e cumprimento da ordem.

![Implementação sem servidor](./media/serverless-implementation.png)

As vantagens do sem servidor incluem:

- **Alta densidade.** Muitas instâncias do mesmo código sem servidor podem ser executadas no mesmo host em comparação com contêineres ou máquinas virtuais. A escala de instâncias em vários hosts é dimensionada e resiliência.
- **Microcobrança.** A maioria dos provedores sem servidor fatura com base em execuções sem servidor, permitindo uma enorme economia de custos em certos cenários.
- **Escala instantânea.** Sem servidor pode dimensionar para corresponder cargas de trabalho automaticamente e rapidamente.
- **Mais rápido para o mercado.** Os desenvolvedores se concentram no código e implantam diretamente na plataforma sem servidor. Os componentes podem ser liberados independentemente uns dos outros.

O serverless é mais frequentemente discutido no contexto da computação, mas também pode se aplicar aos dados. Por exemplo, [o Azure SQL](https://docs.microsoft.com/azure/sql-database) e [o Cosmos DB](https://docs.microsoft.com/azure/cosmos-db) fornecem bancos de dados em nuvem que não exigem que você configure máquinas host ou clusters. Este livro se concentra na computação sem servidor.

## <a name="summary"></a>Resumo

Há um amplo espectro de opções disponíveis para arquitetura, incluindo uma abordagem híbrida. O Serverless simplifica a abordagem, o gerenciamento e o custo dos recursos de aplicativos em detrimento do controle e da portabilidade. No entanto, muitas plataformas sem servidor expõem a configuração para ajudar a ajustar a solução. Boas práticas de programação também podem levar a mais código portátil e menos bloqueio de plataforma sem servidor. A tabela a seguir ilustra que a arquitetura se aproxima lado a lado. Escolha sem servidor com base nas necessidades da sua escala, se você deseja ou não gerenciar o tempo de execução e quão bem você pode quebrar suas cargas de trabalho em pequenos componentes. Você aprenderá sobre desafios potenciais com sem servidor e outros pontos de decisão no próximo capítulo.

|         |IaaS     |PaaS     |Contêiner|Sem servidor|
|---------|---------|---------|---------|----------|
|**Escala**|VM       |Instância |Aplicativo      |Função  |
|**Resumos**|Hardware|Plataforma|OS Host|Runtime   |
|**Unidade** |VM       |Project  |Imagem    |Código      |
|**Tempo de vida**|Months|Dias a Meses|Minutos para Dias|Milissegundos para Minutos|
|**Responsabilidade**|Aplicações, dependências, tempo de execução e sistema operacional|Aplicações e dependências|Aplicativos, dependências e tempo de execução|Função

- **Escala** refere-se à unidade que é usada para dimensionar a aplicação
- **Resumos** refere-se à camada que é abstraída pela implementação
- **Unidade** refere-se ao escopo do que é implantado
- **Lifetime** refere-se ao tempo de execução típico de uma instância específica
- **Responsabilidade** refere-se à sobrecarga para construir, implantar e manter o aplicativo

O próximo capítulo se concentrará na arquitetura sem servidor, nos casos de uso e nos padrões de design.

## <a name="recommended-resources"></a>Recursos recomendados

- [Guia de arquitetura de aplicativos do Azure](https://docs.microsoft.com/azure/architecture/guide/)
- [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db)
- [SQL Azure](https://docs.microsoft.com/azure/sql-database)
- [Padrão de arquitetura N-Tier](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier)
- [Kubernetes no Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes)
- [Microserviços](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)
- [Arquitetura de referência n-tier de máquina virtual](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)
- [Máquinas virtuais](https://docs.microsoft.com/azure/virtual-machines/)
- [O que é Docker?](../microservices/container-docker-introduction/docker-defined.md)
- [Aplicativo Wingtip Tickets SaaS](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)

>[!div class="step-by-step"]
>[Próximo](architecture-approaches.md)
>[anterior](serverless-architecture.md)
