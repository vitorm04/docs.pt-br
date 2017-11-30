---
title: "Aplicativos monolíticos containerizing"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Aplicativos monolíticos containerizing"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 11e2c24403b9b61584e424696c844e00e5d34b03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="containerizing-monolithic-applications"></a>Aplicativos monolíticos containerizing

Você talvez queira criar um aplicativo web única, monolithically implantado ou serviço e implantá-lo como um contêiner. O aplicativo em si pode não ser monolítico internamente, mas estruturados como várias bibliotecas, componentes ou até mesmo camadas (camada de aplicativo, camada de domínio, camada de acesso a dados, etc.). Externamente, no entanto, é um único contêiner — um único processo, um único aplicativo web ou um único serviço.

Para gerenciar esse modelo, você deve implantar um único contêiner para representar o aplicativo. Para dimensionar o, adicione mais cópias com um balanceador de carga na frente. A simplicidade é proveniente do gerenciamento de uma única implantação em um único contêiner ou VM.

![](./media/image1.png)

**Figura 4-1**. Exemplo de arquitetura de um aplicativo monolítico em contêineres

Você pode incluir vários componentes, bibliotecas ou camadas internas em cada contêiner, conforme ilustrado na Figura 4-1. No entanto, esse padrão monolítico entrarem em conflito com o princípio de contêiner "um contêiner executa uma ação e faz isso em um processo", mas podem ser okey para alguns casos.

A desvantagem dessa abordagem fica evidente se o aplicativo cresce, solicitá-la para dimensionar. Se o aplicativo inteiro pode ser dimensionado, não é realmente um problema. No entanto, na maioria dos casos, apenas algumas partes do aplicativo são os pontos de restrição que exigir dimensionamento, enquanto outros componentes são menos usado.

Por exemplo, em um aplicativo de comércio eletrônico típico, você provavelmente precisa dimensionar o subsistema de informações do produto, porque muitos clientes mais procurem produtos de comprá-las. Mais clientes usam seu carrinho de usar o pipeline de pagamento. Os clientes menos adicionem comentários ou exibam seu histórico de compra. E você pode ter apenas uma série de funcionários, o que precisa para gerenciar o conteúdo e campanhas de marketing. Se você expandir o design monolítico, todo o código para essas tarefas diferentes é implantado várias vezes e dimensionado na mesma classificação.

Há várias maneiras para dimensionar um aplicativo – eliminação de duplicação horizontal, divisão de diferentes áreas do aplicativo e particionamento conceitos semelhantes de negócios ou dados. No entanto, o problema de dimensionamento de todos os componentes, além de alterações para um único componente exigem teste completa de todo o aplicativo e uma reimplantação completa de todas as instâncias.

No entanto, a abordagem monolítica é comum, pois o desenvolvimento do aplicativo é inicialmente muito mais fácil para microservices abordagens. Portanto, muitas organizações desenvolvem usando essa abordagem de arquitetura. Embora algumas empresas tiveram bons resultados suficientes, outros estão atingindo os limites. Muitas organizações projetado seus aplicativos usando esse modelo, como as ferramentas e infraestrutura feitas muito difícil criar serviço arquiteturas orientadas a (SOA) anos, e não encontrou a necessidade, até que o aplicativo aumentou.

De uma perspectiva de infraestrutura, cada servidor pode executar muitos aplicativos dentro do mesmo host e têm uma taxa aceitável de eficiência no uso de recursos, como mostrado na Figura 4-2.

![](./media/image2.png)

**Figura 4-2**. Abordagem monolítica: Host executando vários aplicativos, cada aplicativo em execução como um contêiner

