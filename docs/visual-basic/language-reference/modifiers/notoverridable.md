---
title: NotOverridable (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.NotOverridable
- NotOverridable
dev_langs:
- VB
helpviewer_keywords:
- sealed methods
- NotOverridable keyword
- properties [Visual Basic], redefining
- elements, sealed
- sealed elements
- procedures, overriding
- procedures, redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
caps.latest.revision: 15
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
ms.openlocfilehash: 1881334495e9955e9c2fb4374e7dd4b0c6e01d88
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="5bfa9-102">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5bfa9-102">NotOverridable (Visual Basic)</span></span>
<span data-ttu-id="5bfa9-103">Especifica que uma propriedade ou procedimento não pode ser substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="5bfa9-103">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bfa9-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="5bfa9-104">Remarks</span></span>  
 <span data-ttu-id="5bfa9-105">O `NotOverridable` modificador impede que uma propriedade ou método que está sendo substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="5bfa9-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="5bfa9-106">O [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modificador permite que uma propriedade ou método em uma classe a ser substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="5bfa9-106">The [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="5bfa9-107">Para obter mais informações, consulte [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="5bfa9-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="5bfa9-108">Se o `Overridable` ou `NotOverridable` modificador não for especificado, a configuração padrão depende se a propriedade ou método substitui um método ou propriedade da classe base.</span><span class="sxs-lookup"><span data-stu-id="5bfa9-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="5bfa9-109">Se a propriedade ou método substitui um método ou propriedade da classe base, a configuração padrão é `Overridable`; caso contrário, ele é `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="5bfa9-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="5bfa9-110">Um elemento que não pode ser substituído às vezes é chamado um *lacrado* elemento.</span><span class="sxs-lookup"><span data-stu-id="5bfa9-110">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="5bfa9-111">Você pode usar `NotOverridable` somente na declaração de uma propriedade ou um procedimento.</span><span class="sxs-lookup"><span data-stu-id="5bfa9-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="5bfa9-112">Você pode especificar `NotOverridable` somente em uma propriedade ou um procedimento que substitui outra propriedade ou procedimento, ou seja, somente em combinação com `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="5bfa9-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="5bfa9-113">Modificadores combinados</span><span class="sxs-lookup"><span data-stu-id="5bfa9-113">Combined Modifiers</span></span>  
 <span data-ttu-id="5bfa9-114">Não é possível especificar `Overridable` ou `NotOverridable` para um `Private` método.</span><span class="sxs-lookup"><span data-stu-id="5bfa9-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="5bfa9-115">Não é possível especificar `NotOverridable` junto com `MustOverride`, `Overridable`, ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="5bfa9-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="5bfa9-116">Uso</span><span class="sxs-lookup"><span data-stu-id="5bfa9-116">Usage</span></span>  
 <span data-ttu-id="5bfa9-117">O `NotOverridable` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="5bfa9-117">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="5bfa9-118">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="5bfa9-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="5bfa9-119">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="5bfa9-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="5bfa9-120">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="5bfa9-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="5bfa9-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5bfa9-121">See Also</span></span>  
 <span data-ttu-id="5bfa9-122">[Modificadores](../../../visual-basic/language-reference/modifiers/index.md) </span><span class="sxs-lookup"><span data-stu-id="5bfa9-122">[Modifiers](../../../visual-basic/language-reference/modifiers/index.md) </span></span>  
<span data-ttu-id="5bfa9-123"> [Noções básicas sobre herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md) </span><span class="sxs-lookup"><span data-stu-id="5bfa9-123"> [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md) </span></span>  
<span data-ttu-id="5bfa9-124"> [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md) </span><span class="sxs-lookup"><span data-stu-id="5bfa9-124"> [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md) </span></span>  
<span data-ttu-id="5bfa9-125"> [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md) </span><span class="sxs-lookup"><span data-stu-id="5bfa9-125"> [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) </span></span>  
<span data-ttu-id="5bfa9-126"> [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md) </span><span class="sxs-lookup"><span data-stu-id="5bfa9-126"> [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md) </span></span>  
<span data-ttu-id="5bfa9-127"> [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="5bfa9-127"> [Keywords](../../../visual-basic/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="5bfa9-128"> [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)</span><span class="sxs-lookup"><span data-stu-id="5bfa9-128"> [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)</span></span>
