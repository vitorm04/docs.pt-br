---
title: NotOverridable
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
ms.openlocfilehash: c55d57bb3008b2825fe5382844908ea32f0d500c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351451"
---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="8ff38-102">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ff38-102">NotOverridable (Visual Basic)</span></span>
<span data-ttu-id="8ff38-103">Especifica que uma propriedade ou procedimento não pode ser substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="8ff38-103">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ff38-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="8ff38-104">Remarks</span></span>  
 <span data-ttu-id="8ff38-105">O modificador `NotOverridable` impede que uma propriedade ou um método seja substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="8ff38-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="8ff38-106">O modificador [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) permite que uma propriedade ou método em uma classe seja substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="8ff38-106">The [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="8ff38-107">Para obter mais informações, consulte [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="8ff38-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="8ff38-108">Se o modificador `Overridable` ou `NotOverridable` não for especificado, a configuração padrão dependerá se a propriedade ou o método substituirá uma propriedade ou método de classe base.</span><span class="sxs-lookup"><span data-stu-id="8ff38-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="8ff38-109">Se a propriedade ou o método substituir uma propriedade ou método de classe base, a configuração padrão será `Overridable`; caso contrário, será `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="8ff38-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="8ff38-110">Um elemento que não pode ser substituído às vezes é chamado de elemento *lacrado* .</span><span class="sxs-lookup"><span data-stu-id="8ff38-110">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="8ff38-111">Você pode usar `NotOverridable` apenas em uma instrução de declaração de propriedade ou de procedimento.</span><span class="sxs-lookup"><span data-stu-id="8ff38-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="8ff38-112">Você pode especificar `NotOverridable` apenas em uma propriedade ou procedimento que substitua outra propriedade ou procedimento, ou seja, somente em combinação com `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="8ff38-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="8ff38-113">Modificadores combinados</span><span class="sxs-lookup"><span data-stu-id="8ff38-113">Combined Modifiers</span></span>  
 <span data-ttu-id="8ff38-114">Você não pode especificar `Overridable` ou `NotOverridable` para um método de `Private`.</span><span class="sxs-lookup"><span data-stu-id="8ff38-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="8ff38-115">Não é possível especificar `NotOverridable` junto com `MustOverride`, `Overridable`ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="8ff38-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="8ff38-116">Uso</span><span class="sxs-lookup"><span data-stu-id="8ff38-116">Usage</span></span>  
 <span data-ttu-id="8ff38-117">O modificador de `NotOverridable` pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="8ff38-117">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="8ff38-118">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="8ff38-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="8ff38-119">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="8ff38-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="8ff38-120">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="8ff38-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="8ff38-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ff38-121">See also</span></span>

- [<span data-ttu-id="8ff38-122">Modificadores</span><span class="sxs-lookup"><span data-stu-id="8ff38-122">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)
- [<span data-ttu-id="8ff38-123">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="8ff38-123">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="8ff38-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="8ff38-124">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="8ff38-125">Substituível</span><span class="sxs-lookup"><span data-stu-id="8ff38-125">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="8ff38-126">Substituições</span><span class="sxs-lookup"><span data-stu-id="8ff38-126">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="8ff38-127">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="8ff38-127">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="8ff38-128">Sombreamento em Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8ff38-128">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
