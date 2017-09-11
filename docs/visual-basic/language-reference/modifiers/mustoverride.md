---
title: MustOverride (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.MustOverride
- MustOverride
dev_langs:
- VB
helpviewer_keywords:
- virtual elements, pure
- elements, pure virtual
- properties [Visual Basic], redefining
- procedures, overriding
- overriding, MustOverride keyword
- procedures, redefining
- pure virtual elements
- MustOverride keyword
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
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
ms.openlocfilehash: 7f349971f8890bccac027c4bdcce1764be89d2b8
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="818c9-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="818c9-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="818c9-103">Especifica que uma propriedade ou um procedimento não é implementado dessa classe e deve ser substituído em uma classe derivada antes de ser usada.</span><span class="sxs-lookup"><span data-stu-id="818c9-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="818c9-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="818c9-104">Remarks</span></span>  
 <span data-ttu-id="818c9-105">Você pode usar `MustOverride` somente na declaração de uma propriedade ou um procedimento.</span><span class="sxs-lookup"><span data-stu-id="818c9-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="818c9-106">A propriedade ou procedimento que especifica `MustOverride` deve ser um membro de uma classe, e a classe deve ser marcada como [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="818c9-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="818c9-107">Regras</span><span class="sxs-lookup"><span data-stu-id="818c9-107">Rules</span></span>  
  
-   <span data-ttu-id="818c9-108">**Declaração incompleta.**</span><span class="sxs-lookup"><span data-stu-id="818c9-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="818c9-109">Quando você especifica `MustOverride`, você não fornecer quaisquer linhas adicionais de código para a propriedade ou procedimento, não até o `End Function`, `End Property`, ou `End Sub` instrução.</span><span class="sxs-lookup"><span data-stu-id="818c9-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="818c9-110">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="818c9-110">**Combined Modifiers.**</span></span> <span data-ttu-id="818c9-111">Não é possível especificar `MustOverride` junto com `NotOverridable`, `Overridable`, ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="818c9-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
-   <span data-ttu-id="818c9-112">**Sombreamento e sobreposição.**</span><span class="sxs-lookup"><span data-stu-id="818c9-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="818c9-113">Tanto o sombreamento e sobreposição redefinem um elemento herdado, mas há diferenças significativas entre as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="818c9-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="818c9-114">Para obter mais informações, consulte [sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="818c9-114">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
-   <span data-ttu-id="818c9-115">**Termos alternativos.**</span><span class="sxs-lookup"><span data-stu-id="818c9-115">**Alternate Terms.**</span></span> <span data-ttu-id="818c9-116">Um elemento que não pode ser usado, exceto em uma substituição às vezes é chamado um *puro virtual* elemento.</span><span class="sxs-lookup"><span data-stu-id="818c9-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="818c9-117">O `MustOverride` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="818c9-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="818c9-118">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="818c9-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="818c9-119">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="818c9-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="818c9-120">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="818c9-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="818c9-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="818c9-121">See Also</span></span>  
 <span data-ttu-id="818c9-122">[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) </span><span class="sxs-lookup"><span data-stu-id="818c9-122">[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) </span></span>  
<span data-ttu-id="818c9-123"> [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md) </span><span class="sxs-lookup"><span data-stu-id="818c9-123"> [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) </span></span>  
<span data-ttu-id="818c9-124"> [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md) </span><span class="sxs-lookup"><span data-stu-id="818c9-124"> [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md) </span></span>  
<span data-ttu-id="818c9-125"> [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md) </span><span class="sxs-lookup"><span data-stu-id="818c9-125"> [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md) </span></span>  
<span data-ttu-id="818c9-126"> [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="818c9-126"> [Keywords](../../../visual-basic/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="818c9-127"> [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)</span><span class="sxs-lookup"><span data-stu-id="818c9-127"> [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)</span></span>
