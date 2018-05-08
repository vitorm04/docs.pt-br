---
title: 'Como: Recuperar informações como somente leitura'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: dd3a510339bca8649f5654d00a9cbdfba156d92c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
