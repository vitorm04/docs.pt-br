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
ms.openlocfilehash: 463dd2454aafebf11554fb7bacdb73724c3130d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392152"
---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="83e6f-102">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83e6f-102">NotOverridable (Visual Basic)</span></span>
<span data-ttu-id="83e6f-103">Especifica que uma propriedade ou procedimento não pode ser substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="83e6f-103">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83e6f-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="83e6f-104">Remarks</span></span>  
 <span data-ttu-id="83e6f-105">O `NotOverridable` modificador impede que uma propriedade ou um método seja substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="83e6f-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="83e6f-106">O modificador [Overridable](overridable.md) permite que uma propriedade ou método em uma classe seja substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="83e6f-106">The [Overridable](overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="83e6f-107">Para obter mais informações, consulte [Noções básicas de herança](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="83e6f-107">For more information, see [Inheritance Basics](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="83e6f-108">Se o `Overridable` `NotOverridable` modificador ou não for especificado, a configuração padrão dependerá se a propriedade ou o método substituirá uma propriedade ou método de classe base.</span><span class="sxs-lookup"><span data-stu-id="83e6f-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="83e6f-109">Se a propriedade ou o método substituir uma propriedade ou método de classe base, a configuração padrão será `Overridable` ; caso contrário, será `NotOverridable` .</span><span class="sxs-lookup"><span data-stu-id="83e6f-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="83e6f-110">Um elemento que não pode ser substituído às vezes é chamado de elemento *lacrado* .</span><span class="sxs-lookup"><span data-stu-id="83e6f-110">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="83e6f-111">Você pode usar `NotOverridable` somente em uma instrução de declaração de propriedade ou de procedimento.</span><span class="sxs-lookup"><span data-stu-id="83e6f-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="83e6f-112">Você pode especificar `NotOverridable` apenas em uma propriedade ou um procedimento que substitua outra propriedade ou procedimento, ou seja, somente em combinação com `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="83e6f-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="83e6f-113">Modificadores combinados</span><span class="sxs-lookup"><span data-stu-id="83e6f-113">Combined Modifiers</span></span>  
 <span data-ttu-id="83e6f-114">Você não pode especificar `Overridable` ou `NotOverridable` para um `Private` método.</span><span class="sxs-lookup"><span data-stu-id="83e6f-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="83e6f-115">Você não pode especificar `NotOverridable` juntos com `MustOverride` , `Overridable` ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="83e6f-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="83e6f-116">Uso</span><span class="sxs-lookup"><span data-stu-id="83e6f-116">Usage</span></span>  
 <span data-ttu-id="83e6f-117">O `NotOverridable` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="83e6f-117">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="83e6f-118">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="83e6f-118">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="83e6f-119">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="83e6f-119">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="83e6f-120">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="83e6f-120">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="83e6f-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="83e6f-121">See also</span></span>

- [<span data-ttu-id="83e6f-122">Modificadores</span><span class="sxs-lookup"><span data-stu-id="83e6f-122">Modifiers</span></span>](index.md)
- [<span data-ttu-id="83e6f-123">Noções básicas de herança</span><span class="sxs-lookup"><span data-stu-id="83e6f-123">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="83e6f-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="83e6f-124">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="83e6f-125">Substituível</span><span class="sxs-lookup"><span data-stu-id="83e6f-125">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="83e6f-126">Substituições</span><span class="sxs-lookup"><span data-stu-id="83e6f-126">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="83e6f-127">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="83e6f-127">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="83e6f-128">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="83e6f-128">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
