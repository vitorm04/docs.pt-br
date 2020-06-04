---
title: MustOverride
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
ms.openlocfilehash: 1b20108a2d42e82c0af7598fde8d60a08fea28ec
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396188"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="06203-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06203-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="06203-103">Especifica que uma propriedade ou procedimento não está implementado nesta classe e deve ser substituído em uma classe derivada antes que possa ser usado.</span><span class="sxs-lookup"><span data-stu-id="06203-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06203-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="06203-104">Remarks</span></span>  
 <span data-ttu-id="06203-105">Você pode usar `MustOverride` somente em uma instrução de declaração de propriedade ou de procedimento.</span><span class="sxs-lookup"><span data-stu-id="06203-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="06203-106">A propriedade ou procedimento que especifica `MustOverride` deve ser um membro de uma classe e a classe deve ser marcada como [MustInherit](mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="06203-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="06203-107">Regras</span><span class="sxs-lookup"><span data-stu-id="06203-107">Rules</span></span>  
  
- <span data-ttu-id="06203-108">**Declaração incompleta.**</span><span class="sxs-lookup"><span data-stu-id="06203-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="06203-109">Quando você especifica `MustOverride` , você não fornece nenhuma linha adicional de código para a propriedade ou procedimento, nem mesmo a `End Function` instrução, `End Property` ou `End Sub` .</span><span class="sxs-lookup"><span data-stu-id="06203-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
- <span data-ttu-id="06203-110">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="06203-110">**Combined Modifiers.**</span></span> <span data-ttu-id="06203-111">Você não pode especificar `MustOverride` juntos com `NotOverridable` , `Overridable` ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="06203-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
- <span data-ttu-id="06203-112">**Sombreamento e substituição.**</span><span class="sxs-lookup"><span data-stu-id="06203-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="06203-113">Sombreamento e substituição redefinem um elemento herdado, mas há diferenças significativas entre as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="06203-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="06203-114">Para obter mais informações, consulte [sombreamento em Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="06203-114">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
- <span data-ttu-id="06203-115">**Termos alternativos.**</span><span class="sxs-lookup"><span data-stu-id="06203-115">**Alternate Terms.**</span></span> <span data-ttu-id="06203-116">Um elemento que não pode ser usado, exceto em uma substituição, às vezes é chamado de elemento *virtual puro* .</span><span class="sxs-lookup"><span data-stu-id="06203-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="06203-117">O `MustOverride` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="06203-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="06203-118">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="06203-118">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="06203-119">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="06203-119">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="06203-120">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="06203-120">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="06203-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="06203-121">See also</span></span>

- [<span data-ttu-id="06203-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="06203-122">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="06203-123">Substituível</span><span class="sxs-lookup"><span data-stu-id="06203-123">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="06203-124">Substituições</span><span class="sxs-lookup"><span data-stu-id="06203-124">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="06203-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="06203-125">MustInherit</span></span>](mustinherit.md)
- [<span data-ttu-id="06203-126">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="06203-126">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="06203-127">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="06203-127">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
