---
title: LINQ to SQL com aplicativos Apertado- agrupados do servidor cliente
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e083d805-dcf6-459d-b9af-9ef0563f2dd7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a2fa902cfbea3c6eb15e1832231bb3ed83de5497
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="linq-to-sql-with-tightly-coupled-client-server-applications"></a>LINQ to SQL com aplicativos Apertado- agrupados do servidor cliente
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]pode ser usado na camada intermediária com clientes inteligentes estreitamente ligado na camada de apresentação. Em cenários que não envolvem acesso a dados somente leitura, a nenhuma verificação de concorrência otimista, ou concorrência otimista com os carimbos de data/hora, não há muito mais complexidade do que com cenários de não remoto. No entanto, quando uma base de dados requer verificação de simultaneidade otimista com valores originais, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não fornece o nível de suporte para fazer ide de dados que que você localiza em datasets. No entanto, uma camada intermediária de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pode trocar dados com clientes em qualquer plataforma.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]em [!INCLUDE[vs_orcas_long](../../../../../../includes/vs-orcas-long-md.md)] não fornece nenhuma infraestrutura para controlar o estado de entidade depois que eles tiverem sido serializados em um cliente. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Habilita arquiteturas orientadas a serviços em que as interações entre as camadas de apresentação e de dados são pequenos e relativamente atômica, mas não executa qualquer ciclo de valores originais. Portanto, se você desejar usar um cliente inteligente apertado- acoplado com [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], e uma concorrência otimista com valores originais, você usos de base de dados precisará implementar seu próprio mecanismo para alterações de comunicação entre a camada de apresentação e a camada intermediária. Depende o designer do sistema para decidir se faz sentido fazer isso bit de trabalho extra de troca de benefícios que fornece [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] na camada intermediária. Por outro lado, se o base de dados tem data/hora, não há necessidade de lógica personalizada de controle de alterações.  
  
## <a name="see-also"></a>Consulte também  
 [Aplicativos de N camadas e remotos com o LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [LINQ to SQL de N camadas com serviços Web](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
 [Trabalhando com conjuntos de dados em aplicativos de N camadas](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20)
