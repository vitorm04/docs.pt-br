---
title: 'Como: usar procedimentos armazenados mapeados para várias formas de resultado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: d32faf026789923ca4343271c9fd1b6bbdb068df
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793098"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a>Como: usar procedimentos armazenados mapeados para várias formas de resultado
Quando um procedimento armazenado pode retornar várias formas de resultado, o tipo de retorno não pode ser fortemente tipado a uma única forma de projeção. Embora [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] o possa gerar todos os tipos de projeção possíveis, ele não pode saber a ordem na qual eles serão retornados.  
  
 Compare este cenário com procedimentos armazenados que gerenciar várias formas de resultado seqüencialmente. Para obter mais informações, confira [Como: Use procedimentos armazenados mapeados para formas](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)de resultados sequenciais.  
  
 O atributo de <xref:System.Data.Linq.Mapping.ResultTypeAttribute> é aplicado aos procedimentos armazenados que vários tipos de retorno de resultado para especificar o conjunto de tipos podem retornar o procedimento.  
  
## <a name="example"></a>Exemplo  
 No exemplo de código SQL, a forma de resultado depende de entrada (`shape =1` ou `shape = 2`). Você não sabe que projeção será retornada primeiro.  
  
```  
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a>Exemplo  
 Você usaria código semelhante ao seguinte para executar este procedimento armazenado.  
  
> [!NOTE]
> Você deve usar o padrão de <xref:System.Data.Linq.IMultipleResults.GetResult%2A> para obter um enumerador do tipo correto, com base no seu conhecimento do procedimento armazenado.  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos armazenados](stored-procedures.md)
