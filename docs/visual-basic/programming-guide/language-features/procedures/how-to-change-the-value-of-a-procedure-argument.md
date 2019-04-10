---
title: 'Como: Altere o valor de um argumento de procedimento (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
ms.openlocfilehash: a56bdf888163c9559b87e857abb33522c547ed45
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316616"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="1560b-102">Como: Altere o valor de um argumento de procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1560b-102">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>
<span data-ttu-id="1560b-103">Quando você chama um procedimento, cada argumento que você fornecer corresponde a um dos parâmetros definidos no procedimento.</span><span class="sxs-lookup"><span data-stu-id="1560b-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="1560b-104">Em alguns casos, o código do procedimento pode alterar o valor subjacente de um argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="1560b-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="1560b-105">Em outros casos, o procedimento pode alterar apenas sua cópia local de um argumento.</span><span class="sxs-lookup"><span data-stu-id="1560b-105">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="1560b-106">Quando você chama o procedimento, o Visual Basic faz uma cópia local de cada argumento que é passado [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="1560b-106">When you call the procedure, Visual Basic makes a local copy of every argument that is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="1560b-107">Para cada argumento passado [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic fornece o código do procedimento uma referência direta ao elemento de programação subjacente do argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="1560b-107">For each argument passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="1560b-108">Se o elemento base no código de chamada é um elemento modificável e o argumento é passado `ByRef`, o código do procedimento pode usar a referência direta para alterar o valor do elemento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="1560b-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="1560b-109">Alterando o valor subjacente</span><span class="sxs-lookup"><span data-stu-id="1560b-109">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="1560b-110">Para alterar o valor subjacente de um argumento de procedimento no código de chamada</span><span class="sxs-lookup"><span data-stu-id="1560b-110">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1. <span data-ttu-id="1560b-111">Na declaração do procedimento, especifique [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) para o parâmetro correspondente ao argumento.</span><span class="sxs-lookup"><span data-stu-id="1560b-111">In the procedure declaration, specify [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2. <span data-ttu-id="1560b-112">No código de chamada, passe um elemento de programação modificável como o argumento.</span><span class="sxs-lookup"><span data-stu-id="1560b-112">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3. <span data-ttu-id="1560b-113">No código de chamada, não coloque o argumento entre parênteses na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="1560b-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4. <span data-ttu-id="1560b-114">No código do procedimento, use o nome do parâmetro para atribuir um valor para o elemento base no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="1560b-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="1560b-115">Veja o exemplo mais adiante, para ver uma demonstração.</span><span class="sxs-lookup"><span data-stu-id="1560b-115">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="1560b-116">Alterando cópias locais</span><span class="sxs-lookup"><span data-stu-id="1560b-116">Changing Local Copies</span></span>  
 <span data-ttu-id="1560b-117">Se o elemento base no código de chamada é um elemento não modificável, ou se o argumento é passado `ByVal`, o procedimento não pode alterar seu valor no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="1560b-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="1560b-118">No entanto, o procedimento pode alterar sua cópia local de um argumento.</span><span class="sxs-lookup"><span data-stu-id="1560b-118">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="1560b-119">Para alterar a cópia de um argumento de procedimento no código do procedimento</span><span class="sxs-lookup"><span data-stu-id="1560b-119">To change the copy of a procedure argument in the procedure code</span></span>  
  
1. <span data-ttu-id="1560b-120">Na declaração do procedimento, especifique [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) para o parâmetro correspondente ao argumento.</span><span class="sxs-lookup"><span data-stu-id="1560b-120">In the procedure declaration, specify [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="1560b-121">- ou -</span><span class="sxs-lookup"><span data-stu-id="1560b-121">-or-</span></span>  
  
     <span data-ttu-id="1560b-122">No código de chamada, coloque o argumento entre parênteses na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="1560b-122">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="1560b-123">Isso força o Visual Basic para passar o argumento por valor, mesmo se o parâmetro correspondente especifica `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="1560b-123">This forces Visual Basic to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2. <span data-ttu-id="1560b-124">No código do procedimento, use o nome do parâmetro para atribuir um valor para a cópia local do argumento.</span><span class="sxs-lookup"><span data-stu-id="1560b-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="1560b-125">O valor subjacente no código de chamada não é alterado.</span><span class="sxs-lookup"><span data-stu-id="1560b-125">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1560b-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1560b-126">Example</span></span>  
 <span data-ttu-id="1560b-127">O exemplo a seguir mostra dois procedimentos que têm uma variável de matriz e operam em seus elementos.</span><span class="sxs-lookup"><span data-stu-id="1560b-127">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="1560b-128">O procedimento `increase` simplesmente adiciona um para cada elemento.</span><span class="sxs-lookup"><span data-stu-id="1560b-128">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="1560b-129">O procedimento `replace` atribui uma nova matriz para o parâmetro `a()` e, em seguida, adiciona um para cada elemento.</span><span class="sxs-lookup"><span data-stu-id="1560b-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 <span data-ttu-id="1560b-130">A primeira `MsgBox` chamada exibe "após increase (n): 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="1560b-130">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="1560b-131">Porque a matriz `n` é um tipo de referência `replace` podem alterar seus membros, mesmo que o mecanismo de passagem é `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="1560b-131">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="1560b-132">O segundo `MsgBox` chamada exibe "Após Replace (n): 101, 201, 301".</span><span class="sxs-lookup"><span data-stu-id="1560b-132">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="1560b-133">Porque `n` é passado `ByRef`, `replace` pode modificar a variável `n` no código de chamada e atribuir uma nova matriz a ela.</span><span class="sxs-lookup"><span data-stu-id="1560b-133">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="1560b-134">Porque `n` é um tipo de referência, `replace` também pode alterar seus membros.</span><span class="sxs-lookup"><span data-stu-id="1560b-134">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="1560b-135">Você pode impedir que o procedimento a modificar a variável no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="1560b-135">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="1560b-136">Confira [Como Proteger um argumento de procedimento contra alterações de valor](./how-to-protect-a-procedure-argument-against-value-changes.md).</span><span class="sxs-lookup"><span data-stu-id="1560b-136">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1560b-137">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="1560b-137">Compiling the Code</span></span>  
 <span data-ttu-id="1560b-138">Quando você passa uma variável por referência, você deve usar o `ByRef` palavra-chave para especificar esse mecanismo.</span><span class="sxs-lookup"><span data-stu-id="1560b-138">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="1560b-139">É o padrão no Visual Basic passar argumentos por valor.</span><span class="sxs-lookup"><span data-stu-id="1560b-139">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="1560b-140">No entanto, é uma boa prática de programação incluir as palavras-chave [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) em cada parâmetro declarado.</span><span class="sxs-lookup"><span data-stu-id="1560b-140">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="1560b-141">Isso torna o código mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="1560b-141">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1560b-142">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1560b-142">.NET Framework Security</span></span>  
 <span data-ttu-id="1560b-143">Sempre há um risco potencial em permitir que um procedimento para alterar o valor subjacente de um argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="1560b-143">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="1560b-144">Verifique se você espera que esse valor a ser alterado e esteja preparado para verificá-lo quanto à validade antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="1560b-144">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1560b-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1560b-145">See also</span></span>

- [<span data-ttu-id="1560b-146">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="1560b-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="1560b-147">Parâmetros e argumentos de procedimento</span><span class="sxs-lookup"><span data-stu-id="1560b-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="1560b-148">Como: passar argumentos para um procedimento</span><span class="sxs-lookup"><span data-stu-id="1560b-148">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="1560b-149">Passar argumentos por valor e por referência</span><span class="sxs-lookup"><span data-stu-id="1560b-149">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="1560b-150">Diferenças entre argumentos modificáveis e não modificáveis</span><span class="sxs-lookup"><span data-stu-id="1560b-150">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="1560b-151">Diferenças entre passar um argumento por valor e por referência</span><span class="sxs-lookup"><span data-stu-id="1560b-151">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="1560b-152">Como: proteger um argumento de procedimento contra alterações de valor</span><span class="sxs-lookup"><span data-stu-id="1560b-152">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="1560b-153">Como: forçar um argumento a ser passado por valor</span><span class="sxs-lookup"><span data-stu-id="1560b-153">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="1560b-154">Passar argumentos por posição e nome</span><span class="sxs-lookup"><span data-stu-id="1560b-154">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="1560b-155">Tipos de valor e referência</span><span class="sxs-lookup"><span data-stu-id="1560b-155">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