Monolíticos aplicativos no Microsoft Azure podem ser implantados usando VMs dedicadas para cada instância. Além disso, usando [conjuntos de escala de VM do Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), você pode facilmente dimensionar as VMs. [Serviço de aplicativo do Azure](https://azure.microsoft.com/services/app-service/) pode também executar aplicativos monolíticos e expandir facilmente instâncias sem a necessidade de gerenciar as máquinas virtuais. Desde 2016, serviços de aplicativo do Azure pode executar instâncias únicas de contêineres do Docker, simplificando a implantação.

Como um ambiente de controle de qualidade ou em um ambiente de produção limitado, você pode implantar o host do Docker várias VMs e equilibrá-los usando o balanceador do Azure, conforme mostrado na Figura 4-3. Isso permite que você gerencie dimensionamento com uma abordagem de alta granularidade, porque todo o aplicativo reside em um único contêiner.

![](./media/image3.png)

**Figura 4-3**. Exemplo de vários hosts de dimensionamento de um aplicativo de contêiner único

Implantação em vários hosts pode ser gerenciada com as técnicas tradicionais de implantação. Hosts de docker podem ser gerenciados com comandos como `docker run` ou `docker-compose` executada manualmente ou através da automação, como os pipelines de fornecimento contínuo (CD).

## <a name="deploying-a-monolithic-application-as-a-container"></a>Implantando um aplicativo monolítico como um contêiner

Há benefícios de usar contêineres para gerenciar implantações de aplicativo monolítico. Dimensionamento de instâncias de contêiner é muito mais rápido e mais fácil do que a implantação de VMs adicionais. Mesmo se você usar conjuntos de escala de VM, VMs levar tempo para iniciar. Quando implantado como instâncias de aplicativo tradicional, em vez de contêineres, a configuração do aplicativo é gerenciada como parte da VM, que não é ideal.

Implantando atualizações como imagens do Docker é muito mais rápida e eficiente de rede. Imagens do docker geralmente iniciam em segundos, que agiliza a implementação. Subdividir uma instância de imagem do Docker é tão fácil quanto emitir um `docker stop` de comando e normalmente é concluído em menos de um segundo.

Como contêineres são imutáveis por design, você nunca precisa se preocupar sobre VMs corrompidas. Em contraste, os scripts de atualização de uma VM podem esquecer de conta para alguma configuração específica ou o arquivo deixado no disco.

Enquanto monolíticos aplicativos podem se beneficiar do Docker, podemos tocam somente sobre os benefícios. Benefícios adicionais de gerenciamento de contêineres vêm da implantação de orchestrators do contêiner, que gerencia as várias instâncias e ciclo de vida de cada instância de contêiner. Dividir o aplicativo monolítico em subsistemas que pode ser dimensionado, desenvolvidos e implantados individualmente é o ponto de entrada para o território de microservices.

## <a name="publishing-a-single-container-based-application-to-azure-app-service"></a>Publicar um aplicativo com base em contêiner único para o serviço de aplicativo do Azure

Se você deseja obter a validação de um contêiner implantado no Azure, ou quando um aplicativo é simplesmente um aplicativo de contêiner de único, o serviço de aplicativo do Azure fornece uma ótima maneira de fornecer serviços escalonáveis com base em contêiner único. Usar o serviço de aplicativo do Azure é simple. Ele fornece uma excelente integração com o Git para tornar mais fácil executar seu código, compile-o no Visual Studio e implantá-lo diretamente no Azure.

![](./media/image4.png)

**Figura 4-4**. Publicar um aplicativo de contêiner único para o serviço de aplicativo do Azure do Visual Studio

Sem Docker, se precisar de outros recursos, estruturas ou dependências que não há suporte para o serviço de aplicativo do Azure, era necessário aguardar até que a equipe do Azure atualizada essas dependências no serviço de aplicativo. Ou você tinha que alternar para outros serviços, como o Azure Service Fabric, serviços de nuvem do Azure ou até mesmo VMs, em que você tinha mais controle e você pode instalar um componente necessário ou a estrutura do seu aplicativo.

Suporte de contêiner no Visual Studio de 2017 fornece a capacidade de incluir tudo o que você deseja em seu ambiente de aplicativo, conforme mostrado na Figura 4-4. Desde que esteja executando-o em um contêiner, se você adicionar uma dependência ao seu aplicativo, você pode incluir a dependência na imagem Dockerfile ou Docker.

Como também é mostrado na Figura 4-4, o fluxo de publicação envia uma imagem por meio de um registro de contêiner. Isso pode ser o registro de contêiner do Azure (um registro Fechar para suas implantações no Azure e protegido por contas e grupos do Active Directory do Azure), ou qualquer outro registro de Docker, como o Hub do Docker ou um registro de local.


>[!div class="step-by-step"]
[Anterior] (index.md) [Avançar] (docker-aplicativo-estado-data.md)
