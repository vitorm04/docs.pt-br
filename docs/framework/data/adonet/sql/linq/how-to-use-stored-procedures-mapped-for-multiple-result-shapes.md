---
title: 'Como: Use os procedimentos armazenados mapeados para várias formas de resultado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 065e866ec5937c4af31c0b1563a7582cb4112eba
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003277"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a>Como: Use os procedimentos armazenados mapeados para várias formas de resultado
Quando um procedimento armazenado pode retornar várias formas de resultado, o tipo de retorno não pode ser fortemente tipado a uma única forma de projeção. Embora [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] possa gerar todos os tipos de projeção possíveis, não é possível saber a ordem na qual eles serão retornados.  
  
 Compare este cenário com procedimentos armazenados que gerenciar várias formas de resultado seqüencialmente. Para obter mais informações, consulte [como: usar procedimentos armazenados mapeados para formas de resultados sequenciais](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).  
  
 O atributo de <xref:System.Data.Linq.Mapping.ResultTypeAttribute> é aplicado aos procedimentos armazenados que vários tipos de retorno de resultado para especificar o conjunto de tipos podem retornar o procedimento.  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 No exemplo de código SQL, a forma de resultado depende de entrada (`shape =1` ou `shape = 2`). Você não sabe que projeção será retornada primeiro.  
  
``` sql
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 Você usaria código semelhante ao seguinte para executar este procedimento armazenado.  
  
> [!NOTE]
> Você deve usar o padrão de <xref:System.Data.Linq.IMultipleResults.GetResult%2A> para obter um enumerador do tipo correto, com base no seu conhecimento do procedimento armazenado.  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos armazenados](stored-procedures.md)
