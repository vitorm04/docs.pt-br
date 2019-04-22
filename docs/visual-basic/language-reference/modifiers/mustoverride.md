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
ms.openlocfilehash: 0ddd7d0d2a57afc02aa7483ba5e83b65c48af534
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822811"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="792f4-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="792f4-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="792f4-103">Especifica que uma propriedade ou procedimento não está implementado nesta classe e deve ser substituído em uma classe derivada antes que ele pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="792f4-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="792f4-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="792f4-104">Remarks</span></span>  
 <span data-ttu-id="792f4-105">Você pode usar `MustOverride` somente em uma instrução de declaração de propriedade ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="792f4-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="792f4-106">A propriedade ou procedimento que especifica `MustOverride` deve ser um membro de uma classe, e a classe deve ser marcada [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="792f4-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="792f4-107">Regras</span><span class="sxs-lookup"><span data-stu-id="792f4-107">Rules</span></span>  
  
-   <span data-ttu-id="792f4-108">**Declaração incompleta.**</span><span class="sxs-lookup"><span data-stu-id="792f4-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="792f4-109">Quando você especifica `MustOverride`, você não fornecer quaisquer linhas adicionais de código para a propriedade ou procedimento, não até mesmo os `End Function`, `End Property`, ou `End Sub` instrução.</span><span class="sxs-lookup"><span data-stu-id="792f4-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="792f4-110">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="792f4-110">**Combined Modifiers.**</span></span> <span data-ttu-id="792f4-111">Não é possível especificar `MustOverride` junto com `NotOverridable`, `Overridable`, ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="792f4-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
-   <span data-ttu-id="792f4-112">**Sombreamento e sobreposição.**</span><span class="sxs-lookup"><span data-stu-id="792f4-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="792f4-113">Tanto o sombreamento e sobreposição redefinem um elemento herdado, mas há diferenças significativas entre as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="792f4-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="792f4-114">Para obter mais informações, consulte [sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="792f4-114">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
-   <span data-ttu-id="792f4-115">**Termos alternativos.**</span><span class="sxs-lookup"><span data-stu-id="792f4-115">**Alternate Terms.**</span></span> <span data-ttu-id="792f4-116">Um elemento que não pode ser usado, exceto em uma substituição às vezes é chamado um *pura virtual* elemento.</span><span class="sxs-lookup"><span data-stu-id="792f4-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="792f4-117">O `MustOverride` modificador pode ser usado nestes contextos:</span><span class="sxs-lookup"><span data-stu-id="792f4-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="792f4-118">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="792f4-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="792f4-119">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="792f4-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="792f4-120">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="792f4-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="792f4-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="792f4-121">See also</span></span>

- [<span data-ttu-id="792f4-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="792f4-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="792f4-123">Substituível</span><span class="sxs-lookup"><span data-stu-id="792f4-123">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="792f4-124">Substituições</span><span class="sxs-lookup"><span data-stu-id="792f4-124">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="792f4-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="792f4-125">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [<span data-ttu-id="792f4-126">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="792f4-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="792f4-127">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="792f4-127">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
