---
title: Substituível
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
ms.openlocfilehash: 9c639665fd92a56de6fb6e5147cda873ef457b45
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351397"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="96f20-102">Substituível (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96f20-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="96f20-103">Especifica que uma propriedade ou procedimento pode ser substituído por uma propriedade nomeada de forma idêntica ou um procedimento em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="96f20-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96f20-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="96f20-104">Remarks</span></span>  
 <span data-ttu-id="96f20-105">O modificador `Overridable` permite que uma propriedade ou método em uma classe seja substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="96f20-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="96f20-106">O modificador [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) impede que uma propriedade ou um método seja substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="96f20-106">The [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="96f20-107">Para obter mais informações, consulte [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="96f20-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="96f20-108">Se o modificador `Overridable` ou `NotOverridable` não for especificado, a configuração padrão dependerá se a propriedade ou o método substituirá uma propriedade ou método de classe base.</span><span class="sxs-lookup"><span data-stu-id="96f20-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="96f20-109">Se a propriedade ou o método substituir uma propriedade ou método de classe base, a configuração padrão será `Overridable`; caso contrário, será `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="96f20-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="96f20-110">Você pode sombrear ou substituir para redefinir um elemento herdado, mas há diferenças significativas entre as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="96f20-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="96f20-111">Para obter mais informações, consulte [sombreamento em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="96f20-111">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="96f20-112">Um elemento que pode ser substituído às vezes é chamado de elemento *virtual* .</span><span class="sxs-lookup"><span data-stu-id="96f20-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="96f20-113">Se ele puder ser substituído, mas não precisar ser, às vezes ele também é chamado de elemento *concreto* .</span><span class="sxs-lookup"><span data-stu-id="96f20-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="96f20-114">Você pode usar `Overridable` apenas em uma instrução de declaração de propriedade ou de procedimento.</span><span class="sxs-lookup"><span data-stu-id="96f20-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="96f20-115">Modificadores combinados</span><span class="sxs-lookup"><span data-stu-id="96f20-115">Combined Modifiers</span></span>  
 <span data-ttu-id="96f20-116">Você não pode especificar `Overridable` ou `NotOverridable` para um método de `Private`.</span><span class="sxs-lookup"><span data-stu-id="96f20-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="96f20-117">Não é possível especificar `Overridable` junto com `MustOverride`, `NotOverridable`ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="96f20-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="96f20-118">Como um elemento de substituição é implicitamente substituível, não é possível combinar `Overridable` com `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="96f20-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="96f20-119">Uso</span><span class="sxs-lookup"><span data-stu-id="96f20-119">Usage</span></span>  
 <span data-ttu-id="96f20-120">O modificador de `Overridable` pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="96f20-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="96f20-121">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="96f20-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="96f20-122">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="96f20-122">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="96f20-123">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="96f20-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="96f20-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96f20-124">See also</span></span>

- [<span data-ttu-id="96f20-125">Modificadores</span><span class="sxs-lookup"><span data-stu-id="96f20-125">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)
- [<span data-ttu-id="96f20-126">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="96f20-126">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="96f20-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="96f20-127">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="96f20-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="96f20-128">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="96f20-129">Substituições</span><span class="sxs-lookup"><span data-stu-id="96f20-129">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="96f20-130">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="96f20-130">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="96f20-131">Sombreamento em Visual Basic</span><span class="sxs-lookup"><span data-stu-id="96f20-131">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
