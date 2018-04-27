---
title: Como proteger um argumento de procedimento contra alterações de valor (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59c0486bd9543167e4c17a3109c4b89b3502e80e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a><span data-ttu-id="80e9c-102">Como proteger um argumento de procedimento contra alterações de valor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80e9c-102">How to: Protect a Procedure Argument Against Value Changes (Visual Basic)</span></span>
<span data-ttu-id="80e9c-103">Se um procedimento declara um parâmetro como [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic fornece o código do procedimento uma referência direta para o elemento de programação subjacente do argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="80e9c-103">If a procedure declares a parameter as [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="80e9c-104">Isso permite que o procedimento para alterar o valor subjacente do argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="80e9c-104">This permits the procedure to change the value underlying the argument in the calling code.</span></span> <span data-ttu-id="80e9c-105">Em alguns casos, o código de chamada talvez queira proteger contra essa alteração.</span><span class="sxs-lookup"><span data-stu-id="80e9c-105">In some cases the calling code might want to protect against such a change.</span></span>  
  
 <span data-ttu-id="80e9c-106">Você sempre pode proteger um argumento de alteração, declarando o parâmetro correspondente [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) no procedimento.</span><span class="sxs-lookup"><span data-stu-id="80e9c-106">You can always protect an argument from change by declaring the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) in the procedure.</span></span> <span data-ttu-id="80e9c-107">Se desejar alterar um argumento fornecido em alguns casos, mas outros não, você pode declará-la `ByRef` e permitir que o código de chamada determinar o mecanismo de passagem em cada chamada.</span><span class="sxs-lookup"><span data-stu-id="80e9c-107">If you want to be able to change a given argument in some cases but not others, you can declare it `ByRef` and let the calling code determine the passing mechanism in each call.</span></span> <span data-ttu-id="80e9c-108">Ele faz isso colocando o argumento correspondente entre parênteses para passá-lo por valor ou não envolve em parênteses para passá-lo por referência.</span><span class="sxs-lookup"><span data-stu-id="80e9c-108">It does this by enclosing the corresponding argument in parentheses to pass it by value, or not enclosing it in parentheses to pass it by reference.</span></span> <span data-ttu-id="80e9c-109">Para obter mais informações, consulte [como: forçar um argumento a ser passado por valor](./how-to-force-an-argument-to-be-passed-by-value.md).</span><span class="sxs-lookup"><span data-stu-id="80e9c-109">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80e9c-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="80e9c-110">Example</span></span>  
 <span data-ttu-id="80e9c-111">O exemplo a seguir mostra dois procedimentos que tenham uma variável de matriz e operam em seus elementos.</span><span class="sxs-lookup"><span data-stu-id="80e9c-111">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="80e9c-112">O `increase` procedimento simplesmente adiciona um para cada elemento.</span><span class="sxs-lookup"><span data-stu-id="80e9c-112">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="80e9c-113">O `replace` procedimento atribui uma nova matriz para o parâmetro `a()` e, em seguida, adiciona um para cada elemento.</span><span class="sxs-lookup"><span data-stu-id="80e9c-113">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="80e9c-114">No entanto, a reatribuição não afeta a variável array subjacente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="80e9c-114">However, the reassignment does not affect the underlying array variable in the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 <span data-ttu-id="80e9c-115">A primeira `MsgBox` chamada exibe "após increase (n): 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="80e9c-115">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="80e9c-116">Porque a matriz `n` é um tipo de referência, `replace` pode alterar seus membros, mesmo que o mecanismo de passagem é `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="80e9c-116">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="80e9c-117">O segundo `MsgBox` chamada exibe "Após Replace (n): 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="80e9c-117">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="80e9c-118">Porque `n` é passado `ByVal`, `replace` não é possível modificar a variável `n` no código de chamada atribuindo uma nova matriz.</span><span class="sxs-lookup"><span data-stu-id="80e9c-118">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` in the calling code by assigning a new array to it.</span></span> <span data-ttu-id="80e9c-119">Quando `replace` cria a nova instância de matriz `k` e o atribui à variável local `a`, ele perde a referência à `n` passado pelo código de chamada.</span><span class="sxs-lookup"><span data-stu-id="80e9c-119">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="80e9c-120">Quando ele é alterado os membros de `a`, somente a matriz local `k` é afetado.</span><span class="sxs-lookup"><span data-stu-id="80e9c-120">When it changes the members of `a`, only the local array `k` is affected.</span></span> <span data-ttu-id="80e9c-121">Portanto, `replace` não incrementa os valores de matriz `n` no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="80e9c-121">Therefore, `replace` does not increment the values of array `n` in the calling code.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="80e9c-122">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="80e9c-122">Compiling the Code</span></span>  
 <span data-ttu-id="80e9c-123">O padrão no Visual Basic é passar argumentos por valor.</span><span class="sxs-lookup"><span data-stu-id="80e9c-123">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="80e9c-124">No entanto, é uma boa prática para incluir qualquer um de programação de [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) palavra-chave com cada parâmetro declarado.</span><span class="sxs-lookup"><span data-stu-id="80e9c-124">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="80e9c-125">Isso facilita a leitura do seu código.</span><span class="sxs-lookup"><span data-stu-id="80e9c-125">This makes your code easier to read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e9c-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80e9c-126">See Also</span></span>  
 [<span data-ttu-id="80e9c-127">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="80e9c-127">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="80e9c-128">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="80e9c-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="80e9c-129">Como passar argumentos para um procedimento</span><span class="sxs-lookup"><span data-stu-id="80e9c-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="80e9c-130">Passando Argumentos por Valor e por Referência</span><span class="sxs-lookup"><span data-stu-id="80e9c-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="80e9c-131">Diferenças entre argumentos modificáveis e não modificáveis</span><span class="sxs-lookup"><span data-stu-id="80e9c-131">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [<span data-ttu-id="80e9c-132">Diferenças entre passar um argumento por valor e por referência</span><span class="sxs-lookup"><span data-stu-id="80e9c-132">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="80e9c-133">Como alterar o valor de um argumento de procedimento</span><span class="sxs-lookup"><span data-stu-id="80e9c-133">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)  
 [<span data-ttu-id="80e9c-134">Como forçar um argumento a ser passado por Valor</span><span class="sxs-lookup"><span data-stu-id="80e9c-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [<span data-ttu-id="80e9c-135">Passando Argumentos por Posição e Nome</span><span class="sxs-lookup"><span data-stu-id="80e9c-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="80e9c-136">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="80e9c-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
