---
title: Substituível (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: 91a1cedc66fd66e336b6e7976ad87ad638cb43c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053893"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="c39bb-102">Substituível (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c39bb-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="c39bb-103">Especifica que uma propriedade ou procedimento pode ser substituído por uma propriedade nomeada de forma idêntica ou procedimento em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c39bb-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c39bb-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="c39bb-104">Remarks</span></span>  
 <span data-ttu-id="c39bb-105">O `Overridable` modificador permite que uma propriedade ou método em uma classe seja substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c39bb-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="c39bb-106">O [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modificador impede que uma propriedade ou método que está sendo substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c39bb-106">The [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="c39bb-107">Para obter mais informações, consulte [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="c39bb-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="c39bb-108">Se o `Overridable` ou `NotOverridable` modificador não for especificado, a configuração padrão depende se a propriedade ou método substitui um método ou propriedade de classe base.</span><span class="sxs-lookup"><span data-stu-id="c39bb-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="c39bb-109">Se a propriedade ou método substitui um método ou propriedade de classe base, a configuração padrão é `Overridable`; caso contrário, ele é `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="c39bb-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="c39bb-110">Você pode sombrear ou substituir para redefinir um elemento herdado, mas há diferenças significativas entre as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="c39bb-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="c39bb-111">Para obter mais informações, consulte [sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="c39bb-111">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="c39bb-112">Um elemento que pode ser substituído, às vezes é chamado para um *virtual* elemento.</span><span class="sxs-lookup"><span data-stu-id="c39bb-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="c39bb-113">Se ele pode ser substituído, mas não precisa ser, às vezes, também é chamado um *concreto* elemento.</span><span class="sxs-lookup"><span data-stu-id="c39bb-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="c39bb-114">Você pode usar `Overridable` somente em uma instrução de declaração de propriedade ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="c39bb-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="c39bb-115">Modificadores combinados</span><span class="sxs-lookup"><span data-stu-id="c39bb-115">Combined Modifiers</span></span>  
 <span data-ttu-id="c39bb-116">Não é possível especificar `Overridable` ou `NotOverridable` para um `Private` método.</span><span class="sxs-lookup"><span data-stu-id="c39bb-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="c39bb-117">Não é possível especificar `Overridable` junto com `MustOverride`, `NotOverridable`, ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="c39bb-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="c39bb-118">Como um elemento de substituição é implicitamente substituível, não é possível combinar `Overridable` com `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="c39bb-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="c39bb-119">Uso</span><span class="sxs-lookup"><span data-stu-id="c39bb-119">Usage</span></span>  
 <span data-ttu-id="c39bb-120">O `Overridable` modificador pode ser usado nestes contextos:</span><span class="sxs-lookup"><span data-stu-id="c39bb-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="c39bb-121">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="c39bb-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="c39bb-122">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="c39bb-122">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="c39bb-123">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="c39bb-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c39bb-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c39bb-124">See also</span></span>

- [<span data-ttu-id="c39bb-125">Modificadores</span><span class="sxs-lookup"><span data-stu-id="c39bb-125">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)
- [<span data-ttu-id="c39bb-126">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="c39bb-126">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="c39bb-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="c39bb-127">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="c39bb-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="c39bb-128">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="c39bb-129">Substituições</span><span class="sxs-lookup"><span data-stu-id="c39bb-129">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="c39bb-130">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="c39bb-130">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="c39bb-131">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c39bb-131">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
