---
title: Considerações sobre procedimentos de sobrecarga
ms.date: 07/20/2015
helpviewer_keywords:
- signatures [Visual Basic], ParamArray arguments
- ParamArray keyword [Visual Basic], parameter arrays
- ParamArray keyword [Visual Basic], arguments and signatures
- function overloading [Visual Basic], implicit overloads for ParamArray
- ParamArray keyword [Visual Basic], signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], overloading
- parameters [Visual Basic], lists
- function overloading [Visual Basic], typeless programming
- typeless programming
- function overloading [Visual Basic], restrictions
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], overloading
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- parameter arrays [Visual Basic], overloading arguments
- Visual Basic code, parameter lists
- procedure overloading [Visual Basic], considerations
- Option Explicit statement [Visual Basic]
- restrictions [Visual Basic], overloading procedures
- procedures [Visual Basic], parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
ms.openlocfilehash: 4a0cfe176a59b3f90f5850ae8b4e34784c400c6b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351005"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="789f4-102">Considerações sobre procedimentos de sobrecarga (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="789f4-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="789f4-103">Ao sobrecarregar um procedimento, você deve usar uma *assinatura* diferente para cada versão sobrecarregada.</span><span class="sxs-lookup"><span data-stu-id="789f4-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="789f4-104">Isso geralmente significa que cada versão deve especificar uma lista de parâmetros diferente.</span><span class="sxs-lookup"><span data-stu-id="789f4-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="789f4-105">Para obter mais informações, consulte "assinatura diferente" em [sobrecarga de procedimento](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="789f4-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="789f4-106">Você pode sobrecarregar um procedimento de `Function` com um procedimento de `Sub` e vice-versa, desde que eles tenham assinaturas diferentes.</span><span class="sxs-lookup"><span data-stu-id="789f4-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="789f4-107">Duas sobrecargas não podem diferir apenas se uma tiver um valor de retorno e a outra não.</span><span class="sxs-lookup"><span data-stu-id="789f4-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="789f4-108">Você pode sobrecarregar uma propriedade da mesma maneira que sobrecarrega um procedimento e com as mesmas restrições.</span><span class="sxs-lookup"><span data-stu-id="789f4-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="789f4-109">No entanto, você não pode sobrecarregar um procedimento com uma propriedade ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="789f4-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="789f4-110">Alternativas para versões sobrecarregadas</span><span class="sxs-lookup"><span data-stu-id="789f4-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="789f4-111">Às vezes, você tem alternativas para versões sobrecarregadas, especialmente quando a presença de argumentos é opcional ou seu número é variável.</span><span class="sxs-lookup"><span data-stu-id="789f4-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="789f4-112">Tenha em mente que os argumentos opcionais não são necessariamente suportados por todas as linguagens, e as matrizes de parâmetros são limitadas a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="789f4-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to Visual Basic.</span></span> <span data-ttu-id="789f4-113">Se você estiver escrevendo um procedimento que provavelmente será chamado a partir de um código escrito em qualquer uma das várias linguagens diferentes, as versões sobrecarregadas oferecem a maior flexibilidade.</span><span class="sxs-lookup"><span data-stu-id="789f4-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="789f4-114">Sobrecargas e argumentos opcionais</span><span class="sxs-lookup"><span data-stu-id="789f4-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="789f4-115">Quando o código de chamada pode opcionalmente fornecer ou omitir um ou mais argumentos, você pode definir várias versões sobrecarregadas ou usar parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="789f4-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="789f4-116">Quando usar versões sobrecarregadas</span><span class="sxs-lookup"><span data-stu-id="789f4-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="789f4-117">Você pode considerar a definição de uma série de versões sobrecarregadas nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="789f4-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="789f4-118">A lógica no código do procedimento é significativamente diferente dependendo se o código de chamada fornece um argumento opcional ou não.</span><span class="sxs-lookup"><span data-stu-id="789f4-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
- <span data-ttu-id="789f4-119">O código do procedimento não pode testar de maneira confiável se o código de chamada forneceu um argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="789f4-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="789f4-120">Esse é o caso, por exemplo, se não houver nenhum candidato possível para um valor padrão que o código de chamada não tenha se esperado de fornecer.</span><span class="sxs-lookup"><span data-stu-id="789f4-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="789f4-121">Quando usar parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="789f4-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="789f4-122">Você pode preferir um ou mais parâmetros opcionais nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="789f4-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
- <span data-ttu-id="789f4-123">A única ação necessária quando o código de chamada não fornece um argumento opcional é definir o parâmetro como um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="789f4-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="789f4-124">Nesse caso, o código do procedimento pode ser menos complicado se você definir uma única versão com um ou mais parâmetros de `Optional`.</span><span class="sxs-lookup"><span data-stu-id="789f4-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="789f4-125">Para obter mais informações, consulte [parâmetros opcionais](./optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="789f4-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="789f4-126">Sobrecargas e ParamArrays</span><span class="sxs-lookup"><span data-stu-id="789f4-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="789f4-127">Quando o código de chamada pode passar um número variável de argumentos, você pode definir várias versões sobrecarregadas ou usar uma matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="789f4-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="789f4-128">Quando usar versões sobrecarregadas</span><span class="sxs-lookup"><span data-stu-id="789f4-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="789f4-129">Você pode considerar a definição de uma série de versões sobrecarregadas nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="789f4-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="789f4-130">Você sabe que o código de chamada nunca passa mais do que um pequeno número de valores para a matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="789f4-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
- <span data-ttu-id="789f4-131">A lógica no código do procedimento é significativamente diferente dependendo de quantos valores o código de chamada passa.</span><span class="sxs-lookup"><span data-stu-id="789f4-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
- <span data-ttu-id="789f4-132">O código de chamada pode passar valores de tipos de dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="789f4-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="789f4-133">Quando usar uma matriz de parâmetros</span><span class="sxs-lookup"><span data-stu-id="789f4-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="789f4-134">Você é mais bem atendido por um parâmetro `ParamArray` nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="789f4-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
- <span data-ttu-id="789f4-135">Você não pode prever quantos valores o código de chamada pode passar para a matriz de parâmetros e pode ser um grande número.</span><span class="sxs-lookup"><span data-stu-id="789f4-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
- <span data-ttu-id="789f4-136">A lógica do procedimento se presta para iterar em todos os valores que o código de chamada passa, executando essencialmente as mesmas operações em cada valor.</span><span class="sxs-lookup"><span data-stu-id="789f4-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="789f4-137">Para obter mais informações, consulte [matrizes de parâmetros](./parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="789f4-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="789f4-138">Sobrecargas implícitas para parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="789f4-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="789f4-139">Um procedimento com um parâmetro [opcional](../../../../visual-basic/language-reference/modifiers/optional.md) é equivalente a dois procedimentos sobrecarregados, um com o parâmetro opcional e outro sem ele.</span><span class="sxs-lookup"><span data-stu-id="789f4-139">A procedure with an [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="789f4-140">Não é possível sobrecarregar esse procedimento com uma lista de parâmetros correspondente a um desses.</span><span class="sxs-lookup"><span data-stu-id="789f4-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="789f4-141">As declarações a seguir ilustram isso.</span><span class="sxs-lookup"><span data-stu-id="789f4-141">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 <span data-ttu-id="789f4-142">Para um procedimento com mais de um parâmetro opcional, há um conjunto de sobrecargas implícitas, recebidos pela lógica semelhante àquela no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="789f4-142">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="789f4-143">Sobrecargas implícitas para um parâmetro ParamArray</span><span class="sxs-lookup"><span data-stu-id="789f4-143">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="789f4-144">O compilador considera um procedimento com um parâmetro [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) para ter um número infinito de sobrecargas, diferente do outro no que o código de chamada passa para a matriz de parâmetros, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="789f4-144">The compiler considers a procedure with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
- <span data-ttu-id="789f4-145">Uma sobrecarga para quando o código de chamada não fornece um argumento para o `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="789f4-145">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
- <span data-ttu-id="789f4-146">Uma sobrecarga para quando o código de chamada fornece uma matriz unidimensional do tipo de elemento `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="789f4-146">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
- <span data-ttu-id="789f4-147">Para cada inteiro positivo, uma sobrecarga para quando o código de chamada fornece esse número de argumentos, cada um dos `ParamArray` tipo de elemento</span><span class="sxs-lookup"><span data-stu-id="789f4-147">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="789f4-148">As declarações a seguir ilustram essas sobrecargas implícitas.</span><span class="sxs-lookup"><span data-stu-id="789f4-148">The following declarations illustrate these implicit overloads.</span></span>  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="789f4-149">Não é possível sobrecarregar esse procedimento com uma lista de parâmetros que usa uma matriz unidimensional para a matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="789f4-149">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="789f4-150">No entanto, você pode usar as assinaturas das outras sobrecargas implícitas.</span><span class="sxs-lookup"><span data-stu-id="789f4-150">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="789f4-151">As declarações a seguir ilustram isso.</span><span class="sxs-lookup"><span data-stu-id="789f4-151">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="789f4-152">Programação não tipada como uma alternativa à sobrecarga</span><span class="sxs-lookup"><span data-stu-id="789f4-152">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="789f4-153">Se você quiser permitir que o código de chamada transmita tipos de dados diferentes para um parâmetro, uma abordagem alternativa será a programação sem tipo.</span><span class="sxs-lookup"><span data-stu-id="789f4-153">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="789f4-154">Você pode definir a opção de verificação de tipo para `Off` com a [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) ou a opção [-optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) do compilador.</span><span class="sxs-lookup"><span data-stu-id="789f4-154">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) or the [-optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="789f4-155">Em seguida, você não precisa declarar o tipo de dados do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="789f4-155">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="789f4-156">No entanto, essa abordagem tem as seguintes desvantagens em comparação com a sobrecarga:</span><span class="sxs-lookup"><span data-stu-id="789f4-156">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
- <span data-ttu-id="789f4-157">A programação sem tipo produz um código de execução menos eficiente.</span><span class="sxs-lookup"><span data-stu-id="789f4-157">Typeless programming produces less efficient execution code.</span></span>  
  
- <span data-ttu-id="789f4-158">O procedimento deve testar para cada tipo de dados que ele prevê que está sendo passado.</span><span class="sxs-lookup"><span data-stu-id="789f4-158">The procedure must test for every data type it anticipates being passed.</span></span>  
  
- <span data-ttu-id="789f4-159">O compilador não poderá sinalizar um erro se o código de chamada passar um tipo de dados ao qual o procedimento não dá suporte.</span><span class="sxs-lookup"><span data-stu-id="789f4-159">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="789f4-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="789f4-160">See also</span></span>

- [<span data-ttu-id="789f4-161">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="789f4-161">Procedures</span></span>](./index.md)
- [<span data-ttu-id="789f4-162">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="789f4-162">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="789f4-163">Solução de problemas de Procedimentos</span><span class="sxs-lookup"><span data-stu-id="789f4-163">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="789f4-164">Como definir várias versões de um procedimento</span><span class="sxs-lookup"><span data-stu-id="789f4-164">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="789f4-165">Como chamar um procedimento sobrecarregado</span><span class="sxs-lookup"><span data-stu-id="789f4-165">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="789f4-166">Como sobrecarregar um procedimento que usa parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="789f4-166">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="789f4-167">Como sobrecarregar um procedimento que usa um número indefinido de parâmetros</span><span class="sxs-lookup"><span data-stu-id="789f4-167">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="789f4-168">Resolução de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="789f4-168">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="789f4-169">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="789f4-169">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
