---
title: Implantar aplicativos monolíticos em contêineres
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Implantar aplicativos monolíticos em contêineres
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 4e5b7a8202a0af26c8d61e315c3aa8f592ed45d9
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105917"
---
# <a name="containerizing-monolithic-applications"></a>Implantar aplicativos monolíticos em contêineres

Talvez você queira criar um aplicativo ou serviço Web único e monolítico e implantá-lo como um contêiner. O aplicativo em si pode não ser monolítico internamente, mas estruturado como várias bibliotecas, componentes ou até mesmo camadas (camada de aplicativo, de domínio, de acesso a dados, etc.). No entanto, externamente ele é um contêiner único – um processo único, um aplicativo Web único ou um serviço único.

Para gerenciar esse modelo, implante um contêiner único para representar o aplicativo. Para escalar verticalmente, adicione mais cópias com o balanceador de carga na frente. A simplicidade está em gerenciar um a implantação única em um contêiner ou VM único.

![](./media/image1.png)

**Figura 4-1**. Exemplo de arquitetura de um aplicativo monolítico em contêiner

É possível incluir vários componentes, bibliotecas ou camadas internas em cada contêiner, conforme ilustrado na Figura 4-1. No entanto, esse padrão monolítico pode entrar em conflito com o princípio do contêiner: "um contêiner executa uma ação em um processo". Porém, em alguns casos não haverá problemas.

O ponto negativo dessa abordagem ficará evidente se o aplicativo crescer e for necessário dimensioná-lo. Se o aplicativo inteiro puder ser dimensionado, não será realmente um problema. Entretanto, na maioria dos casos apenas algumas partes do aplicativo são os pontos de redução que exigem escalonamento, enquanto outros componentes são menos utilizados.

Por exemplo, em um aplicativo comum de comércio eletrônico, provavelmente é preciso dimensionar o subsistema de informações do produto, pois a procura por produtos é maior do que a compra. Mais clientes usam o carrinho em vez do pipeline de pagamento. Menos clientes fazem comentários ou exibem o histórico de compras. E você pode ter apenas alguns funcionários para gerenciar conteúdo e campanhas de marketing. Ao escalonar o design monolítico, todo o código dessas tarefas diferentes é implantado diversas vezes e dimensionado no mesmo grau.

Há várias maneiras de dimensionar um aplicativo – duplicação horizontal, divisão de diferentes áreas do aplicativo e partição de conceitos ou dados de negócios semelhantes. No entanto, além do problema de dimensionamento de todos os componentes, alterar um único componente exige testar novamente todo o aplicativo e reimplantar todas as instâncias.

Porém, a abordagem monolítica é comum, pois o desenvolvimento do aplicativo é inicialmente muito mais fácil do que nas abordagens de microsserviços. Assim, diversas organizações desenvolvem usando essas abordagem de arquitetura. Embora algumas delas tenham obtido bons resultados, outras estão atingindo seus limites. Muitas organizações criaram aplicativos usando esse modelo porque as ferramentas e a infraestrutura dificultaram bastante a criação de SOAs (arquiteturas orientadas a serviços) no passado, e eles não viam necessidade disso – até os aplicativos crescerem.

De uma perspectiva de infraestrutura, cada servidor pode executar vários aplicativos no mesmo host e ter um índice de eficiência razoável de uso de recursos, conforme mostrado na Figura 4-2.

![](./media/image2.png)

**Figura 4-2**. Abordagem monolítica: host executando vários aplicativos, cada um em execução como um contêiner

