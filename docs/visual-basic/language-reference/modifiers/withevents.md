---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 41d38dcb3f44ccda19253adcd39401b0ac8dfb02
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647649"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="256a1-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="256a1-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="256a1-103">Especifica que um ou mais variáveis de membro declaradas se referem a uma instância de uma classe que pode gerar eventos.</span><span class="sxs-lookup"><span data-stu-id="256a1-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="256a1-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="256a1-104">Remarks</span></span>  
 <span data-ttu-id="256a1-105">Quando uma variável é definida usando `WithEvents`, você pode especificar declarativamente que um método trata os eventos da variável usando o `Handles` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="256a1-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>  
  
 <span data-ttu-id="256a1-106">Você pode usar `WithEvents` apenas no nível de classe ou módulo.</span><span class="sxs-lookup"><span data-stu-id="256a1-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="256a1-107">Isso significa que o contexto da declaração para um `WithEvents` variável deve ser uma classe ou módulo e não pode ser um arquivo de origem, namespace, estrutura ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="256a1-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>  
  
 <span data-ttu-id="256a1-108">Não é possível usar `WithEvents` em um membro da estrutura.</span><span class="sxs-lookup"><span data-stu-id="256a1-108">You cannot use `WithEvents` on a structure member.</span></span>  
  
 <span data-ttu-id="256a1-109">Você pode declarar apenas variáveis individuais — não matrizes — com `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="256a1-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="256a1-110">Regras</span><span class="sxs-lookup"><span data-stu-id="256a1-110">Rules</span></span>  
  
- <span data-ttu-id="256a1-111">**Tipos de elemento.**</span><span class="sxs-lookup"><span data-stu-id="256a1-111">**Element Types.**</span></span> <span data-ttu-id="256a1-112">Você deve declarar `WithEvents` variáveis sejam variáveis de objeto para que eles possam aceitar instâncias de classe.</span><span class="sxs-lookup"><span data-stu-id="256a1-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="256a1-113">No entanto, você não pode declará-los como `Object`.</span><span class="sxs-lookup"><span data-stu-id="256a1-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="256a1-114">Você deve declará-los como a classe específica que pode gerar eventos.</span><span class="sxs-lookup"><span data-stu-id="256a1-114">You must declare them as the specific class that can raise the events.</span></span>  
  
 <span data-ttu-id="256a1-115">O `WithEvents` modificador pode ser usado neste contexto: [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="256a1-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="256a1-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="256a1-116">See also</span></span>

- [<span data-ttu-id="256a1-117">Handles</span><span class="sxs-lookup"><span data-stu-id="256a1-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="256a1-118">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="256a1-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="256a1-119">Eventos</span><span class="sxs-lookup"><span data-stu-id="256a1-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
