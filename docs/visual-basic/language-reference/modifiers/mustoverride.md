---
title: MustOverride (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
ms.openlocfilehash: 5dabd90d29bc41d017436876af24a67fa87e8e17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599864"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="3d1ac-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d1ac-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="3d1ac-103">Especifica que uma propriedade ou procedimento não é implementado dessa classe e deve ser substituído em uma classe derivada antes que ele possa ser usado.</span><span class="sxs-lookup"><span data-stu-id="3d1ac-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d1ac-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="3d1ac-104">Remarks</span></span>  
 <span data-ttu-id="3d1ac-105">Você pode usar `MustOverride` somente na declaração de uma propriedade ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="3d1ac-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="3d1ac-106">A propriedade ou procedimento que especifica `MustOverride` deve ser um membro de uma classe, e a classe deve ser marcada como [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="3d1ac-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3d1ac-107">Regras</span><span class="sxs-lookup"><span data-stu-id="3d1ac-107">Rules</span></span>  
  
-   <span data-ttu-id="3d1ac-108">**Declaração incompleta.**</span><span class="sxs-lookup"><span data-stu-id="3d1ac-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="3d1ac-109">Quando você especifica `MustOverride`, você não fornecer quaisquer linhas adicionais de código para a propriedade ou procedimento, não até mesmo o `End Function`, `End Property`, ou `End Sub` instrução.</span><span class="sxs-lookup"><span data-stu-id="3d1ac-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="3d1ac-110">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="3d1ac-110">**Combined Modifiers.**</span></span> <span data-ttu-id="3d1ac-111">Não é possível especificar `MustOverride` junto com `NotOverridable`, `Overridable`, ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="3d1ac-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
-   <span data-ttu-id="3d1ac-112">**Sombreamento e sobreposição.**</span><span class="sxs-lookup"><span data-stu-id="3d1ac-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="3d1ac-113">Tanto o sombreamento e sobreposição redefinem um elemento herdado, mas há diferenças significativas entre as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="3d1ac-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="3d1ac-114">Para obter mais informações, consulte [sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="3d1ac-114">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
-   <span data-ttu-id="3d1ac-115">**Termos alternativos.**</span><span class="sxs-lookup"><span data-stu-id="3d1ac-115">**Alternate Terms.**</span></span> <span data-ttu-id="3d1ac-116">Um elemento que não pode ser usado, exceto em uma substituição às vezes é chamado um *puro virtual* elemento.</span><span class="sxs-lookup"><span data-stu-id="3d1ac-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="3d1ac-117">O `MustOverride` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="3d1ac-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="3d1ac-118">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="3d1ac-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="3d1ac-119">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="3d1ac-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="3d1ac-120">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="3d1ac-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="3d1ac-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d1ac-121">See Also</span></span>  
 [<span data-ttu-id="3d1ac-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="3d1ac-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="3d1ac-123">Substituível</span><span class="sxs-lookup"><span data-stu-id="3d1ac-123">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="3d1ac-124">Substituições</span><span class="sxs-lookup"><span data-stu-id="3d1ac-124">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="3d1ac-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="3d1ac-125">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [<span data-ttu-id="3d1ac-126">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="3d1ac-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="3d1ac-127">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3d1ac-127">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
