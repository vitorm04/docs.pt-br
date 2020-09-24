---
title: Personalizando operações usando procedimentos armazenados exclusivamente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 78db5cf448a19056d7265ab84d97d055748c3faa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164318"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="9fc10-102">Personalizando operações usando procedimentos armazenados exclusivamente</span><span class="sxs-lookup"><span data-stu-id="9fc10-102">Customizing Operations by Using Stored Procedures Exclusively</span></span>

<span data-ttu-id="9fc10-103">Acesso a dados usando somente procedimentos armazenados é um cenário comum.</span><span class="sxs-lookup"><span data-stu-id="9fc10-103">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fc10-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9fc10-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9fc10-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="9fc10-105">Description</span></span>  

 <span data-ttu-id="9fc10-106">Você pode modificar o exemplo fornecido em [Personalizando operações usando procedimentos armazenados](customizing-operations-by-using-stored-procedures.md) substituindo até mesmo a primeira consulta (o que causa a execução SQL dinâmica) com uma chamada de método que encapsula um procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="9fc10-106">You can modify the example provided in [Customizing Operations By Using Stored Procedures](customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="9fc10-107">Suponha `CustomersByCity` é o método, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="9fc10-107">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9fc10-108">Código</span><span class="sxs-lookup"><span data-stu-id="9fc10-108">Code</span></span>  

 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="9fc10-109">O código a seguir executa sem nenhum SQL dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="9fc10-109">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="9fc10-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="9fc10-110">See also</span></span>

- [<span data-ttu-id="9fc10-111">Responsabilidades do desenvolvedor em substituir o comportamento padrão</span><span class="sxs-lookup"><span data-stu-id="9fc10-111">Responsibilities of the Developer In Overriding Default Behavior</span></span>](responsibilities-of-the-developer-in-overriding-default-behavior.md)
