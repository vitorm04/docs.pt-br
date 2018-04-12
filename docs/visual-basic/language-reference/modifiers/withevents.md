---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68a58fd130c04f2ed0cb1f2e5b9250f6c85f120d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="09695-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09695-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="09695-103">Especifica que uma ou mais variáveis de membro declaradas referem-se a uma instância de uma classe que pode gerar eventos.</span><span class="sxs-lookup"><span data-stu-id="09695-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09695-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="09695-104">Remarks</span></span>  
 <span data-ttu-id="09695-105">Quando uma variável é definida usando `WithEvents`, você pode especificar declarativamente que um método trata os eventos da variável usando a `Handles` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="09695-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>  
  
 <span data-ttu-id="09695-106">Você pode usar `WithEvents` apenas no nível de classe ou módulo.</span><span class="sxs-lookup"><span data-stu-id="09695-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="09695-107">Isso significa que o contexto da declaração para um `WithEvents` variável deve ser uma classe ou um módulo e não pode ser um arquivo de origem, namespace, estrutura ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="09695-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>  
  
 <span data-ttu-id="09695-108">Não é possível usar `WithEvents` em um membro da estrutura.</span><span class="sxs-lookup"><span data-stu-id="09695-108">You cannot use `WithEvents` on a structure member.</span></span>  
  
 <span data-ttu-id="09695-109">Você pode declarar apenas variáveis individuais — não matrizes — com `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="09695-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="09695-110">Regras</span><span class="sxs-lookup"><span data-stu-id="09695-110">Rules</span></span>  
  
-   <span data-ttu-id="09695-111">**Tipos de elemento.**</span><span class="sxs-lookup"><span data-stu-id="09695-111">**Element Types.**</span></span> <span data-ttu-id="09695-112">Você deve declarar `WithEvents` variáveis como variáveis de objeto para que eles podem aceitar instâncias de classe.</span><span class="sxs-lookup"><span data-stu-id="09695-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="09695-113">No entanto, você não pode declará-los como `Object`.</span><span class="sxs-lookup"><span data-stu-id="09695-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="09695-114">Você deve declará-los como a classe específica que pode gerar eventos.</span><span class="sxs-lookup"><span data-stu-id="09695-114">You must declare them as the specific class that can raise the events.</span></span>  
  
 <span data-ttu-id="09695-115">O `WithEvents` modificador pode ser usado neste contexto: [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="09695-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09695-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09695-116">See Also</span></span>  
 [<span data-ttu-id="09695-117">Handles</span><span class="sxs-lookup"><span data-stu-id="09695-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="09695-118">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="09695-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="09695-119">Eventos</span><span class="sxs-lookup"><span data-stu-id="09695-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
