---
title: "Registros, imagens e contêineres do docker"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Registros, imagens e contêineres do docker"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 224fed34f06d10760b14aa9ecbae6c0e912915cf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="docker-containers-images-and-registries"></a>Registros, imagens e contêineres do docker

Ao usar o Docker, um desenvolvedor cria um aplicativo ou serviço e pacotes-lo e suas dependências em uma imagem de contêiner. Uma imagem é uma representação estática do aplicativo ou serviço e a configuração e as dependências.

Para executar o aplicativo ou serviço, a imagem do aplicativo é instanciada para criar um contêiner, que serão executados no host do Docker. Inicialmente, contêineres são testados em um ambiente de desenvolvimento ou de um computador.

Os desenvolvedores devem armazenar imagens em um registro, que atua como uma biblioteca de imagens e é necessário ao implantar o orchestrators de produção. Docker mantém um registro público via [Docker Hub](https://hub.docker.com/); outros fornecedores fornecem os registros para diferentes coleções de imagens. Como alternativa, as empresas podem ter um registro privado no local para suas próprias imagens do Docker.

Figura 2-4 mostra como imagens e registros no Docker se relacionam com outros componentes. Ele também mostra as várias ofertas de registro de fornecedores.

![](./media/image5.PNG)

**Figura 2-4**. Taxonomia Docker termos e conceitos

Colocar imagens em um registro permite que você armazene os bits de aplicativo estático e imutável, incluindo todas as suas dependências em um nível de estrutura. Essas imagens podem ser implantado em vários ambientes e com controle de versão e, portanto, fornecem uma unidade de implantação consistente.

Registros de imagem privada hospedada no local ou na nuvem, são recomendados quando:

-   As imagens não devem ser compartilhadas publicamente devido a confidencialidade.

-   Você deseja ter a latência de rede mínima entre as imagens e o ambiente de implantação escolhida. Por exemplo, se seu ambiente de produção é uma nuvem do Azure, você provavelmente desejará armazenar as imagens no registro de contêiner do Azure para que a latência de rede será mínima. De maneira semelhante, se seu ambiente de produção for local, convém ter um local registro confiável do Docker disponíveis na mesma rede local.

>[!div class="step-by-step"]
[Anterior] (docker-terminology.md) [Avançar] (... /NET-Core-NET-Framework-Containers/index.MD)
