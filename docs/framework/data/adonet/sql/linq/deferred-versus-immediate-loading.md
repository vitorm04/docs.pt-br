---
title: Adiado contra a carga immediate
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1d7247f-a3b7-460b-b342-5c1a2365aa1a
ms.openlocfilehash: 5955d7361658c825c120e62e531b72d402a12650
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="deferred-versus-immediate-loading"></a>Adiado contra a carga immediate
Quando você consulta para um objeto, você só retorna o objeto que você solicitou. O *relacionados* objetos não são buscados automaticamente ao mesmo tempo. (Para obter mais informações, consulte [consulta entre relações](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).) Você não pode ver o fato de que os objetos relacionados não são carregados já, porque uma tentativa de acessar gerencia uma solicitação que recupere-os.  
  
 Por exemplo, convém consultar um conjunto específico de pedidos e apenas ocasionalmente enviar uma notificação por email aos clientes específicos. Você não precisará necessariamente inicialmente de recuperar todos os dados do cliente com cada pedido. Você pode usar o carregamento adiada para adiar a recuperação de informações extras até que você tenha que absolutamente. Considere o exemplo a seguir:  
  
 [!code-csharp[DLinqQueryConcepts#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#1)]
 [!code-vb[DLinqQueryConcepts#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#1)]  
  
 O oposto também pode ser true. Você pode ter um aplicativo que tenha que exibir o cliente e ordenação dados ao mesmo tempo. Você conhece-o necessidade dois conjuntos de dados. Você sabe suas informações de ordem das necessidades do aplicativo para cada cliente para que você obter os resultados. Você não deve enviar para consultas individuais de pedidos para cada cliente. O que você deseja realmente é recuperar os dados de pedidos juntamente com os clientes.  
  
 [!code-csharp[DLinqQueryConcepts#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#2)]
 [!code-vb[DLinqQueryConcepts#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#2)]  
  
 Você também pode associar à clientes e pedidos em uma consulta formando entre o produto e recuperar todos os bits de dados relacionados como uma grande projeção. Mas esses resultados não são entidades. (Para obter mais informações, consulte [o LINQ no modelo de objeto SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)). As entidades são objetos que possuem a identidade e que você pode alterar, enquanto esses resultados seriam as projeções que não podem ser modificadas e persistente. Ainda pior, você poderia ser recuperando lotes de dados redundantes como as repetições de cada cliente para cada ordem em aplainado se associam a saída.  
  
 O que você precisa realmente é uma maneira para recuperar ao mesmo tempo um conjunto de objetos relacionados. O conjunto é uma seção delineado de um gráfico de modo que você nunca está recuperando mais ou menos que foi necessário para seu uso pretendido. Para essa finalidade, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece <xref:System.Data.Linq.DataLoadOptions> para carregamento imediato de uma região do seu modelo de objeto. Os métodos incluem:  
  
-   O método de <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> , imediatamente para carregar os dados relacionados ao destino principal.  
  
-   O método de <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> , para filtrar os objetos recuperados para um relacionamento específico.  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