Os aplicativos monolíticos no Microsoft Azure podem ser implantados por meio de VMs dedicadas a cada instância. Além disso, com os [Conjuntos de Dimensionamento de VMs do Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/) é possível dimensionar as VMs de forma fácil. O [Serviço de Aplicativo do Azure](https://azure.microsoft.com/services/app-service/) também executa aplicativos monolíticos e dimensiona instâncias facilmente sem necessidade de gerenciamento de VMs. Desde 2016, o Serviços de Aplicativos do Azure também pode executar instâncias únicas de contêineres do Docker, simplificando a implantação.

Como em um ambiente de garantia de qualidade ou de produção limitada, é possível implantar diversas VMs host do Docker e balanceá-las usando o balanceador do Azure, conforme mostrado na Figura 4-3. Assim, você pode gerenciar o dimensionamento com uma abordagem de alta granularidade, pois o aplicativo inteiro está em um único contêiner.

![](./media/image3.png)

**Figura 4-3**. Exemplo de vários hosts escalando verticalmente um aplicativo em contêiner único

A implantação em vários hosts pode ser gerenciada com técnicas de implantação tradicionais. Os hosts do Docker podem ser gerenciados manualmente com comandos como `docker run` ou `docker-compose`. Outra opção é a automação, como os pipelines de entrega contínua.

## <a name="deploying-a-monolithic-application-as-a-container"></a>Implantar um aplicativo monolítico como um contêiner

Há benefícios em usar contêineres para gerenciar implantações de aplicativos monolíticos. O dimensionamento de instâncias de contêiner é muito mais rápido e fácil do que a implantação de VMs adicionais. Mesmo se você usar os Conjuntos de Dimensionamento de VMs, as VMs levarão tempo para iniciar. Quando implantado como instâncias de aplicativo tradicionais em vez de contêineres, a configuração do aplicativo é gerenciada como parte da VM, o que não é o ideal.

Implantar atualizações como imagens do Docker é muito mais rápido e eficiente em termos de rede. As imagens do Docker se inicializam em questão de segundos, o que agiliza a distribuição. Destruir uma instância de imagem do Docker é tão fácil quanto emitir um comando `docker stop` e geralmente leva menos de um segundo.

Como o design dos contêineres é imutável, não é necessário se preocupar com VMs corrompidas. Por outro lado, os scripts de atualização de uma VM podem não levar em conta configurações específicas ou arquivos deixados no disco.

Embora aplicativos monolíticos possam se beneficiar do Docker, estamos mencionando apenas as vantagens. Outros pontos positivos de gerenciar contêineres são decorrentes da implantação com orquestradores de contêiner, que gerenciam as diversas instâncias e o ciclo de vida de cada instância de contêiner. Dividir o aplicativo monolítico em subsistemas que podem ser dimensionados, desenvolvidos e implantados individualmente é o ponto de entrada no universo dos microsserviços.

## <a name="publishing-a-single-container-based-application-to-azure-app-service"></a>Publicar um aplicativo baseado em contêiner único no Serviço de Aplicativo do Azure

Seja para validar um contêiner implantado no Azure ou quando um aplicativo é baseado em contêiner único, o Serviço de Aplicativo do Azure é uma ótima maneira de oferecer serviços escalonáveis baseados em contêiner único. Usar o Serviço de Aplicativo do Azure é simples. Ele tem uma ótima integração com o GIT para facilitar a implantação do código criado no Visual Studio diretamente no Azure.

![](./media/image4.png)

**Figura 4-4**. Publicar um aplicativo baseado em contêiner único no Serviço de Aplicativo do Azure por meio do Visual Studio

Sem o Docker, se você precisasse de outros recursos, estruturas ou dependências não compatíveis com o Serviço de Aplicativo do Azure, seria necessário aguardar até que a equipe do Azure atualizasse essas dependências no Serviço de Aplicativo. Outra opção era mudar para outros serviços, como Azure Service Fabric, Serviços de Nuvem do Azure ou até mesmo VMs, em que se tinha mais controle e era possível instalar o componente ou a estrutura exigidos pelo aplicativo.

No Visual Studio 2017, o suporte para contêineres oferece a capacidade de incluir tudo o que você deseja no ambiente do aplicativo, conforme mostrado na Figura 4-4. Como está sendo executado em um contêiner, se você adicionar uma dependência ao aplicativo, será possível incluí-la em um Dockerfile ou em uma imagem do Docker.

A Figura 4-4 também mostra que o fluxo de publicação envia uma imagem por meio do registro de contêiner. Isso pode ser feito pelo Registro de Contêiner do Azure (um registro próximo às implantações no Azure e protegido por grupos e contas do Azure Active Directory) ou outros registros do Docker, como o Docker Hub ou um registro local.


>[!div class="step-by-step"]
[Anterior](index.md)
[Próximo](docker-application-state-data.md)
