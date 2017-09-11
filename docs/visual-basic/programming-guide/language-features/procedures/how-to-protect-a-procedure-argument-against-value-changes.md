---
title: "Como: proteger um argumento de procedimento contra alterações de valor (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- procedures, arguments
- procedures, parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures, calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
caps.latest.revision: 14
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
ms.openlocfilehash: db40b3426256e7789a5273ab4d0afc8d5b47c8a7
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a><span data-ttu-id="45364-102">Como proteger um argumento de procedimento contra alterações de valor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45364-102">How to: Protect a Procedure Argument Against Value Changes (Visual Basic)</span></span>
<span data-ttu-id="45364-103">Se um procedimento declara um parâmetro como [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece o código do procedimento uma referência direta ao elemento de programação subjacente o argumento o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="45364-103">If a procedure declares a parameter as [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="45364-104">Isso permite que o procedimento para alterar o valor subjacente do argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="45364-104">This permits the procedure to change the value underlying the argument in the calling code.</span></span> <span data-ttu-id="45364-105">Em alguns casos, o código de chamada talvez queira proteger contra uma alteração.</span><span class="sxs-lookup"><span data-stu-id="45364-105">In some cases the calling code might want to protect against such a change.</span></span>  
  
 <span data-ttu-id="45364-106">Você sempre pode proteger um argumento de alteração ao declarar o parâmetro correspondente [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) no procedimento.</span><span class="sxs-lookup"><span data-stu-id="45364-106">You can always protect an argument from change by declaring the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) in the procedure.</span></span> <span data-ttu-id="45364-107">Se você quiser ser capaz de alterar um determinado argumento em alguns casos, mas outros não, você pode declará-lo `ByRef` e permitir que o código de chamada determinar o mecanismo de passagem em cada chamada.</span><span class="sxs-lookup"><span data-stu-id="45364-107">If you want to be able to change a given argument in some cases but not others, you can declare it `ByRef` and let the calling code determine the passing mechanism in each call.</span></span> <span data-ttu-id="45364-108">Isso é feito colocando o argumento correspondente entre parênteses para passá-lo por valor ou não envolve em parênteses passá-lo por referência.</span><span class="sxs-lookup"><span data-stu-id="45364-108">It does this by enclosing the corresponding argument in parentheses to pass it by value, or not enclosing it in parentheses to pass it by reference.</span></span> <span data-ttu-id="45364-109">Para obter mais informações, consulte [como: forçar um argumento a ser passado por valor](./how-to-force-an-argument-to-be-passed-by-value.md).</span><span class="sxs-lookup"><span data-stu-id="45364-109">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="45364-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45364-110">Example</span></span>  
 <span data-ttu-id="45364-111">O exemplo a seguir mostra dois procedimentos que tenham uma variável de matriz e operam em seus elementos.</span><span class="sxs-lookup"><span data-stu-id="45364-111">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="45364-112">O `increase` procedimento simplesmente adiciona um para cada elemento.</span><span class="sxs-lookup"><span data-stu-id="45364-112">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="45364-113">O `replace` procedimento atribui uma nova matriz para o parâmetro `a()` e, em seguida, adiciona um para cada elemento.</span><span class="sxs-lookup"><span data-stu-id="45364-113">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="45364-114">No entanto, a reatribuição não afeta a variável array subjacente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="45364-114">However, the reassignment does not affect the underlying array variable in the calling code.</span></span>  
  
 <span data-ttu-id="45364-115">[!code-vb[VbVbcnProcedures&#35;](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="45364-115">[!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]</span></span>  
  
 <span data-ttu-id="45364-116">[!code-vb[VbVbcnProcedures&38;](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="45364-116">[!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]</span></span>  
  
 <span data-ttu-id="45364-117">[!code-vb[VbVbcnProcedures&#37;](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="45364-117">[!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]</span></span>  
  
 <span data-ttu-id="45364-118">A primeira `MsgBox` chamada exibe "após increase (n): 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="45364-118">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="45364-119">Porque a matriz `n` é um tipo de referência, `replace` pode alterar seus membros, mesmo que o mecanismo de passagem é `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="45364-119">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="45364-120">O segundo `MsgBox` chamada exibe "Após Replace (n): 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="45364-120">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="45364-121">Porque `n` é passado `ByVal`, `replace` não é possível modificar a variável `n` no código de chamada, atribuindo uma nova matriz para ele.</span><span class="sxs-lookup"><span data-stu-id="45364-121">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` in the calling code by assigning a new array to it.</span></span> <span data-ttu-id="45364-122">Quando `replace` cria a nova instância de matriz `k` e o atribui à variável local `a`, ele perde a referência à `n` passado pelo código de chamada.</span><span class="sxs-lookup"><span data-stu-id="45364-122">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="45364-123">Quando ele se transformar os membros de `a`, somente o array local `k` é afetado.</span><span class="sxs-lookup"><span data-stu-id="45364-123">When it changes the members of `a`, only the local array `k` is affected.</span></span> <span data-ttu-id="45364-124">Portanto, `replace` não incrementa os valores de matriz `n` no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="45364-124">Therefore, `replace` does not increment the values of array `n` in the calling code.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="45364-125">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="45364-125">Compiling the Code</span></span>  
 <span data-ttu-id="45364-126">O padrão no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] é passar argumentos por valor.</span><span class="sxs-lookup"><span data-stu-id="45364-126">The default in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="45364-127">No entanto, é boa prática incluir de programação a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) palavra-chave com cada parâmetro declarado.</span><span class="sxs-lookup"><span data-stu-id="45364-127">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="45364-128">Isso torna seu código mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="45364-128">This makes your code easier to read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45364-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45364-129">See Also</span></span>  
 <span data-ttu-id="45364-130">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="45364-130">[Procedures](./index.md) </span></span>  
<span data-ttu-id="45364-131"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="45364-131"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="45364-132"> [Como: passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="45364-132"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="45364-133"> [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="45364-133"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="45364-134"> [Diferenças entre argumentos modificável e não modificável](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="45364-134"> [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span></span>  
<span data-ttu-id="45364-135"> [Diferenças entre passar um argumento por valor e por referência](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="45364-135"> [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="45364-136"> [Como: alterar o valor de um argumento de procedimento](./how-to-change-the-value-of-a-procedure-argument.md) </span><span class="sxs-lookup"><span data-stu-id="45364-136"> [How to: Change the Value of a Procedure Argument](./how-to-change-the-value-of-a-procedure-argument.md) </span></span>  
<span data-ttu-id="45364-137"> [Como: forçar um argumento a ser passado por valor](./how-to-force-an-argument-to-be-passed-by-value.md) </span><span class="sxs-lookup"><span data-stu-id="45364-137"> [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md) </span></span>  
<span data-ttu-id="45364-138"> [Passando argumentos por posição e nome](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="45364-138"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="45364-139"> [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="45364-139"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
