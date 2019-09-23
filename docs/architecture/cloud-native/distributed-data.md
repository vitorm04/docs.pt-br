---
title: Dados distribuídos
description: Arquitetando aplicativos .NET nativos da nuvem para o Azure | Dados distribuídos para aplicativos nativos de nuvem
ms.date: 06/30/2019
ms.openlocfilehash: 92086c52b02360e90461aea9ad23a2068224e187
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183129"
---
# <a name="distributed-data-for-cloud-native-apps"></a>Dados distribuídos para aplicativos nativos de nuvem

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Ao construir um sistema nativo de nuvem que consiste em muitos microservices independentes, a maneira de pensar sobre as alterações de armazenamento de dados.

Os aplicativos monolíticos tradicionais favorecem um armazenamento de dados centralizado mostrado na Figura 5-1. 

![Banco de dados monolítico único](./media/single-monolithic-database.png)

**Figura 5-1**. Banco de dados monolítico único

Observe na figura anterior como todos os componentes do aplicativo consomem um único banco de dados relacional.

Há muitos benefícios para essa abordagem. É simples consultar dados espalhados por várias tabelas, e é simples implementar [Transações ACID](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) que garantam a consistência dos dados. Você sempre acaba com a *consistência imediata*: todas as atualizações de dados ou nenhuma delas.

Os sistemas nativos de nuvem favorecem uma arquitetura de dados mostrada na Figura 5-2, na qual cada microserviço possui e encapsula seus próprios dados.

![Vários bancos de dados em microserviços](./media/data-across-microservices.png)

**Figura 5-2**. Vários bancos de dados em microserviços

Observe como, na figura anterior, cada microserviço possui e encapsula o armazenamento de dados de ti e expõe apenas dados para o mundo exterior de sua API pública.
 
Esse modelo permite que cada microserviço evolua independentemente sem a necessidade de coordenar as alterações de esquema de dados com outros microserviços. Cada microserviço é gratuito para implementar o tipo de armazenamento de dados (banco de dados relacional, banco de dados de documentos, repositório de chave-valor) que melhor atenda às suas necessidades. Em tempo de execução, cada microserviço pode dimensionar seus dados de forma adequada. Isso é mostrado na Figura 5-3:

![Persistência de dados poliglota](./media/polyglot-data-persistence.png)

**Figura 5-3**. Persistência de dados poliglota

Observe como, na figura anterior, o catálogo de produtos e os microserviços de inventário adotam bancos de dados relacionais, o microserviço de pedidos, um banco de dados de documentos NoSql e o microserviço do carrinho de compras, que é um repositório de chave-valor externo. Embora os bancos de dados relacionais permaneçam relevantes para os microserviços com os complexos, eles ganharam uma popularidade considerável, fornecendo a adaptabilidade, pesquisa rápida e alta disponibilidade. Sua natureza sem esquema permite que os desenvolvedores se afastem de uma arquitetura de classes de dados tipadas e ORMs que tornam a alteração cara e demorada.

>[!div class="step-by-step"]
>[Anterior](service-mesh-communication-infrastructure.md)
>[Próximo](data-patterns.md)
