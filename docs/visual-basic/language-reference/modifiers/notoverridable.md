---
title: NotOverridable (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
ms.openlocfilehash: 41c08a48fdb7501081e887fb5cf9f99c334c72ac
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822285"
---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="52338-102">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52338-102">NotOverridable (Visual Basic)</span></span>
<span data-ttu-id="52338-103">Especifica que uma propriedade ou procedimento não pode ser substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="52338-103">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52338-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="52338-104">Remarks</span></span>  
 <span data-ttu-id="52338-105">O `NotOverridable` modificador impede que uma propriedade ou método que está sendo substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="52338-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="52338-106">O [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modificador permite que uma propriedade ou método em uma classe seja substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="52338-106">The [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="52338-107">Para obter mais informações, consulte [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="52338-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="52338-108">Se o `Overridable` ou `NotOverridable` modificador não for especificado, a configuração padrão depende se a propriedade ou método substitui um método ou propriedade de classe base.</span><span class="sxs-lookup"><span data-stu-id="52338-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="52338-109">Se a propriedade ou método substitui um método ou propriedade de classe base, a configuração padrão é `Overridable`; caso contrário, ele é `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="52338-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="52338-110">Um elemento que não pode ser substituído é chamado, às vezes, uma *lacrado* elemento.</span><span class="sxs-lookup"><span data-stu-id="52338-110">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="52338-111">Você pode usar `NotOverridable` somente em uma instrução de declaração de propriedade ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="52338-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="52338-112">Você pode especificar `NotOverridable` somente em uma propriedade ou procedimento que substitui outra propriedade ou procedimento, ou seja, apenas em combinação com `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="52338-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="52338-113">Modificadores combinados</span><span class="sxs-lookup"><span data-stu-id="52338-113">Combined Modifiers</span></span>  
 <span data-ttu-id="52338-114">Não é possível especificar `Overridable` ou `NotOverridable` para um `Private` método.</span><span class="sxs-lookup"><span data-stu-id="52338-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="52338-115">Não é possível especificar `NotOverridable` junto com `MustOverride`, `Overridable`, ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="52338-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="52338-116">Uso</span><span class="sxs-lookup"><span data-stu-id="52338-116">Usage</span></span>  
 <span data-ttu-id="52338-117">O `NotOverridable` modificador pode ser usado nestes contextos:</span><span class="sxs-lookup"><span data-stu-id="52338-117">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="52338-118">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="52338-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="52338-119">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="52338-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="52338-120">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="52338-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="52338-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52338-121">See also</span></span>

- [<span data-ttu-id="52338-122">Modificadores</span><span class="sxs-lookup"><span data-stu-id="52338-122">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)
- [<span data-ttu-id="52338-123">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="52338-123">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="52338-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="52338-124">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="52338-125">Substituível</span><span class="sxs-lookup"><span data-stu-id="52338-125">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="52338-126">Substituições</span><span class="sxs-lookup"><span data-stu-id="52338-126">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="52338-127">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="52338-127">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="52338-128">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52338-128">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
