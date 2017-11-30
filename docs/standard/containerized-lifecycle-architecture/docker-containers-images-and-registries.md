---
title: "Registros, imagens e contêineres do docker"
description: "Ciclo de vida de aplicativo de Docker em contêineres com ferramentas e plataformas da Microsoft"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: b115b25d8ae335aafbe41bac0d694170be7e3c49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="docker-containers-images-and-registries"></a>Registros, imagens e contêineres do docker

Ao usar o Docker, você cria um aplicativo ou serviço e pacote ele e suas dependências em uma imagem de contêiner. Uma imagem é uma representação estática do aplicativo ou serviço e a configuração e as dependências.

Para executar o aplicativo ou serviço, a imagem do aplicativo é instanciada para criar um contêiner, que serão executados no host do Docker. Inicialmente, contêineres são testados em um ambiente de desenvolvimento ou de um computador.

Você pode armazenar imagens em um registro, que atua como uma biblioteca de imagens. Ao implantar o orchestrators de produção, é necessário um registro. Docker mantém um registro público via [Docker Hub](https://hub.docker.com/); outros fornecedores fornecem os registros para diferentes coleções de imagens. Como alternativa, as empresas podem ter um registro privado no local para suas próprias imagens do Docker.

Figura 1-4 mostra como imagens e registros no Docker se relacionam com outros componentes. Ele também mostra as várias ofertas de registro de fornecedores.

![](./media/image4.png)

Figura 1-4: taxonomia Docker termos e conceitos

Ao colocar imagens em um registro, você pode armazenar bits de aplicativo estático e imutável, incluindo todas as suas dependências, em um nível de estrutura. Você pode versão e implantar imagens em vários ambientes e, portanto, fornecem uma unidade de implantação consistente.

Registros de imagem privada, hospedado no local ou na nuvem, são recomendados para as seguintes situações:

-   As imagens não devem ser compartilhadas publicamente devido a confidencialidade.

-   Você deseja ter a latência de rede mínima entre as imagens e o ambiente de implantação escolhida. Por exemplo, se seu ambiente de produção é o Azure, você provavelmente desejará armazenar as imagens no registro de contêiner do Azure para que a latência de rede será mínima. De maneira semelhante, se seu ambiente de produção for local, convém ter um local registro confiável do Docker disponíveis na mesma rede local.

>[!div class="step-by-step"]
[Anterior] (docker-terminology.md) [Avançar] (Docker-aplicativo-ciclo de vida/index.md)
