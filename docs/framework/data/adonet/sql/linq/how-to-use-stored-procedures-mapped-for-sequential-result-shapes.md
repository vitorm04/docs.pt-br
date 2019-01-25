---
title: 'Como: Use os procedimentos armazenados mapeados para formas sequenciais de resultado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: 296870029d2329640466b3a540e9057738173aa3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495650"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a>Como: Use os procedimentos armazenados mapeados para formas sequenciais de resultado
Esse tipo de procedimento armazenado pode gerar mais de uma forma de resultado, mas você souber ordem em que os resultados são retornados. Compare este cenário com o cenário onde você não souber a sequência de retorna. Para obter mais informações, confira [Como: Use os procedimentos armazenados mapeados para várias formas de resultado](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).  
  
## <a name="example"></a>Exemplo  
 Aqui está T-SQL de um procedimento armazenado que retorna várias formas de resultado em seqüência:  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a>Exemplo  
 Você usaria código semelhante ao seguinte para executar este procedimento armazenado.  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>Consulte também
- [Procedimentos armazenados](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
