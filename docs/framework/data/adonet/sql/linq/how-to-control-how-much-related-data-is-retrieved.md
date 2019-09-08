---
title: 'Como: controlar quantos dados relacionados são recuperados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: 2112600dfcef65b1c85445b03806ce8e9cab6a27
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782060"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a>Como: controlar quantos dados relacionados são recuperados
Use o método de <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> para especificar que os dados relacionados ao destino de chave devem ser recuperados ao mesmo tempo. Por exemplo, se você souber você precisará informações sobre os pedidos de clientes, você pode usar <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> para certificar-se de que as informações do pedido é recuperada ao mesmo tempo que informações para o cliente. Essa abordagem resulta em apenas um processamento para o base de dados para ambos os conjuntos de informações.  
  
> [!NOTE]
> Você pode recuperar os dados relacionados ao destino principal da sua consulta recuperando entre um produto como uma grande projeção, como recuperar pedidos quando você seleciona clientes. Mas essa abordagem tem geralmente desvantagens. Por exemplo, os resultados são apenas projeções e não entidades que podem ser alteradas e persistidas [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]pelo. E você pode recuperar muitos dados que não são necessários.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, qualquer `Orders` para qualquer `Customers` que está localizado em Londres é recuperado quando a consulta é executada. Como resultado, o acesso são a propriedade de `Orders` em um objeto de `Customer` não dispara uma nova consulta de base de dados.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- [Consultando o banco de dados](querying-the-database.md)
