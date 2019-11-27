---
title: Como forçar um argumento a ser passado por Valor
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: 8261d126f988bdcf05b4a2af3106b38717e46bc8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344524"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="28b5f-102">Como forçar um argumento a ser passado por valor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28b5f-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>
<span data-ttu-id="28b5f-103">A declaração de procedimento determina o mecanismo de passagem.</span><span class="sxs-lookup"><span data-stu-id="28b5f-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="28b5f-104">Se um parâmetro for declarado como [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic esperará passar o argumento correspondente por referência.</span><span class="sxs-lookup"><span data-stu-id="28b5f-104">If a parameter is declared [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="28b5f-105">Isso permite que o procedimento altere o valor do elemento de programação subjacente ao argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="28b5f-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="28b5f-106">Se você deseja proteger o elemento subjacente contra essa alteração, você pode substituir o `ByRef` mecanismo de passagem na chamada de procedimento ao colocar o nome do argumento entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="28b5f-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="28b5f-107">Esses parênteses são além dos parênteses que envolvem a lista de argumentos na chamada.</span><span class="sxs-lookup"><span data-stu-id="28b5f-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="28b5f-108">O código de chamada não pode substituir um mecanismo [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) .</span><span class="sxs-lookup"><span data-stu-id="28b5f-108">The calling code cannot override a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="28b5f-109">Para forçar um argumento a ser passado por valor</span><span class="sxs-lookup"><span data-stu-id="28b5f-109">To force an argument to be passed by value</span></span>  
  
- <span data-ttu-id="28b5f-110">Se o parâmetro correspondente for declarado `ByVal` no procedimento, você não precisará executar etapas adicionais.</span><span class="sxs-lookup"><span data-stu-id="28b5f-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> <span data-ttu-id="28b5f-111">Visual Basic já espera passar o argumento por valor.</span><span class="sxs-lookup"><span data-stu-id="28b5f-111">Visual Basic already expects to pass the argument by value.</span></span>  
  
- <span data-ttu-id="28b5f-112">Se o parâmetro correspondente for declarado `ByRef` no procedimento, coloque o argumento entre parênteses na chamada de procedimento.</span><span class="sxs-lookup"><span data-stu-id="28b5f-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28b5f-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="28b5f-113">Example</span></span>  
 <span data-ttu-id="28b5f-114">O exemplo a seguir substitui uma declaração de parâmetro `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="28b5f-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="28b5f-115">Na chamada que força `ByVal`, observe os dois níveis de parênteses.</span><span class="sxs-lookup"><span data-stu-id="28b5f-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 <span data-ttu-id="28b5f-116">Quando `str` é colocado entre parênteses extras na lista de argumentos, o procedimento de `setNewString` não pode alterar seu valor no código de chamada e `MsgBox` exibe "não pode ser substituído se passado por ByVal".</span><span class="sxs-lookup"><span data-stu-id="28b5f-116">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="28b5f-117">Quando `str` não está entre parênteses extras, o procedimento pode alterá-lo e `MsgBox` exibe "Este é um novo valor para o argumento inString".</span><span class="sxs-lookup"><span data-stu-id="28b5f-117">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="28b5f-118">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="28b5f-118">Compiling the Code</span></span>  
 <span data-ttu-id="28b5f-119">Ao passar uma variável por referência, você deve usar a palavra-chave `ByRef` para especificar esse mecanismo.</span><span class="sxs-lookup"><span data-stu-id="28b5f-119">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="28b5f-120">O padrão no Visual Basic é passar argumentos por valor.</span><span class="sxs-lookup"><span data-stu-id="28b5f-120">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="28b5f-121">No entanto, é uma boa prática de programação incluir a palavra-chave [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) com cada parâmetro declarado.</span><span class="sxs-lookup"><span data-stu-id="28b5f-121">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="28b5f-122">Isso torna seu código mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="28b5f-122">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="28b5f-123">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="28b5f-123">Robust Programming</span></span>  
 <span data-ttu-id="28b5f-124">Se um procedimento declarar um parâmetro [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), a execução correta do código poderá depender da possibilidade de alterar o elemento subjacente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="28b5f-124">If a procedure declares a parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="28b5f-125">Se o código de chamada substituir esse mecanismo de chamada ao colocar o argumento entre parênteses ou se ele passar um argumento não modificável, o procedimento não poderá alterar o elemento subjacente.</span><span class="sxs-lookup"><span data-stu-id="28b5f-125">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="28b5f-126">Isso pode produzir resultados inesperados no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="28b5f-126">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="28b5f-127">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="28b5f-127">.NET Framework Security</span></span>  
 <span data-ttu-id="28b5f-128">Sempre há um risco potencial em permitir que um procedimento altere o valor subjacente a um argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="28b5f-128">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="28b5f-129">Certifique-se de que você espera que esse valor seja alterado e esteja preparado para verificá-lo quanto à validade antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="28b5f-129">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28b5f-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28b5f-130">See also</span></span>

- [<span data-ttu-id="28b5f-131">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="28b5f-131">Procedures</span></span>](./index.md)
- [<span data-ttu-id="28b5f-132">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="28b5f-132">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="28b5f-133">Como passar argumentos para um procedimento</span><span class="sxs-lookup"><span data-stu-id="28b5f-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="28b5f-134">Passando Argumentos por Valor e por Referência</span><span class="sxs-lookup"><span data-stu-id="28b5f-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="28b5f-135">Diferenças entre argumentos modificáveis e não modificáveis</span><span class="sxs-lookup"><span data-stu-id="28b5f-135">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="28b5f-136">Diferenças entre passar um argumento por valor e por referência</span><span class="sxs-lookup"><span data-stu-id="28b5f-136">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="28b5f-137">Como alterar o valor de um argumento de procedimento</span><span class="sxs-lookup"><span data-stu-id="28b5f-137">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="28b5f-138">Como proteger um argumento de procedimento contra alterações de valor</span><span class="sxs-lookup"><span data-stu-id="28b5f-138">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="28b5f-139">Passando Argumentos por Posição e Nome</span><span class="sxs-lookup"><span data-stu-id="28b5f-139">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="28b5f-140">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="28b5f-140">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
