---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 240058a534456ae20c9c129a068bae575ac45eda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596002"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="55ecc-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55ecc-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="55ecc-103">Especifica que uma ou mais variáveis de membro declaradas referem-se a uma instância de uma classe que pode gerar eventos.</span><span class="sxs-lookup"><span data-stu-id="55ecc-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55ecc-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="55ecc-104">Remarks</span></span>  
 <span data-ttu-id="55ecc-105">Quando uma variável é definida usando `WithEvents`, você pode especificar declarativamente que um método trata os eventos da variável usando a `Handles` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="55ecc-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>  
  
 <span data-ttu-id="55ecc-106">Você pode usar `WithEvents` apenas no nível de classe ou módulo.</span><span class="sxs-lookup"><span data-stu-id="55ecc-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="55ecc-107">Isso significa que o contexto da declaração para um `WithEvents` variável deve ser uma classe ou um módulo e não pode ser um arquivo de origem, namespace, estrutura ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="55ecc-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>  
  
 <span data-ttu-id="55ecc-108">Não é possível usar `WithEvents` em um membro da estrutura.</span><span class="sxs-lookup"><span data-stu-id="55ecc-108">You cannot use `WithEvents` on a structure member.</span></span>  
  
 <span data-ttu-id="55ecc-109">Você pode declarar apenas variáveis individuais — não matrizes — com `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="55ecc-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="55ecc-110">Regras</span><span class="sxs-lookup"><span data-stu-id="55ecc-110">Rules</span></span>  
  
-   <span data-ttu-id="55ecc-111">**Tipos de elemento.**</span><span class="sxs-lookup"><span data-stu-id="55ecc-111">**Element Types.**</span></span> <span data-ttu-id="55ecc-112">Você deve declarar `WithEvents` variáveis como variáveis de objeto para que eles podem aceitar instâncias de classe.</span><span class="sxs-lookup"><span data-stu-id="55ecc-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="55ecc-113">No entanto, você não pode declará-los como `Object`.</span><span class="sxs-lookup"><span data-stu-id="55ecc-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="55ecc-114">Você deve declará-los como a classe específica que pode gerar eventos.</span><span class="sxs-lookup"><span data-stu-id="55ecc-114">You must declare them as the specific class that can raise the events.</span></span>  
  
 <span data-ttu-id="55ecc-115">O `WithEvents` modificador pode ser usado neste contexto: [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="55ecc-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55ecc-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55ecc-116">See Also</span></span>  
 [<span data-ttu-id="55ecc-117">Handles</span><span class="sxs-lookup"><span data-stu-id="55ecc-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="55ecc-118">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="55ecc-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="55ecc-119">Eventos</span><span class="sxs-lookup"><span data-stu-id="55ecc-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
