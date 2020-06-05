---
title: Lista de parâmetros
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: 706fc2414806db5608cce410bf4156839ec2d83e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404311"
---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="8c48c-102">Lista de parâmetros (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c48c-102">Parameter List (Visual Basic)</span></span>

<span data-ttu-id="8c48c-103">Especifica os parâmetros que um procedimento espera quando é chamado.</span><span class="sxs-lookup"><span data-stu-id="8c48c-103">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="8c48c-104">Vários parâmetros são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="8c48c-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="8c48c-105">Veja a seguir a sintaxe de um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8c48c-105">The following is the syntax for one parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="8c48c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c48c-106">Syntax</span></span>

```vb
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]
parametername[( )] [ As parametertype ] [ = defaultvalue ]
```

## <a name="parts"></a><span data-ttu-id="8c48c-107">Partes</span><span class="sxs-lookup"><span data-stu-id="8c48c-107">Parts</span></span>

`attributelist`  
<span data-ttu-id="8c48c-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8c48c-108">Optional.</span></span> <span data-ttu-id="8c48c-109">Lista de atributos que se aplicam a esse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8c48c-109">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="8c48c-110">Você deve colocar a [lista de atributos](attribute-list.md) entre colchetes angulares (" `<` " e " `>` ").</span><span class="sxs-lookup"><span data-stu-id="8c48c-110">You must enclose the [Attribute List](attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

`Optional`  
<span data-ttu-id="8c48c-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8c48c-111">Optional.</span></span> <span data-ttu-id="8c48c-112">Especifica que esse parâmetro não é necessário quando o procedimento é chamado.</span><span class="sxs-lookup"><span data-stu-id="8c48c-112">Specifies that this parameter is not required when the procedure is called.</span></span>

`ByVal`  
<span data-ttu-id="8c48c-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8c48c-113">Optional.</span></span> <span data-ttu-id="8c48c-114">Especifica que o procedimento não pode substituir ou reatribuir o elemento Variable subjacente ao argumento correspondente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="8c48c-114">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>

`ByRef`  
<span data-ttu-id="8c48c-115">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8c48c-115">Optional.</span></span> <span data-ttu-id="8c48c-116">Especifica que o procedimento pode modificar o elemento variável subjacente no código de chamada da mesma maneira que o próprio código de chamada pode.</span><span class="sxs-lookup"><span data-stu-id="8c48c-116">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>

`ParamArray`  
<span data-ttu-id="8c48c-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8c48c-117">Optional.</span></span> <span data-ttu-id="8c48c-118">Especifica que o último parâmetro na lista de parâmetros é uma matriz opcional de elementos do tipo de dados especificado.</span><span class="sxs-lookup"><span data-stu-id="8c48c-118">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="8c48c-119">Isso permite que o código de chamada passe um número arbitrário de argumentos para o procedimento.</span><span class="sxs-lookup"><span data-stu-id="8c48c-119">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>

`parametername`  
<span data-ttu-id="8c48c-120">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="8c48c-120">Required.</span></span> <span data-ttu-id="8c48c-121">Nome da variável local que representa o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8c48c-121">Name of the local variable representing the parameter.</span></span>

`parametertype`  
<span data-ttu-id="8c48c-122">Obrigatório se `Option Strict` for `On` .</span><span class="sxs-lookup"><span data-stu-id="8c48c-122">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="8c48c-123">Tipo de dados da variável local que representa o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8c48c-123">Data type of the local variable representing the parameter.</span></span>

`defaultvalue`  
<span data-ttu-id="8c48c-124">Obrigatório para `Optional` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8c48c-124">Required for `Optional` parameters.</span></span> <span data-ttu-id="8c48c-125">Qualquer expressão constante ou constante que seja avaliada como o tipo de dados do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8c48c-125">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="8c48c-126">Se o tipo for `Object` , ou uma classe, interface, matriz ou estrutura, o valor padrão só poderá ser `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="8c48c-126">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>

## <a name="remarks"></a><span data-ttu-id="8c48c-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c48c-127">Remarks</span></span>

<span data-ttu-id="8c48c-128">Os parâmetros são circundados por parênteses e separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="8c48c-128">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="8c48c-129">Um parâmetro pode ser declarado com qualquer tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="8c48c-129">A parameter can be declared with any data type.</span></span> <span data-ttu-id="8c48c-130">Se você não especificar `parametertype` , o padrão será `Object` .</span><span class="sxs-lookup"><span data-stu-id="8c48c-130">If you do not specify `parametertype`, it defaults to `Object`.</span></span>

<span data-ttu-id="8c48c-131">Quando o código de chamada chama o procedimento, ele passa um *argumento* para cada parâmetro necessário.</span><span class="sxs-lookup"><span data-stu-id="8c48c-131">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="8c48c-132">Para obter mais informações, consulte [diferenças entre parâmetros e argumentos](../../programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="8c48c-132">For more information, see [Differences Between Parameters and Arguments](../../programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>

<span data-ttu-id="8c48c-133">O argumento que o código de chamada passa para cada parâmetro é um ponteiro para um elemento subjacente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="8c48c-133">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="8c48c-134">Se esse elemento não for *variável* (uma constante, literal, enumeração ou expressão), será impossível para qualquer código alterá-lo.</span><span class="sxs-lookup"><span data-stu-id="8c48c-134">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="8c48c-135">Se for um elemento *variável* (uma variável declarada, um campo, uma propriedade, um elemento de matriz ou um elemento de estrutura), o código de chamada poderá alterá-lo.</span><span class="sxs-lookup"><span data-stu-id="8c48c-135">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="8c48c-136">Para obter mais informações, consulte [diferenças entre argumentos modificáveis e não modificáveis](../../programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="8c48c-136">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>

<span data-ttu-id="8c48c-137">Se um elemento variable for passado `ByRef` , o procedimento também poderá alterá-lo.</span><span class="sxs-lookup"><span data-stu-id="8c48c-137">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="8c48c-138">Para obter mais informações, consulte [diferenças entre passar um argumento por valor e por referência](../../programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="8c48c-138">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>

## <a name="rules"></a><span data-ttu-id="8c48c-139">Regras</span><span class="sxs-lookup"><span data-stu-id="8c48c-139">Rules</span></span>

- <span data-ttu-id="8c48c-140">**Parênteses.**</span><span class="sxs-lookup"><span data-stu-id="8c48c-140">**Parentheses.**</span></span> <span data-ttu-id="8c48c-141">Se você especificar uma lista de parâmetros, deverá colocá-la entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="8c48c-141">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="8c48c-142">Se não houver parâmetros, você ainda poderá usar parênteses delimitando uma lista vazia.</span><span class="sxs-lookup"><span data-stu-id="8c48c-142">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="8c48c-143">Isso melhora a legibilidade do seu código, esclarecendo que o elemento é um procedimento.</span><span class="sxs-lookup"><span data-stu-id="8c48c-143">This improves the readability of your code by clarifying that the element is a procedure.</span></span>

- <span data-ttu-id="8c48c-144">**Parâmetros opcionais.**</span><span class="sxs-lookup"><span data-stu-id="8c48c-144">**Optional Parameters.**</span></span> <span data-ttu-id="8c48c-145">Se você usar o `Optional` modificador em um parâmetro, todos os parâmetros subsequentes na lista também deverão ser opcionais e serem declarados usando o `Optional` modificador.</span><span class="sxs-lookup"><span data-stu-id="8c48c-145">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>

     <span data-ttu-id="8c48c-146">Cada declaração de parâmetro opcional deve fornecer a `defaultvalue` cláusula.</span><span class="sxs-lookup"><span data-stu-id="8c48c-146">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>

     <span data-ttu-id="8c48c-147">Para obter mais informações, consulte [parâmetros opcionais](../../programming-guide/language-features/procedures/optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="8c48c-147">For more information, see [Optional Parameters](../../programming-guide/language-features/procedures/optional-parameters.md).</span></span>

- <span data-ttu-id="8c48c-148">**Matrizes de parâmetros.**</span><span class="sxs-lookup"><span data-stu-id="8c48c-148">**Parameter Arrays.**</span></span> <span data-ttu-id="8c48c-149">Você deve especificar `ByVal` para um `ParamArray` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8c48c-149">You must specify `ByVal` for a `ParamArray` parameter.</span></span>

     <span data-ttu-id="8c48c-150">Você não pode usar ambos `Optional` e `ParamArray` na mesma lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8c48c-150">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>

     <span data-ttu-id="8c48c-151">Para obter mais informações, consulte [matrizes de parâmetros](../../programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="8c48c-151">For more information, see [Parameter Arrays](../../programming-guide/language-features/procedures/parameter-arrays.md).</span></span>

- <span data-ttu-id="8c48c-152">**Mecanismo de passagem.**</span><span class="sxs-lookup"><span data-stu-id="8c48c-152">**Passing Mechanism.**</span></span> <span data-ttu-id="8c48c-153">O mecanismo padrão para cada argumento é `ByVal` , o que significa que o procedimento não pode alterar o elemento de variável subjacente.</span><span class="sxs-lookup"><span data-stu-id="8c48c-153">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="8c48c-154">No entanto, se o elemento for um tipo de referência, o procedimento poderá modificar o conteúdo ou os membros do objeto subjacente, mesmo que ele não possa substituir ou reatribuir o próprio objeto.</span><span class="sxs-lookup"><span data-stu-id="8c48c-154">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>

- <span data-ttu-id="8c48c-155">**Nomes de parâmetro.**</span><span class="sxs-lookup"><span data-stu-id="8c48c-155">**Parameter Names.**</span></span> <span data-ttu-id="8c48c-156">Se o tipo de dados do parâmetro for uma matriz, siga `parametername` imediatamente por parênteses.</span><span class="sxs-lookup"><span data-stu-id="8c48c-156">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="8c48c-157">Para obter mais informações sobre nomes de parâmetro, consulte [nomes de elemento declarados](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="8c48c-157">For more information on parameter names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="example"></a><span data-ttu-id="8c48c-158">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8c48c-158">Example</span></span>

<span data-ttu-id="8c48c-159">O exemplo a seguir mostra um `Function` procedimento que define dois parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8c48c-159">The following example shows a `Function` procedure that defines two parameters.</span></span>

[!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="8c48c-160">Confira também</span><span class="sxs-lookup"><span data-stu-id="8c48c-160">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="8c48c-161">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="8c48c-161">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="8c48c-162">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="8c48c-162">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="8c48c-163">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="8c48c-163">Declare Statement</span></span>](declare-statement.md)
- [<span data-ttu-id="8c48c-164">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="8c48c-164">Structure Statement</span></span>](structure-statement.md)
- [<span data-ttu-id="8c48c-165">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="8c48c-165">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="8c48c-166">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="8c48c-166">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="8c48c-167">Como: Quebrar e combinar instruções no código</span><span class="sxs-lookup"><span data-stu-id="8c48c-167">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
