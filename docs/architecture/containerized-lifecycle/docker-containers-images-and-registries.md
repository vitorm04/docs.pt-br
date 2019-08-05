---
title: Registros, imagens e contêineres do Docker
description: Saiba o importante papel geral desempenhado pelos registros no modo como o Docker implanta aplicativos.
ms.date: 02/15/2019
ms.openlocfilehash: 7becadc3de16d96f8d6f167cf49c6cdd3bcc0d32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68673513"
---
# <a name="docker-containers-images-and-registries"></a>Registros, imagens e contêineres do Docker

Ao usar o Docker, você cria um aplicativo ou serviço e empacota a ele e suas dependências em uma imagem de contêiner. Uma imagem é uma representação estática do aplicativo ou do serviço e de sua configuração e dependências.

Para executar o aplicativo ou o serviço, uma instância da imagem do aplicativo é criada para criar um contêiner, que estará em execução no host do Docker. Inicialmente, os contêineres são testados em um ambiente de desenvolvimento ou em um computador.

Você armazena imagens em um registro que atua como uma biblioteca de imagens. É necessário um registro ao implantar em orquestradores de produção. O Docker mantém um Registro público por meio do [Hub do Docker](https://hub.docker.com/); outros fornecedores fornecem os Registros para diferentes coleções de imagens, incluindo [Registro de Contêiner do Azure](https://azure.microsoft.com/services/container-registry/). Como alternativa, as empresas podem ter um Registro privado local para suas próprias imagens do Docker.

A Figura 1-4 mostra como imagens e registros no Docker se relacionam com outros componentes. Ela também mostra as várias ofertas de Registro dos fornecedores.

![Taxonomia básica no Docker: o Registro é como uma estante de livros em que as imagens são armazenadas e ficam disponíveis para serem retiradas para a criação de contêineres para executar os serviços ou aplicativos Web. Há registros do Docker privados locais e na nuvem pública. O Hub do Docker é um registro público mantido pelo Docker, junto com o Registro Confiável do Docker, uma solução empresarial, o Azure oferece ao Registro de Contêiner do Azure. AWS, Google e outros também têm Registros de contêiner.](./media/image4.png)

**Figura 1-4**. Taxonomia de termos e conceitos do Docker

Colocar imagens em um registro permite armazenar os bits de aplicativo estáticos e imutáveis, incluindo todas as suas dependências em um nível de estrutura. A versão dessas imagens pode ser controlada e elas podem ser implantadas em vários ambientes e, portanto, fornecem uma unidade de implantação consistente.

Registros de imagem privados, hospedados localmente ou na nuvem, são recomendados quando:

- Suas imagens não devem ser compartilhadas publicamente devido à confidencialidade.

- Você deseja ter latência de rede mínima entre suas imagens e o ambiente de implantação escolhido. Por exemplo, se o ambiente de produção for o Azure, você provavelmente desejará armazenar as imagens no [Registro de Contêiner do Azure](https://azure.microsoft.com/services/container-registry/) para que a latência de rede seja mínima. De maneira semelhante, se seu ambiente de produção for local, tenha um Registro Confiável do Docker local disponível na mesma rede local.

>[!div class="step-by-step"]
>[Anterior](docker-terminology.md)
>[Próximo](road-to-modern-applications-based-on-containers.md)
