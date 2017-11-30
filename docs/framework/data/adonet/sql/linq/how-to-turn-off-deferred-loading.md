---
title: 'Como: Desativar a carga adiada'
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
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d98b190ef4454ff29318eb6ef0f20624c85b62a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-turn-off-deferred-loading"></a>Como: Desativar a carga adiada
Você pode desativar a carga adiada definindo <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> a `false`. Para obter mais informações, consulte [adiado contra Carregando imediata](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
> [!NOTE]
>  A carga adiada é desativada implicitamente quando o rastreamento de objeto é desativado. Para obter mais informações, consulte [como: recuperar informações como somente leitura](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como desativar a carga adiada definindo <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> a `false`.  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Consultando o banco de dados](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
