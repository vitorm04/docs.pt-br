---
title: Personalizando operações usando procedimentos armazenados exclusivamente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 3c60a9e430b4228117fd03a43a30f27342154b1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357508"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="1d7e2-102">Personalizando operações usando procedimentos armazenados exclusivamente</span><span class="sxs-lookup"><span data-stu-id="1d7e2-102">Customizing Operations by Using Stored Procedures Exclusively</span></span>
<span data-ttu-id="1d7e2-103">Acesso a dados usando somente procedimentos armazenados é um cenário comum.</span><span class="sxs-lookup"><span data-stu-id="1d7e2-103">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d7e2-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1d7e2-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="1d7e2-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d7e2-105">Description</span></span>  
 <span data-ttu-id="1d7e2-106">Você pode modificar o exemplo fornecido em [personalizando operações, usando procedimentos armazenados](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) , substituindo até a primeira consulta (que faz a execução de SQL dinâmica) por uma chamada de método que encapsula um procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="1d7e2-106">You can modify the example provided in [Customizing Operations By Using Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="1d7e2-107">Suponha `CustomersByCity` é o método, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1d7e2-107">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1d7e2-108">Código</span><span class="sxs-lookup"><span data-stu-id="1d7e2-108">Code</span></span>  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="1d7e2-109">O código a seguir executa sem nenhum SQL dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="1d7e2-109">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="1d7e2-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d7e2-110">See Also</span></span>  
 [<span data-ttu-id="1d7e2-111">Responsabilidades do desenvolvedor em substituir o comportamento padrão</span><span class="sxs-lookup"><span data-stu-id="1d7e2-111">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
