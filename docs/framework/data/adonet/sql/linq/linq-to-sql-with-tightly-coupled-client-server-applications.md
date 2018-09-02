---
title: LINQ to SQL com aplicativos Apertado- agrupados do servidor cliente
ms.date: 03/30/2017
ms.assetid: e083d805-dcf6-459d-b9af-9ef0563f2dd7
ms.openlocfilehash: 9c36fc1f402d3791611af47a3a6d997db4f31167
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408954"
---
# <a name="linq-to-sql-with-tightly-coupled-client-server-applications"></a>LINQ to SQL com aplicativos Apertado- agrupados do servidor cliente
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pode ser usado na camada intermediária com clientes de inteligentes apertado-agrupados na camada de apresentação. Em cenários que não envolvem acesso a dados somente leitura, a nenhuma verificação de concorrência otimista, ou concorrência otimista com os carimbos de data/hora, não há muito mais complexidade do que com cenários de não remoto. No entanto, quando uma base de dados requer verificação de simultaneidade otimista com valores originais, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não fornece o nível de suporte para fazer ide de dados que que você localiza em datasets. No entanto, uma camada intermediária de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pode trocar dados com clientes em qualquer plataforma.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] no [!INCLUDE[vs_orcas_long](../../../../../../includes/vs-orcas-long-md.md)] não fornece nenhuma infraestrutura para controlar o estado de entidade depois que eles foram serializados para um cliente. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Habilita arquiteturas orientadas a serviços onde as interações entre as camadas de dados e a apresentação são pequenos e relativamente atômicas, mas não realiza nenhum redondo-tropeço de valores originais. Portanto, se você desejar usar um cliente inteligente apertado- acoplado com [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], e uma concorrência otimista com valores originais, você usos de base de dados precisará implementar seu próprio mecanismo para alterações de comunicação entre a camada de apresentação e a camada intermediária. Depende o designer do sistema para decidir se faz sentido fazer isso bit de trabalho extra de troca de benefícios que fornece [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] na camada intermediária. Por outro lado, se o base de dados tem data/hora, não há necessidade de lógica personalizada de controle de alterações.  
  
## <a name="see-also"></a>Consulte também  
 [Aplicativos de N camadas e remotos com o LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [LINQ to SQL de N camadas com serviços Web](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
 [Trabalhando com conjuntos de dados em aplicativos de N camadas](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)
