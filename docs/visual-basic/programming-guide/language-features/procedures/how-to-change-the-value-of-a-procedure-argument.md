---
title: 'Como: alterar o valor de um argumento de procedimento (Visual Basic) | Documentos do Microsoft'
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
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
caps.latest.revision: 16
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
ms.openlocfilehash: 3f192d738ca2753cd12b6fffca1f4f94a606a42c
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="33301-102">Como alterar o valor de um argumento de procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33301-102">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>
<span data-ttu-id="33301-103">Quando você chama um procedimento, cada argumento que você fornecer corresponde a um dos parâmetros definidos no procedimento.</span><span class="sxs-lookup"><span data-stu-id="33301-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="33301-104">Em alguns casos, o código do procedimento pode alterar o valor subjacente um argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="33301-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="33301-105">Em outros casos, o procedimento pode alterar apenas sua cópia local de um argumento.</span><span class="sxs-lookup"><span data-stu-id="33301-105">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="33301-106">Quando você chama o procedimento [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] faz uma cópia local de cada argumento que é passado [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="33301-106">When you call the procedure, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] makes a local copy of every argument that is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="33301-107">Para cada argumento passado [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece o código do procedimento uma referência direta ao elemento de programação subjacente o argumento o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="33301-107">For each argument passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="33301-108">Se o elemento base no código de chamada é um elemento modificável e o argumento é passado `ByRef`, o código do procedimento pode usar a referência direta para alterar o valor do elemento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="33301-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="33301-109">Alterar o valor subjacente</span><span class="sxs-lookup"><span data-stu-id="33301-109">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="33301-110">Para alterar o valor subjacente de um argumento de procedimento no código de chamada</span><span class="sxs-lookup"><span data-stu-id="33301-110">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1.  <span data-ttu-id="33301-111">Na declaração do procedimento, especifique [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) para o parâmetro correspondente ao argumento.</span><span class="sxs-lookup"><span data-stu-id="33301-111">In the procedure declaration, specify [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2.  <span data-ttu-id="33301-112">No código de chamada, passe um elemento de programação modificável como o argumento.</span><span class="sxs-lookup"><span data-stu-id="33301-112">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3.  <span data-ttu-id="33301-113">No código de chamada, não coloque o argumento entre parênteses na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="33301-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4.  <span data-ttu-id="33301-114">No código do procedimento, use o nome do parâmetro para atribuir um valor para o elemento base no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="33301-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="33301-115">Consulte o exemplo mais para baixo para ver uma demonstração.</span><span class="sxs-lookup"><span data-stu-id="33301-115">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="33301-116">Alterando cópias locais</span><span class="sxs-lookup"><span data-stu-id="33301-116">Changing Local Copies</span></span>  
 <span data-ttu-id="33301-117">Se o elemento base no código de chamada é um elemento não modificável, ou se o argumento é passado `ByVal`, o procedimento não pode alterar o valor no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="33301-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="33301-118">No entanto, o procedimento pode alterar sua cópia local de um argumento.</span><span class="sxs-lookup"><span data-stu-id="33301-118">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="33301-119">Para alterar a cópia de um argumento de procedimento no código de procedimento</span><span class="sxs-lookup"><span data-stu-id="33301-119">To change the copy of a procedure argument in the procedure code</span></span>  
  
1.  <span data-ttu-id="33301-120">Na declaração do procedimento, especifique [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) para o parâmetro correspondente ao argumento.</span><span class="sxs-lookup"><span data-stu-id="33301-120">In the procedure declaration, specify [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="33301-121">-ou-</span><span class="sxs-lookup"><span data-stu-id="33301-121">-or-</span></span>  
  
     <span data-ttu-id="33301-122">No código de chamada, coloque o argumento entre parênteses na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="33301-122">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="33301-123">Isso força [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] para passar o argumento por valor, mesmo se o parâmetro correspondente especifica `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="33301-123">This forces [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2.  <span data-ttu-id="33301-124">No código do procedimento, use o nome do parâmetro para atribuir um valor para a cópia local do argumento.</span><span class="sxs-lookup"><span data-stu-id="33301-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="33301-125">O valor subjacente no código de chamada não é alterado.</span><span class="sxs-lookup"><span data-stu-id="33301-125">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33301-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="33301-126">Example</span></span>  
 <span data-ttu-id="33301-127">O exemplo a seguir mostra dois procedimentos que tenham uma variável de matriz e operam em seus elementos.</span><span class="sxs-lookup"><span data-stu-id="33301-127">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="33301-128">O `increase` procedimento simplesmente adiciona um para cada elemento.</span><span class="sxs-lookup"><span data-stu-id="33301-128">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="33301-129">O `replace` procedimento atribui uma nova matriz para o parâmetro `a()` e, em seguida, adiciona um para cada elemento.</span><span class="sxs-lookup"><span data-stu-id="33301-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 <span data-ttu-id="33301-130">[!code-vb[VbVbcnProcedures&#35;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="33301-130">[!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]</span></span>  
  
 <span data-ttu-id="33301-131">[!code-vb[VbVbcnProcedures&#36;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="33301-131">[!code-vb[VbVbcnProcedures#36](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]</span></span>  
  
 <span data-ttu-id="33301-132">[!code-vb[VbVbcnProcedures&#37;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="33301-132">[!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]</span></span>  
  
 <span data-ttu-id="33301-133">A primeira `MsgBox` chamada exibe "após increase (n): 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="33301-133">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="33301-134">Porque a matriz `n` é um tipo de referência, `replace` pode alterar seus membros, mesmo que o mecanismo de passagem é `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="33301-134">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="33301-135">O segundo `MsgBox` chamada exibe "Após Replace (n): 101, 201, 301".</span><span class="sxs-lookup"><span data-stu-id="33301-135">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="33301-136">Porque `n` é passado `ByRef`, `replace` pode modificar a variável `n` no código de chamada e atribuir uma nova matriz para ele.</span><span class="sxs-lookup"><span data-stu-id="33301-136">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="33301-137">Porque `n` é um tipo de referência, `replace` também pode alterar seus membros.</span><span class="sxs-lookup"><span data-stu-id="33301-137">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="33301-138">Você pode impedir que o procedimento modificar a variável no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="33301-138">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="33301-139">Consulte [como: proteger um argumento de procedimento contra alterações de valor](./how-to-protect-a-procedure-argument-against-value-changes.md).</span><span class="sxs-lookup"><span data-stu-id="33301-139">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="33301-140">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="33301-140">Compiling the Code</span></span>  
 <span data-ttu-id="33301-141">Quando uma variável é passada por referência, você deve usar o `ByRef` palavra-chave para especificar esse mecanismo.</span><span class="sxs-lookup"><span data-stu-id="33301-141">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="33301-142">O padrão no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] é passar argumentos por valor.</span><span class="sxs-lookup"><span data-stu-id="33301-142">The default in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="33301-143">No entanto, é boa prática incluir de programação a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) palavra-chave com cada parâmetro declarado.</span><span class="sxs-lookup"><span data-stu-id="33301-143">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="33301-144">Isso torna seu código mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="33301-144">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="33301-145">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="33301-145">.NET Framework Security</span></span>  
 <span data-ttu-id="33301-146">Sempre há um risco potencial em permitir que um procedimento alterar o valor subjacente um argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="33301-146">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="33301-147">Verifique se você espera que esse valor seja alterado e esteja preparado para verificá-lo para validade antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="33301-147">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33301-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33301-148">See Also</span></span>  
 <span data-ttu-id="33301-149">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="33301-149">[Procedures](./index.md) </span></span>  
<span data-ttu-id="33301-150"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="33301-150"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="33301-151"> [Como: passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="33301-151"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="33301-152"> [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="33301-152"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="33301-153"> [Diferenças entre argumentos modificável e não modificável](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="33301-153"> [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span></span>  
<span data-ttu-id="33301-154"> [Diferenças entre passar um argumento por valor e por referência](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="33301-154"> [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="33301-155"> [Como: proteger um argumento de procedimento contra alterações de valor](./how-to-protect-a-procedure-argument-against-value-changes.md) </span><span class="sxs-lookup"><span data-stu-id="33301-155"> [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md) </span></span>  
<span data-ttu-id="33301-156"> [Como: forçar um argumento a ser passado por valor](./how-to-force-an-argument-to-be-passed-by-value.md) </span><span class="sxs-lookup"><span data-stu-id="33301-156"> [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md) </span></span>  
<span data-ttu-id="33301-157"> [Passando argumentos por posição e nome](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="33301-157"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="33301-158"> [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="33301-158"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
