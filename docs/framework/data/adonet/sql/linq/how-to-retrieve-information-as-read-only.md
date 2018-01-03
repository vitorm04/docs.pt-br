---
title: "Como: Recuperar informações como somente leitura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 04a20a06cd8ed8785b37bdc604a817b475f93873
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-information-as-read-only"></a>Como: Recuperar informações como somente leitura
Quando você não pretende modificar os dados, você pode aumentar o desempenho de consultas buscando resultados somente leitura.  
  
 Você implementar o processamento somente leitura <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> definindo a `false`.  
  
> [!NOTE]
>  Quando <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> é definido como `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> é definido implicitamente a `false`.  
  
## <a name="example"></a>Exemplo  
 O código a seguir recupera uma coleção somente leitura de datas de admissão de funcionários.  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Consultando o banco de dados](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 [Carregamento adiado versus imediato](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
