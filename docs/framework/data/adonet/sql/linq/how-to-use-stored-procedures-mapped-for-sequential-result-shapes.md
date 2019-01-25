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
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a><span data-ttu-id="0c79e-102">Como: Use os procedimentos armazenados mapeados para formas sequenciais de resultado</span><span class="sxs-lookup"><span data-stu-id="0c79e-102">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>
<span data-ttu-id="0c79e-103">Esse tipo de procedimento armazenado pode gerar mais de uma forma de resultado, mas você souber ordem em que os resultados são retornados.</span><span class="sxs-lookup"><span data-stu-id="0c79e-103">This kind of stored procedure can generate more than one result shape, but you know in what order the results are returned.</span></span> <span data-ttu-id="0c79e-104">Compare este cenário com o cenário onde você não souber a sequência de retorna.</span><span class="sxs-lookup"><span data-stu-id="0c79e-104">Contrast this scenario with the scenario where you do not know the sequence of the returns.</span></span> <span data-ttu-id="0c79e-105">Para obter mais informações, confira [Como: Use os procedimentos armazenados mapeados para várias formas de resultado](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="0c79e-105">For more information, see [How to: Use Stored Procedures Mapped for Multiple Result Shapes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c79e-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0c79e-106">Example</span></span>  
 <span data-ttu-id="0c79e-107">Aqui está T-SQL de um procedimento armazenado que retorna várias formas de resultado em seqüência:</span><span class="sxs-lookup"><span data-stu-id="0c79e-107">Here is the T-SQL of a stored procedure that returns multiple result shapes sequentially:</span></span>  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="0c79e-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0c79e-108">Example</span></span>  
 <span data-ttu-id="0c79e-109">Você usaria código semelhante ao seguinte para executar este procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="0c79e-109">You would use code similar to the following to execute this stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="0c79e-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c79e-110">See also</span></span>
- [<span data-ttu-id="0c79e-111">Procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="0c79e-111">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
