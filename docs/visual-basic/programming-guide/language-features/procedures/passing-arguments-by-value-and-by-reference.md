---
title: "Passando argumentos por valor e por referência (Visual Basic) | Documentos do Microsoft"
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
- ByRef keyword, passing arguments by reference
- Visual Basic code, procedures
- passing arguments, by value or by reference
- ByVal keyword, passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing, by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
caps.latest.revision: 23
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
ms.openlocfilehash: 44107171d6f24e22614788470c65cf7ad8d28640
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a><span data-ttu-id="09e82-102">Passando argumentos por valor e por referência (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09e82-102">Passing Arguments by Value and by Reference (Visual Basic)</span></span>
<span data-ttu-id="09e82-103">Em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], você pode passar um argumento para um procedimento *pelo valor* ou *por referência*.</span><span class="sxs-lookup"><span data-stu-id="09e82-103">In [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], you can pass an argument to a procedure *by value* or *by reference*.</span></span> <span data-ttu-id="09e82-104">Isso é conhecido como o *mecanismo de passagem*, e determina se o procedimento pode modificar o elemento de programação subjacente o argumento o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="09e82-104">This is known as the *passing mechanism*, and it determines whether the procedure can modify the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="09e82-105">A declaração do procedimento determina o mecanismo de passagem de cada parâmetro especificando o [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="09e82-105">The procedure declaration determines the passing mechanism for each parameter by specifying the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword.</span></span>  
  
## <a name="distinctions"></a><span data-ttu-id="09e82-106">Distinções</span><span class="sxs-lookup"><span data-stu-id="09e82-106">Distinctions</span></span>  
 <span data-ttu-id="09e82-107">Ao passar um argumento para um procedimento, esteja ciente das várias distinções diferentes que interagem entre si:</span><span class="sxs-lookup"><span data-stu-id="09e82-107">When passing an argument to a procedure, be aware of several different distinctions that interact with each other:</span></span>  
  
-   <span data-ttu-id="09e82-108">Se o elemento de programação subjacente é modificáveis ou não modificáveis</span><span class="sxs-lookup"><span data-stu-id="09e82-108">Whether the underlying programming element is modifiable or nonmodifiable</span></span>  
  
-   <span data-ttu-id="09e82-109">Se o próprio argumento é modificáveis ou não modificáveis</span><span class="sxs-lookup"><span data-stu-id="09e82-109">Whether the argument itself is modifiable or nonmodifiable</span></span>  
  
-   <span data-ttu-id="09e82-110">Se o argumento está sendo passado por valor ou por referência</span><span class="sxs-lookup"><span data-stu-id="09e82-110">Whether the argument is being passed by value or by reference</span></span>  
  
-   <span data-ttu-id="09e82-111">Se o tipo de dados de argumento é um tipo de valor ou um tipo de referência</span><span class="sxs-lookup"><span data-stu-id="09e82-111">Whether the argument data type is a value type or a reference type</span></span>  
  
 <span data-ttu-id="09e82-112">Para obter mais informações, consulte [as diferenças entre modificáveis e não modificáveis argumentos](./differences-between-modifiable-and-nonmodifiable-arguments.md) e [as diferenças entre passar um argumento por valor e por referência](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="09e82-112">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) and [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="choice-of-passing-mechanism"></a><span data-ttu-id="09e82-113">Escolha do mecanismo de passagem</span><span class="sxs-lookup"><span data-stu-id="09e82-113">Choice of Passing Mechanism</span></span>  
 <span data-ttu-id="09e82-114">Você deve escolher cuidadosamente para cada argumento, o mecanismo de passagem.</span><span class="sxs-lookup"><span data-stu-id="09e82-114">You should choose the passing mechanism carefully for each argument.</span></span>  
  
-   <span data-ttu-id="09e82-115">**Proteção**.</span><span class="sxs-lookup"><span data-stu-id="09e82-115">**Protection**.</span></span> <span data-ttu-id="09e82-116">Escolher entre os mecanismos de passagem de dois, o critério mais importante é a exposição de chamar a variável para alterar.</span><span class="sxs-lookup"><span data-stu-id="09e82-116">In choosing between the two passing mechanisms, the most important criterion is the exposure of calling variables to change.</span></span> <span data-ttu-id="09e82-117">A vantagem de passar um argumento `ByRef` é que o procedimento pode retornar um valor para o código de chamada através desse argumento.</span><span class="sxs-lookup"><span data-stu-id="09e82-117">The advantage of passing an argument `ByRef` is that the procedure can return a value to the calling code through that argument.</span></span> <span data-ttu-id="09e82-118">A vantagem de passar um argumento `ByVal` é que ele protege uma variável que está sendo alterada pelo procedimento.</span><span class="sxs-lookup"><span data-stu-id="09e82-118">The advantage of passing an argument `ByVal` is that it protects a variable from being changed by the procedure.</span></span>  
  
-   <span data-ttu-id="09e82-119">**Desempenho**.</span><span class="sxs-lookup"><span data-stu-id="09e82-119">**Performance**.</span></span> <span data-ttu-id="09e82-120">Embora o mecanismo de passagem pode afetar o desempenho do seu código, a diferença é geralmente é insignificante.</span><span class="sxs-lookup"><span data-stu-id="09e82-120">Although the passing mechanism can affect the performance of your code, the difference is usually insignificant.</span></span> <span data-ttu-id="09e82-121">Uma exceção a isso é um tipo de valor passado `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="09e82-121">One exception to this is a value type passed `ByVal`.</span></span> <span data-ttu-id="09e82-122">Nesse caso, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copia o conteúdo de todo o data do argumento.</span><span class="sxs-lookup"><span data-stu-id="09e82-122">In this case, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copies the entire data contents of the argument.</span></span> <span data-ttu-id="09e82-123">Portanto, para um tipo de valor grande, como uma estrutura, ele pode ser mais eficiente para passá-lo `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="09e82-123">Therefore, for a large value type such as a structure, it can be more efficient to pass it `ByRef`.</span></span>  
  
     <span data-ttu-id="09e82-124">Para tipos de referência, somente o ponteiro para os dados é copiados (quatro bytes em plataformas de 32 bits, oito bytes em plataformas de 64 bits).</span><span class="sxs-lookup"><span data-stu-id="09e82-124">For reference types, only the pointer to the data is copied (four bytes on 32-bit platforms, eight bytes on 64-bit platforms).</span></span> <span data-ttu-id="09e82-125">Portanto, você pode passar argumentos de tipo `String` ou `Object` por valor sem prejudicar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="09e82-125">Therefore, you can pass arguments of type `String` or `Object` by value without harming performance.</span></span>  
  
## <a name="determination-of-the-passing-mechanism"></a><span data-ttu-id="09e82-126">Determinação do mecanismo de passagem</span><span class="sxs-lookup"><span data-stu-id="09e82-126">Determination of the Passing Mechanism</span></span>  
 <span data-ttu-id="09e82-127">A declaração de procedimento especifica o mecanismo de passagem de cada parâmetro.</span><span class="sxs-lookup"><span data-stu-id="09e82-127">The procedure declaration specifies the passing mechanism for each parameter.</span></span> <span data-ttu-id="09e82-128">O código de chamada não pode substituir um `ByVal` mecanismo.</span><span class="sxs-lookup"><span data-stu-id="09e82-128">The calling code can't override a `ByVal` mechanism.</span></span>  
  
 <span data-ttu-id="09e82-129">Se um parâmetro é declarado com `ByRef`, o código de chamada pode forçar o mecanismo para `ByVal` colocando o nome do argumento entre parênteses na chamada.</span><span class="sxs-lookup"><span data-stu-id="09e82-129">If a parameter is declared with `ByRef`, the calling code can force the mechanism to `ByVal` by enclosing the argument name in parentheses in the call.</span></span> <span data-ttu-id="09e82-130">Para obter mais informações, consulte [como: forçar um argumento a ser passado por valor](./how-to-force-an-argument-to-be-passed-by-value.md).</span><span class="sxs-lookup"><span data-stu-id="09e82-130">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
 <span data-ttu-id="09e82-131">O padrão no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] é passar argumentos por valor.</span><span class="sxs-lookup"><span data-stu-id="09e82-131">The default in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] is to pass arguments by value.</span></span>  
  
