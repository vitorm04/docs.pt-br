---
title: WithEvents (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.WithEvents
- WithEvents
dev_langs:
- VB
helpviewer_keywords:
- WithEvents keyword
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b956f8f0d6f0a2fd9f41c5df6d6c82b43fa09018
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="withevents-visual-basic"></a><span data-ttu-id="b0db2-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0db2-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="b0db2-103">Especifica que uma ou mais variáveis de membro declaradas se referir a uma instância de uma classe que pode gerar eventos.</span><span class="sxs-lookup"><span data-stu-id="b0db2-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0db2-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="b0db2-104">Remarks</span></span>  
 <span data-ttu-id="b0db2-105">Quando uma variável é definida usando `WithEvents`, você pode especificar declarativamente que um método trata os eventos da variável usando a `Handles` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="b0db2-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>  
  
 <span data-ttu-id="b0db2-106">Você pode usar `WithEvents` somente no nível de classe ou módulo.</span><span class="sxs-lookup"><span data-stu-id="b0db2-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="b0db2-107">Isso significa que o contexto da declaração para um `WithEvents` variável deve ser uma classe ou módulo e não pode ser um arquivo fonte, namespace, estrutura ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="b0db2-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>  
  
 <span data-ttu-id="b0db2-108">Não é possível usar `WithEvents` em um membro de estrutura.</span><span class="sxs-lookup"><span data-stu-id="b0db2-108">You cannot use `WithEvents` on a structure member.</span></span>  
  
 <span data-ttu-id="b0db2-109">Você pode declarar apenas variáveis individuais — não matrizes — com `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="b0db2-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="b0db2-110">Regras</span><span class="sxs-lookup"><span data-stu-id="b0db2-110">Rules</span></span>  
  
-   <span data-ttu-id="b0db2-111">**Tipos de elemento.**</span><span class="sxs-lookup"><span data-stu-id="b0db2-111">**Element Types.**</span></span> <span data-ttu-id="b0db2-112">Você deve declarar `WithEvents` variáveis para serem variáveis de objeto para que eles possam aceitar instâncias de classe.</span><span class="sxs-lookup"><span data-stu-id="b0db2-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="b0db2-113">No entanto, você não pode declará-los como `Object`.</span><span class="sxs-lookup"><span data-stu-id="b0db2-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="b0db2-114">Você deve declará-los como a classe específica que pode lançar os eventos.</span><span class="sxs-lookup"><span data-stu-id="b0db2-114">You must declare them as the specific class that can raise the events.</span></span>  
  
 <span data-ttu-id="b0db2-115">O `WithEvents` modificador pode ser usado neste contexto: [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="b0db2-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0db2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0db2-116">See Also</span></span>  
 <span data-ttu-id="b0db2-117">[Identificadores](../../../visual-basic/language-reference/statements/handles-clause.md) </span><span class="sxs-lookup"><span data-stu-id="b0db2-117">[Handles](../../../visual-basic/language-reference/statements/handles-clause.md) </span></span>  
<span data-ttu-id="b0db2-118"> [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="b0db2-118"> [Keywords](../../../visual-basic/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="b0db2-119"> [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="b0db2-119"> [Events](../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
