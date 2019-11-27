---
title: Como alterar o valor de um argumento de procedimento
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
ms.openlocfilehash: e562c0f5ec01380c792b4dc064554171cfb007e7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74339956"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="02e16-102">Como alterar o valor de um argumento de procedimento (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02e16-102">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>
<span data-ttu-id="02e16-103">Quando você chama um procedimento, cada argumento fornecido corresponde a um dos parâmetros definidos no procedimento.</span><span class="sxs-lookup"><span data-stu-id="02e16-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="02e16-104">Em alguns casos, o código do procedimento pode alterar o valor subjacente a um argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="02e16-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="02e16-105">Em outros casos, o procedimento pode alterar apenas sua cópia local de um argumento.</span><span class="sxs-lookup"><span data-stu-id="02e16-105">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="02e16-106">Quando você chama o procedimento, Visual Basic faz uma cópia local de cada argumento passado por [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="02e16-106">When you call the procedure, Visual Basic makes a local copy of every argument that is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="02e16-107">Para cada argumento passado por [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic dá ao código do procedimento uma referência direta para o elemento de programação subjacente ao argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="02e16-107">For each argument passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="02e16-108">Se o elemento subjacente no código de chamada for um elemento modificável e o argumento for passado `ByRef`, o código do procedimento poderá usar a referência direta para alterar o valor do elemento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="02e16-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="02e16-109">Alterando o valor subjacente</span><span class="sxs-lookup"><span data-stu-id="02e16-109">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="02e16-110">Para alterar o valor subjacente de um argumento de procedimento no código de chamada</span><span class="sxs-lookup"><span data-stu-id="02e16-110">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1. <span data-ttu-id="02e16-111">Na declaração de procedimento, especifique [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) para o parâmetro correspondente ao argumento.</span><span class="sxs-lookup"><span data-stu-id="02e16-111">In the procedure declaration, specify [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2. <span data-ttu-id="02e16-112">No código de chamada, passe um elemento de programação modificável como o argumento.</span><span class="sxs-lookup"><span data-stu-id="02e16-112">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3. <span data-ttu-id="02e16-113">No código de chamada, não coloque o argumento entre parênteses na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="02e16-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4. <span data-ttu-id="02e16-114">No código do procedimento, use o nome do parâmetro para atribuir um valor ao elemento subjacente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="02e16-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="02e16-115">Veja o exemplo mais abaixo para ver uma demonstração.</span><span class="sxs-lookup"><span data-stu-id="02e16-115">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="02e16-116">Alterando cópias locais</span><span class="sxs-lookup"><span data-stu-id="02e16-116">Changing Local Copies</span></span>  
 <span data-ttu-id="02e16-117">Se o elemento subjacente no código de chamada for um elemento não modificável ou se o argumento for passado `ByVal`, o procedimento não poderá alterar seu valor no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="02e16-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="02e16-118">No entanto, o procedimento pode alterar sua cópia local desse argumento.</span><span class="sxs-lookup"><span data-stu-id="02e16-118">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="02e16-119">Para alterar a cópia de um argumento de procedimento no código do procedimento</span><span class="sxs-lookup"><span data-stu-id="02e16-119">To change the copy of a procedure argument in the procedure code</span></span>  
  
1. <span data-ttu-id="02e16-120">Na declaração de procedimento, especifique [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) para o parâmetro correspondente ao argumento.</span><span class="sxs-lookup"><span data-stu-id="02e16-120">In the procedure declaration, specify [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="02e16-121">- ou -</span><span class="sxs-lookup"><span data-stu-id="02e16-121">-or-</span></span>  
  
     <span data-ttu-id="02e16-122">No código de chamada, coloque o argumento entre parênteses na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="02e16-122">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="02e16-123">Isso força Visual Basic a passar o argumento por valor, mesmo se o parâmetro correspondente especificar `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="02e16-123">This forces Visual Basic to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2. <span data-ttu-id="02e16-124">No código do procedimento, use o nome do parâmetro para atribuir um valor à cópia local do argumento.</span><span class="sxs-lookup"><span data-stu-id="02e16-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="02e16-125">O valor subjacente no código de chamada não é alterado.</span><span class="sxs-lookup"><span data-stu-id="02e16-125">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02e16-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="02e16-126">Example</span></span>  
 <span data-ttu-id="02e16-127">O exemplo a seguir mostra dois procedimentos que têm uma variável de matriz e operam em seus elementos.</span><span class="sxs-lookup"><span data-stu-id="02e16-127">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="02e16-128">O procedimento `increase` simplesmente adiciona um a cada elemento.</span><span class="sxs-lookup"><span data-stu-id="02e16-128">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="02e16-129">O procedimento `replace` atribui uma nova matriz ao parâmetro `a()` e, em seguida, adiciona um a cada elemento.</span><span class="sxs-lookup"><span data-stu-id="02e16-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 <span data-ttu-id="02e16-130">A primeira chamada de `MsgBox` exibe "após o aumento (n): 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="02e16-130">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="02e16-131">Como a matriz `n` é um tipo de referência, `replace` pode alterar seus membros, embora o mecanismo de passagem seja `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="02e16-131">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="02e16-132">A segunda chamada de `MsgBox` exibe "após Replace (n): 101, 201, 301".</span><span class="sxs-lookup"><span data-stu-id="02e16-132">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="02e16-133">Como `n` é passado `ByRef`, `replace` pode modificar a variável `n` no código de chamada e atribuir uma nova matriz a ela.</span><span class="sxs-lookup"><span data-stu-id="02e16-133">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="02e16-134">Como `n` é um tipo de referência, `replace` também pode alterar seus membros.</span><span class="sxs-lookup"><span data-stu-id="02e16-134">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="02e16-135">Você pode impedir que o procedimento modifique a variável em si no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="02e16-135">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="02e16-136">Consulte [como: proteger um argumento de procedimento contra alterações de valor](./how-to-protect-a-procedure-argument-against-value-changes.md).</span><span class="sxs-lookup"><span data-stu-id="02e16-136">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="02e16-137">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="02e16-137">Compiling the Code</span></span>  
 <span data-ttu-id="02e16-138">Ao passar uma variável por referência, você deve usar a palavra-chave `ByRef` para especificar esse mecanismo.</span><span class="sxs-lookup"><span data-stu-id="02e16-138">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="02e16-139">O padrão no Visual Basic é passar argumentos por valor.</span><span class="sxs-lookup"><span data-stu-id="02e16-139">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="02e16-140">No entanto, é uma boa prática de programação incluir a palavra-chave [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) com cada parâmetro declarado.</span><span class="sxs-lookup"><span data-stu-id="02e16-140">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="02e16-141">Isso torna seu código mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="02e16-141">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="02e16-142">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="02e16-142">.NET Framework Security</span></span>  
 <span data-ttu-id="02e16-143">Sempre há um risco potencial em permitir que um procedimento altere o valor subjacente a um argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="02e16-143">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="02e16-144">Certifique-se de que você espera que esse valor seja alterado e esteja preparado para verificá-lo quanto à validade antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="02e16-144">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02e16-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02e16-145">See also</span></span>

- [<span data-ttu-id="02e16-146">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="02e16-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="02e16-147">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="02e16-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="02e16-148">Como passar argumentos para um procedimento</span><span class="sxs-lookup"><span data-stu-id="02e16-148">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="02e16-149">Passando Argumentos por Valor e por Referência</span><span class="sxs-lookup"><span data-stu-id="02e16-149">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="02e16-150">Diferenças entre argumentos modificáveis e não modificáveis</span><span class="sxs-lookup"><span data-stu-id="02e16-150">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="02e16-151">Diferenças entre passar um argumento por valor e por referência</span><span class="sxs-lookup"><span data-stu-id="02e16-151">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="02e16-152">Como proteger um argumento de procedimento contra alterações de valor</span><span class="sxs-lookup"><span data-stu-id="02e16-152">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="02e16-153">Como forçar um argumento a ser passado por Valor</span><span class="sxs-lookup"><span data-stu-id="02e16-153">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="02e16-154">Passando Argumentos por Posição e Nome</span><span class="sxs-lookup"><span data-stu-id="02e16-154">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="02e16-155">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="02e16-155">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