## <a name="when-to-pass-an-argument-by-value"></a><span data-ttu-id="09e82-132">Quando passar um argumento por valor</span><span class="sxs-lookup"><span data-stu-id="09e82-132">When to Pass an Argument by Value</span></span>  
  
-   <span data-ttu-id="09e82-133">Se o elemento de código chamada subjacente o argumento é um elemento não modificável, declare o parâmetro correspondente [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="09e82-133">If the calling code element underlying the argument is a nonmodifiable element, declare the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="09e82-134">Nenhum código pode alterar o valor de um elemento não modificável.</span><span class="sxs-lookup"><span data-stu-id="09e82-134">No code can change the value of a nonmodifiable element.</span></span>  
  
-   <span data-ttu-id="09e82-135">Se o elemento base é modificável, mas você não quiser que o procedimento seja capaz de alterar seu valor, declare o parâmetro `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="09e82-135">If the underlying element is modifiable, but you do not want the procedure to be able to change its value, declare the parameter `ByVal`.</span></span> <span data-ttu-id="09e82-136">Somente o código de chamada pode alterar o valor de um elemento modificável passado por valor.</span><span class="sxs-lookup"><span data-stu-id="09e82-136">Only the calling code can change the value of a modifiable element passed by value.</span></span>  
  
## <a name="when-to-pass-an-argument-by-reference"></a><span data-ttu-id="09e82-137">Quando você passar um argumento por referência</span><span class="sxs-lookup"><span data-stu-id="09e82-137">When to Pass an Argument by Reference</span></span>  
  
-   <span data-ttu-id="09e82-138">Se o procedimento tenha uma necessidade original para alterar o elemento subjacente no código de chamada, declare o parâmetro correspondente [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span><span class="sxs-lookup"><span data-stu-id="09e82-138">If the procedure has a genuine need to change the underlying element in the calling code, declare the corresponding parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span>  
  
-   <span data-ttu-id="09e82-139">Se a execução correta do código depende do procedimento alterar o elemento subjacente no código de chamada, declare o parâmetro `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="09e82-139">If the correct execution of the code depends on the procedure changing the underlying element in the calling code, declare the parameter `ByRef`.</span></span> <span data-ttu-id="09e82-140">Se você a passar por valor, ou se o código de chamada substitui o `ByRef` mecanismo de passagem, colocando o argumento entre parênteses, a chamada de procedimento pode produzir resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="09e82-140">If you pass it by value, or if the calling code overrides the `ByRef` passing mechanism by enclosing the argument in parentheses, the procedure call might produce unexpected results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09e82-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09e82-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="09e82-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="09e82-142">Description</span></span>  
 <span data-ttu-id="09e82-143">O exemplo a seguir ilustra quando passar argumentos por valor e passá-los por referência.</span><span class="sxs-lookup"><span data-stu-id="09e82-143">The following example illustrates when to pass arguments by value and when to pass them by reference.</span></span> <span data-ttu-id="09e82-144">Procedimento `Calculate` tem um `ByVal` e um `ByRef` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="09e82-144">Procedure `Calculate` has both a `ByVal` and a `ByRef` parameter.</span></span> <span data-ttu-id="09e82-145">Dada uma taxa de juros, `rate`e uma soma de dinheiro, `debt`, é calcular um novo valor para a tarefa do procedimento `debt` que é o resultado da aplicação a taxa de juros para o valor original de `debt`.</span><span class="sxs-lookup"><span data-stu-id="09e82-145">Given an interest rate, `rate`, and a sum of money, `debt`, the task of the procedure is to calculate a new value for `debt` that is the result of applying the interest rate to the original value of `debt`.</span></span> <span data-ttu-id="09e82-146">Porque `debt` é um `ByRef` parâmetro, o novo total será refletido no valor do argumento no código de chamada que corresponde a `debt`.</span><span class="sxs-lookup"><span data-stu-id="09e82-146">Because `debt` is a `ByRef` parameter, the new total is reflected in the value of the argument in the calling code that corresponds to `debt`.</span></span> <span data-ttu-id="09e82-147">Parâmetro `rate` é um `ByVal` parâmetro porque `Calculate` não deve alterar seu valor.</span><span class="sxs-lookup"><span data-stu-id="09e82-147">Parameter `rate` is a `ByVal` parameter because `Calculate` should not change its value.</span></span>  
  
### <a name="code"></a><span data-ttu-id="09e82-148">Código</span><span class="sxs-lookup"><span data-stu-id="09e82-148">Code</span></span>  
 <span data-ttu-id="09e82-149">[!code-vb[VbVbcnProcedures&#74;](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="09e82-149">[!code-vb[VbVbcnProcedures#74](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09e82-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09e82-150">See Also</span></span>  
 <span data-ttu-id="09e82-151">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="09e82-151">[Procedures](./index.md) </span></span>  
<span data-ttu-id="09e82-152"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="09e82-152"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="09e82-153"> [Como: passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="09e82-153"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="09e82-154"> [Como: alterar o valor de um argumento de procedimento](./how-to-change-the-value-of-a-procedure-argument.md) </span><span class="sxs-lookup"><span data-stu-id="09e82-154"> [How to: Change the Value of a Procedure Argument](./how-to-change-the-value-of-a-procedure-argument.md) </span></span>  
<span data-ttu-id="09e82-155"> [Como: proteger um argumento de procedimento contra alterações de valor](./how-to-protect-a-procedure-argument-against-value-changes.md) </span><span class="sxs-lookup"><span data-stu-id="09e82-155"> [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md) </span></span>  
<span data-ttu-id="09e82-156"> [Como: forçar um argumento a ser passado por valor](./how-to-force-an-argument-to-be-passed-by-value.md) </span><span class="sxs-lookup"><span data-stu-id="09e82-156"> [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md) </span></span>  
<span data-ttu-id="09e82-157"> [Passando argumentos por posição e nome](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="09e82-157"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="09e82-158"> [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="09e82-158"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
