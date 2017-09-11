---
title: "Substituível (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- Overridable
- vb.Overridable
dev_langs:
- VB
helpviewer_keywords:
- elements, concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements, virtual
- virtual elements
- procedures, overriding
- concrete elements
- procedures, redefining
- Overridable keyword
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
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
ms.openlocfilehash: a35ab8c638cfa875c7d85d9536aa98c6d81bb27e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="overridable-visual-basic"></a><span data-ttu-id="fb9de-102">Substituível (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb9de-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="fb9de-103">Especifica se uma propriedade ou procedimento pode ser substituído por uma propriedade nomeada de forma idêntica ou procedimento derivado de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="fb9de-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb9de-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb9de-104">Remarks</span></span>  
 <span data-ttu-id="fb9de-105">O `Overridable` modificador permite que uma propriedade ou método em uma classe a ser substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="fb9de-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="fb9de-106">O [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modificador impede que uma propriedade ou método que está sendo substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="fb9de-106">The [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="fb9de-107">Para obter mais informações, consulte [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="fb9de-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="fb9de-108">Se o `Overridable` ou `NotOverridable` modificador não for especificado, a configuração padrão depende se a propriedade ou método substitui um método ou propriedade da classe base.</span><span class="sxs-lookup"><span data-stu-id="fb9de-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="fb9de-109">Se a propriedade ou método substitui um método ou propriedade da classe base, a configuração padrão é `Overridable`; caso contrário, ele é `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="fb9de-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="fb9de-110">Você pode sombrear ou substituir para redefinir um elemento herdado, mas há diferenças significativas entre as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="fb9de-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="fb9de-111">Para obter mais informações, consulte [sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="fb9de-111">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="fb9de-112">Um elemento que pode ser substituído às vezes é conhecido como um *virtual* elemento.</span><span class="sxs-lookup"><span data-stu-id="fb9de-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="fb9de-113">Se ele pode ser substituído, mas não precisa ser, ele também é chamado um *concreta* elemento.</span><span class="sxs-lookup"><span data-stu-id="fb9de-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="fb9de-114">Você pode usar `Overridable` somente na declaração de uma propriedade ou um procedimento.</span><span class="sxs-lookup"><span data-stu-id="fb9de-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="fb9de-115">Modificadores combinados</span><span class="sxs-lookup"><span data-stu-id="fb9de-115">Combined Modifiers</span></span>  
 <span data-ttu-id="fb9de-116">Não é possível especificar `Overridable` ou `NotOverridable` para um `Private` método.</span><span class="sxs-lookup"><span data-stu-id="fb9de-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="fb9de-117">Não é possível especificar `Overridable` junto com `MustOverride`, `NotOverridable`, ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="fb9de-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="fb9de-118">Como um elemento de substituição é implicitamente substituível, você não pode combinar `Overridable` com `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="fb9de-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="fb9de-119">Uso</span><span class="sxs-lookup"><span data-stu-id="fb9de-119">Usage</span></span>  
 <span data-ttu-id="fb9de-120">O `Overridable` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="fb9de-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="fb9de-121">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="fb9de-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="fb9de-122">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="fb9de-122">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="fb9de-123">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="fb9de-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="fb9de-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb9de-124">See Also</span></span>  
 <span data-ttu-id="fb9de-125">[Modificadores](../../../visual-basic/language-reference/modifiers/index.md) </span><span class="sxs-lookup"><span data-stu-id="fb9de-125">[Modifiers](../../../visual-basic/language-reference/modifiers/index.md) </span></span>  
<span data-ttu-id="fb9de-126"> [Noções básicas sobre herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md) </span><span class="sxs-lookup"><span data-stu-id="fb9de-126"> [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md) </span></span>  
<span data-ttu-id="fb9de-127"> [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md) </span><span class="sxs-lookup"><span data-stu-id="fb9de-127"> [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md) </span></span>  
<span data-ttu-id="fb9de-128"> [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) </span><span class="sxs-lookup"><span data-stu-id="fb9de-128"> [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) </span></span>  
<span data-ttu-id="fb9de-129"> [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md) </span><span class="sxs-lookup"><span data-stu-id="fb9de-129"> [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md) </span></span>  
<span data-ttu-id="fb9de-130"> [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="fb9de-130"> [Keywords](../../../visual-basic/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="fb9de-131"> [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)</span><span class="sxs-lookup"><span data-stu-id="fb9de-131"> [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)</span></span>
