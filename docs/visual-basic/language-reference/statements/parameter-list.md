---
title: "Lista de parâmetros (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c7190b618aa98c91b826ca7c065660d3b19c31a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="18ca8-102">Lista de parâmetros (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18ca8-102">Parameter List (Visual Basic)</span></span>
<span data-ttu-id="18ca8-103">Especifica os parâmetros do procedimento quando é chamado.</span><span class="sxs-lookup"><span data-stu-id="18ca8-103">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="18ca8-104">Vários parâmetros são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="18ca8-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="18ca8-105">A seguir está a sintaxe de um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="18ca8-105">The following is the syntax for one parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18ca8-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="18ca8-106">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a><span data-ttu-id="18ca8-107">Partes</span><span class="sxs-lookup"><span data-stu-id="18ca8-107">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="18ca8-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="18ca8-108">Optional.</span></span> <span data-ttu-id="18ca8-109">Lista de atributos que se aplicam a esse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="18ca8-109">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="18ca8-110">Você deve colocar o [a lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) entre colchetes angulares ("`<`"e"`>`").</span><span class="sxs-lookup"><span data-stu-id="18ca8-110">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
 `Optional`  
 <span data-ttu-id="18ca8-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="18ca8-111">Optional.</span></span> <span data-ttu-id="18ca8-112">Especifica que esse parâmetro não é necessário quando o procedimento é chamado.</span><span class="sxs-lookup"><span data-stu-id="18ca8-112">Specifies that this parameter is not required when the procedure is called.</span></span>  
  
 `ByVal`  
 <span data-ttu-id="18ca8-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="18ca8-113">Optional.</span></span> <span data-ttu-id="18ca8-114">Especifica que o procedimento não é possível substituir ou reatribuir o elemento variável subjacente ao argumento correspondente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="18ca8-114">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>  
  
 `ByRef`  
 <span data-ttu-id="18ca8-115">Opcional.</span><span class="sxs-lookup"><span data-stu-id="18ca8-115">Optional.</span></span> <span data-ttu-id="18ca8-116">Especifica que o procedimento pode modificar o elemento variável subjacente no código de chamada da mesma forma que o código de chamada pode.</span><span class="sxs-lookup"><span data-stu-id="18ca8-116">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>  
  
 `ParamArray`  
 <span data-ttu-id="18ca8-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="18ca8-117">Optional.</span></span> <span data-ttu-id="18ca8-118">Especifica que o último parâmetro na lista de parâmetros é uma matriz opcional de elementos do tipo de dados especificado.</span><span class="sxs-lookup"><span data-stu-id="18ca8-118">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="18ca8-119">Isso permite que o código de chamada passe um número arbitrário de argumentos para o procedimento.</span><span class="sxs-lookup"><span data-stu-id="18ca8-119">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>  
  
 `parametername`  
 <span data-ttu-id="18ca8-120">Necessário.</span><span class="sxs-lookup"><span data-stu-id="18ca8-120">Required.</span></span> <span data-ttu-id="18ca8-121">Nome da variável local representando o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="18ca8-121">Name of the local variable representing the parameter.</span></span>  
  
 `parametertype`  
 <span data-ttu-id="18ca8-122">Necessário se `Option Strict` é `On`.</span><span class="sxs-lookup"><span data-stu-id="18ca8-122">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="18ca8-123">Tipo de dados da variável local representando o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="18ca8-123">Data type of the local variable representing the parameter.</span></span>  
  
 `defaultvalue`  
 <span data-ttu-id="18ca8-124">Necessário para `Optional` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="18ca8-124">Required for `Optional` parameters.</span></span> <span data-ttu-id="18ca8-125">Qualquer expressão de constante ou constante que é avaliada como o tipo de dados do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="18ca8-125">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="18ca8-126">Se o tipo é `Object`, ou uma classe, interface, matriz ou estrutura, o valor padrão só pode ser `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="18ca8-126">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18ca8-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="18ca8-127">Remarks</span></span>  
 <span data-ttu-id="18ca8-128">Parâmetros estão entre parênteses e separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="18ca8-128">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="18ca8-129">Um parâmetro pode ser declarado com qualquer tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="18ca8-129">A parameter can be declared with any data type.</span></span> <span data-ttu-id="18ca8-130">Se você não especificar `parametertype`, o padrão é `Object`.</span><span class="sxs-lookup"><span data-stu-id="18ca8-130">If you do not specify `parametertype`, it defaults to `Object`.</span></span>  
  
 <span data-ttu-id="18ca8-131">Quando o código de chamada chama o procedimento, ele passa um *argumento* para cada parâmetro necessário.</span><span class="sxs-lookup"><span data-stu-id="18ca8-131">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="18ca8-132">Para obter mais informações, consulte [diferenças entre parâmetros e argumentos](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="18ca8-132">For more information, see [Differences Between Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>  
  
 <span data-ttu-id="18ca8-133">O argumento que o código de chamada passa para cada parâmetro é um ponteiro para um elemento subjacente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="18ca8-133">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="18ca8-134">Se esse elemento é *invariável* (uma constante, literal, enumeração ou expressão), é impossível para qualquer código mudá-lo.</span><span class="sxs-lookup"><span data-stu-id="18ca8-134">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="18ca8-135">Se for um *variável* elemento (uma variável declarada, campo, propriedade, elemento de matriz ou elemento de estrutura), o código de chamada pode alterá-la.</span><span class="sxs-lookup"><span data-stu-id="18ca8-135">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="18ca8-136">Para obter mais informações, consulte [diferenças entre modificáveis e não modificáveis argumentos](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="18ca8-136">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>  
  
 <span data-ttu-id="18ca8-137">Se um elemento variável é passado `ByRef`, o procedimento pode alterá-lo também.</span><span class="sxs-lookup"><span data-stu-id="18ca8-137">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="18ca8-138">Para obter mais informações, consulte [diferenças entre passar um argumento por valor e por referência](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="18ca8-138">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="18ca8-139">Regras</span><span class="sxs-lookup"><span data-stu-id="18ca8-139">Rules</span></span>  
  
-   <span data-ttu-id="18ca8-140">**Parênteses.**</span><span class="sxs-lookup"><span data-stu-id="18ca8-140">**Parentheses.**</span></span> <span data-ttu-id="18ca8-141">Se você especificar uma lista de parâmetros, você deve colocá-la entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="18ca8-141">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="18ca8-142">Se não houver nenhum parâmetro, você ainda pode usar parênteses delimitando uma lista vazia.</span><span class="sxs-lookup"><span data-stu-id="18ca8-142">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="18ca8-143">Isso melhora a legibilidade do código ao ver que o elemento é um procedimento.</span><span class="sxs-lookup"><span data-stu-id="18ca8-143">This improves the readability of your code by clarifying that the element is a procedure.</span></span>  
  
-   <span data-ttu-id="18ca8-144">**Parâmetros opcionais.**</span><span class="sxs-lookup"><span data-stu-id="18ca8-144">**Optional Parameters.**</span></span> <span data-ttu-id="18ca8-145">Se você usar o `Optional` modificador em um parâmetro, todos os parâmetros subsequentes na lista também devem ser opcionais e ser declarados usando o `Optional` modificador.</span><span class="sxs-lookup"><span data-stu-id="18ca8-145">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>  
  
     <span data-ttu-id="18ca8-146">Cada declaração de parâmetro opcional deve fornecer a `defaultvalue` cláusula.</span><span class="sxs-lookup"><span data-stu-id="18ca8-146">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>  
  
     <span data-ttu-id="18ca8-147">Para obter mais informações, consulte [parâmetros opcionais](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="18ca8-147">For more information, see [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span></span>  
  
-   <span data-ttu-id="18ca8-148">**Matrizes de parâmetros.**</span><span class="sxs-lookup"><span data-stu-id="18ca8-148">**Parameter Arrays.**</span></span> <span data-ttu-id="18ca8-149">Você deve especificar `ByVal` para um `ParamArray` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="18ca8-149">You must specify `ByVal` for a `ParamArray` parameter.</span></span>  
  
     <span data-ttu-id="18ca8-150">Você não pode usar ambos `Optional` e `ParamArray` na mesma lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="18ca8-150">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>  
  
     <span data-ttu-id="18ca8-151">Para obter mais informações, consulte [matrizes de parâmetro](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="18ca8-151">For more information, see [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
-   <span data-ttu-id="18ca8-152">**Mecanismo de passagem.**</span><span class="sxs-lookup"><span data-stu-id="18ca8-152">**Passing Mechanism.**</span></span> <span data-ttu-id="18ca8-153">É o mecanismo padrão para cada argumento `ByVal`, que significa que o procedimento não é possível alterar o elemento variável subjacente.</span><span class="sxs-lookup"><span data-stu-id="18ca8-153">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="18ca8-154">No entanto, se o elemento é um tipo de referência, o procedimento pode modificar o conteúdo ou os membros do objeto subjacente, mesmo que ele não é possível substituir ou reatribuir o objeto.</span><span class="sxs-lookup"><span data-stu-id="18ca8-154">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>  
  
-   <span data-ttu-id="18ca8-155">**Nomes de parâmetro.**</span><span class="sxs-lookup"><span data-stu-id="18ca8-155">**Parameter Names.**</span></span> <span data-ttu-id="18ca8-156">Se o tipo de dados do parâmetro é uma matriz, siga `parametername` imediatamente por parênteses.</span><span class="sxs-lookup"><span data-stu-id="18ca8-156">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="18ca8-157">Para obter mais informações sobre nomes de parâmetro, consulte [nomes de elemento declarado](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="18ca8-157">For more information on parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="18ca8-158">Exemplo</span><span class="sxs-lookup"><span data-stu-id="18ca8-158">Example</span></span>  
 <span data-ttu-id="18ca8-159">A exemplo a seguir mostra uma `Function` procedimento que define dois parâmetros.</span><span class="sxs-lookup"><span data-stu-id="18ca8-159">The following example shows a `Function` procedure that defines two parameters.</span></span>  
  
 [!code-vb[VbVbalrStatements#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-list_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="18ca8-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18ca8-160">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [<span data-ttu-id="18ca8-161">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="18ca8-161">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="18ca8-162">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="18ca8-162">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="18ca8-163">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="18ca8-163">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="18ca8-164">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="18ca8-164">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="18ca8-165">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="18ca8-165">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="18ca8-166">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="18ca8-166">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="18ca8-167">Como quebrar e combinar instruções no código</span><span class="sxs-lookup"><span data-stu-id="18ca8-167">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
