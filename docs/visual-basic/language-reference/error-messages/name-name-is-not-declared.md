---
title: Nome &#39; &lt;nome&gt;&#39; não é declarada
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a63ae74c7179d71756e2b9b4bf6b41a71ce12a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="name-39ltnamegt39-is-not-declared"></a><span data-ttu-id="db37a-102">Nome &#39; &lt;nome&gt;&#39; não é declarada</span><span class="sxs-lookup"><span data-stu-id="db37a-102">Name &#39;&lt;name&gt;&#39; is not declared</span></span>
<span data-ttu-id="db37a-103">Uma instrução faz referência a um elemento de programação, mas o compilador não pode localizar um elemento com esse nome exato.</span><span class="sxs-lookup"><span data-stu-id="db37a-103">A statement refers to a programming element, but the compiler cannot find an element with that exact name.</span></span>  
  
 <span data-ttu-id="db37a-104">**ID do erro:** BC30451</span><span class="sxs-lookup"><span data-stu-id="db37a-104">**Error ID:** BC30451</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="db37a-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="db37a-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="db37a-106">Verifique a ortografia do nome na declaração de referência.</span><span class="sxs-lookup"><span data-stu-id="db37a-106">Check the spelling of the name in the referring statement.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="db37a-107">diferencia maiusculas de minúsculas, mas qualquer outra variação de grafia é considerada como um nome completamente diferente.</span><span class="sxs-lookup"><span data-stu-id="db37a-107"> is case-insensitive, but any other variation in the spelling is regarded as a completely different name.</span></span> <span data-ttu-id="db37a-108">Observe que o caractere de sublinhado (`_`) é parte do nome e, portanto, parte da ortografia.</span><span class="sxs-lookup"><span data-stu-id="db37a-108">Note that the underscore (`_`) is part of the name and therefore part of the spelling.</span></span>  
  
2.  <span data-ttu-id="db37a-109">Verifique se você tem o operador de acesso de membro (`.`) entre um objeto e seus membros.</span><span class="sxs-lookup"><span data-stu-id="db37a-109">Check that you have the member access operator (`.`) between an object and its member.</span></span> <span data-ttu-id="db37a-110">Por exemplo, se você tiver um <xref:System.Windows.Forms.TextBox> controle chamado `TextBox1`, para acessar seu <xref:System.Windows.Forms.TextBoxBase.Text%2A> propriedade, você deve digitar `TextBox1.Text`.</span><span class="sxs-lookup"><span data-stu-id="db37a-110">For example, if you have a <xref:System.Windows.Forms.TextBox> control named `TextBox1`, to access its <xref:System.Windows.Forms.TextBoxBase.Text%2A> property you should type `TextBox1.Text`.</span></span> <span data-ttu-id="db37a-111">Se, em vez disso, você digita `TextBox1Text`, você criou um nome diferente.</span><span class="sxs-lookup"><span data-stu-id="db37a-111">If instead you type `TextBox1Text`, you have created a different name.</span></span>  
  
3.  <span data-ttu-id="db37a-112">Se a ortografia está correta e a sintaxe de qualquer acesso de membro de objeto está correta, verifique se que o elemento foi declarado.</span><span class="sxs-lookup"><span data-stu-id="db37a-112">If the spelling is correct and the syntax of any object member access is correct, verify that the element has been declared.</span></span> <span data-ttu-id="db37a-113">Para obter mais informações, consulte [elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).</span><span class="sxs-lookup"><span data-stu-id="db37a-113">For more information, see [Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).</span></span>  
  
4.  <span data-ttu-id="db37a-114">Se o elemento de programação tiver sido declarado, verifique se ele está no escopo.</span><span class="sxs-lookup"><span data-stu-id="db37a-114">If the programming element has been declared, check that it is in scope.</span></span> <span data-ttu-id="db37a-115">Se a referência está fora da região que declara o elemento de programação, talvez seja necessário qualificar o nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="db37a-115">If the referring statement is outside the region declaring the programming element, you might need to qualify the element name.</span></span> <span data-ttu-id="db37a-116">Para obter mais informações, consulte [escopo no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="db37a-116">For more information, see [Scope in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db37a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db37a-117">See Also</span></span>  
 [<span data-ttu-id="db37a-118">Resumo de Declarações e Constantes</span><span class="sxs-lookup"><span data-stu-id="db37a-118">Declarations and Constants Summary</span></span>](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)  
 [<span data-ttu-id="db37a-119">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="db37a-119">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="db37a-120">Nomes de Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="db37a-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="db37a-121">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="db37a-121">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
