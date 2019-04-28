---
title: Considerações sobre procedimentos de sobrecarga (Visual Basic)
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
ms.openlocfilehash: f14cc28960af28530bda9a78c1309dea10c18b8f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864336"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="481e0-102">Considerações sobre procedimentos de sobrecarga (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="481e0-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="481e0-103">Ao sobrecarregar um procedimento, você deve usar um diferente *assinatura* para cada versão sobrecarregada.</span><span class="sxs-lookup"><span data-stu-id="481e0-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="481e0-104">Isso geralmente significa que cada versão deve especificar uma lista de parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="481e0-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="481e0-105">Para obter mais informações, consulte "Assinatura diferente" na [sobrecarga de procedimento](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="481e0-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="481e0-106">Você pode sobrecarregar uma `Function` procedimento com um `Sub` procedimento e vice-versa, que tenham assinaturas diferentes.</span><span class="sxs-lookup"><span data-stu-id="481e0-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="481e0-107">Duas sobrecargas não podem diferir somente em que uma tem um valor de retorno e o outro não.</span><span class="sxs-lookup"><span data-stu-id="481e0-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="481e0-108">Você pode sobrecarregar uma propriedade da mesma maneira que você sobrecarrega um procedimento e com as mesmas restrições.</span><span class="sxs-lookup"><span data-stu-id="481e0-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="481e0-109">No entanto, você não pode sobrecarregar um procedimento com uma propriedade, ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="481e0-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="481e0-110">Alternativas para versões sobrecarregadas</span><span class="sxs-lookup"><span data-stu-id="481e0-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="481e0-111">Às vezes, você tem alternativas para versões sobrecarregadas, particularmente quando a presença dos argumentos é opcional ou seu número é variável.</span><span class="sxs-lookup"><span data-stu-id="481e0-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="481e0-112">Tenha em mente que argumentos opcionais não são necessariamente suportados por todos os idiomas e matrizes de parâmetros são limitados ao Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="481e0-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to Visual Basic.</span></span> <span data-ttu-id="481e0-113">Se você estiver escrevendo um procedimento que pode ser chamado do código escrito em qualquer um dos vários idiomas diferentes, versões sobrecarregadas oferecem a maior flexibilidade.</span><span class="sxs-lookup"><span data-stu-id="481e0-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="481e0-114">Sobrecargas e argumentos opcionais</span><span class="sxs-lookup"><span data-stu-id="481e0-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="481e0-115">Quando o código de chamada pode, opcionalmente, fornecer ou omitir um ou mais argumentos, você pode definir várias versões sobrecarregadas ou use parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="481e0-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="481e0-116">Quando usar versões sobrecarregadas</span><span class="sxs-lookup"><span data-stu-id="481e0-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="481e0-117">Você pode considerar a definição de várias versões sobrecarregadas nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="481e0-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="481e0-118">A lógica no código do procedimento é significativamente diferente dependendo se o código de chamada fornece um argumento opcional ou não.</span><span class="sxs-lookup"><span data-stu-id="481e0-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
- <span data-ttu-id="481e0-119">O código do procedimento não é possível testar com confiança se o código de chamada tiver fornecido um argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="481e0-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="481e0-120">Esse é o caso, por exemplo, se não houver nenhum candidato possível para um valor padrão que o código de chamada pode não ser esperado para fornecer.</span><span class="sxs-lookup"><span data-stu-id="481e0-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="481e0-121">Quando usar parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="481e0-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="481e0-122">Talvez você prefira um ou mais parâmetros opcionais nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="481e0-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
- <span data-ttu-id="481e0-123">A única ação necessária quando o código de chamada não fornece um argumento opcional é definir o parâmetro como um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="481e0-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="481e0-124">Nesse caso, o código do procedimento pode ser menos complicado se você definir uma única versão com um ou mais `Optional` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="481e0-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="481e0-125">Para obter mais informações, consulte [parâmetros opcionais](./optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="481e0-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="481e0-126">Sobrecargas e ParamArrays</span><span class="sxs-lookup"><span data-stu-id="481e0-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="481e0-127">Quando o código de chamada pode passar um número variável de argumentos, você pode definir várias versões sobrecarregadas ou usar uma matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="481e0-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="481e0-128">Quando usar versões sobrecarregadas</span><span class="sxs-lookup"><span data-stu-id="481e0-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="481e0-129">Você pode considerar a definição de várias versões sobrecarregadas nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="481e0-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="481e0-130">Você sabe que o código de chamada nunca passa mais de um pequeno número de valores para a matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="481e0-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
- <span data-ttu-id="481e0-131">A lógica no código do procedimento é significativamente diferente dependendo de quantos valores passa o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="481e0-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
- <span data-ttu-id="481e0-132">O código de chamada pode passar valores de diferentes tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="481e0-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="481e0-133">Quando usar uma matriz de parâmetros</span><span class="sxs-lookup"><span data-stu-id="481e0-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="481e0-134">Você é melhor atendido por um `ParamArray` parâmetro nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="481e0-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
- <span data-ttu-id="481e0-135">Não é possível prever quantos valores o código de chamada pode passar para a matriz de parâmetros e pode ser um número grande.</span><span class="sxs-lookup"><span data-stu-id="481e0-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
- <span data-ttu-id="481e0-136">A lógica do procedimento se presta à iteração em todos os valores que o código de chamada passa, executando essencialmente as mesmas operações em cada valor.</span><span class="sxs-lookup"><span data-stu-id="481e0-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="481e0-137">Para obter mais informações, consulte [matrizes de parâmetro](./parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="481e0-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="481e0-138">Sobrecargas implícitas para parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="481e0-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="481e0-139">Um procedimento com um [opcional](../../../../visual-basic/language-reference/modifiers/optional.md) parâmetro é equivalente a dois procedimentos sobrecarregados, um com o parâmetro opcional e outra sem ele.</span><span class="sxs-lookup"><span data-stu-id="481e0-139">A procedure with an [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="481e0-140">Você não pode sobrecarregar tal procedimento com uma lista de parâmetros correspondentes a qualquer uma delas.</span><span class="sxs-lookup"><span data-stu-id="481e0-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="481e0-141">As declarações a seguir ilustram isso.</span><span class="sxs-lookup"><span data-stu-id="481e0-141">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 <span data-ttu-id="481e0-142">Para um procedimento com mais de um parâmetro opcional, há um conjunto de sobrecargas implícitas, chegada pela lógica semelhante do exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="481e0-142">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="481e0-143">Sobrecargas implícitas para um parâmetro ParamArray</span><span class="sxs-lookup"><span data-stu-id="481e0-143">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="481e0-144">O compilador considera um procedimento com um [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parâmetro deverá ter um número infinito de sobrecargas, com diferenças no que o código de chamada passa para a matriz de parâmetros, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="481e0-144">The compiler considers a procedure with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
- <span data-ttu-id="481e0-145">Uma sobrecarga para quando o código de chamada não fornece um argumento para o `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="481e0-145">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
- <span data-ttu-id="481e0-146">Uma sobrecarga para quando o código de chamada fornece uma matriz unidimensional do `ParamArray` tipo de elemento</span><span class="sxs-lookup"><span data-stu-id="481e0-146">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
- <span data-ttu-id="481e0-147">Para cada inteiro positivo, uma sobrecarga para quando o código de chamada fornece esse número de argumentos, cada um do `ParamArray` tipo de elemento</span><span class="sxs-lookup"><span data-stu-id="481e0-147">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="481e0-148">As declarações a seguir ilustram essas sobrecargas implícitas.</span><span class="sxs-lookup"><span data-stu-id="481e0-148">The following declarations illustrate these implicit overloads.</span></span>  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="481e0-149">Você não pode sobrecarregar tal procedimento com uma lista de parâmetros que usa uma matriz unidimensional para a matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="481e0-149">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="481e0-150">No entanto, você pode usar as assinaturas das outras sobrecargas implícitas.</span><span class="sxs-lookup"><span data-stu-id="481e0-150">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="481e0-151">As declarações a seguir ilustram isso.</span><span class="sxs-lookup"><span data-stu-id="481e0-151">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="481e0-152">Programação sem tipo como uma alternativa para sobrecarga</span><span class="sxs-lookup"><span data-stu-id="481e0-152">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="481e0-153">Se você quiser permitir que o código de chamada passar diferentes tipos de dados para um parâmetro, uma abordagem alternativa é programação sem tipo.</span><span class="sxs-lookup"><span data-stu-id="481e0-153">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="481e0-154">Você pode definir o tipo de verificação de alternar para o `Off` com qualquer um de [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) ou o [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="481e0-154">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) or the [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="481e0-155">Em seguida, você não precisa declarar o tipo de dados do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="481e0-155">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="481e0-156">No entanto, essa abordagem tem as seguintes desvantagens em comparação com sobrecarga:</span><span class="sxs-lookup"><span data-stu-id="481e0-156">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
- <span data-ttu-id="481e0-157">Programação sem tipo produz código menos eficiente de execução.</span><span class="sxs-lookup"><span data-stu-id="481e0-157">Typeless programming produces less efficient execution code.</span></span>  
  
- <span data-ttu-id="481e0-158">O procedimento deve testar cada tipo de dados que ele prevê que está sendo passado.</span><span class="sxs-lookup"><span data-stu-id="481e0-158">The procedure must test for every data type it anticipates being passed.</span></span>  
  
- <span data-ttu-id="481e0-159">O compilador não pode sinalizar um erro se o código de chamada passa um tipo de dados que o procedimento não oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="481e0-159">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="481e0-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="481e0-160">See also</span></span>

- [<span data-ttu-id="481e0-161">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="481e0-161">Procedures</span></span>](./index.md)
- [<span data-ttu-id="481e0-162">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="481e0-162">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="481e0-163">Solução de problemas de Procedimentos</span><span class="sxs-lookup"><span data-stu-id="481e0-163">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="481e0-164">Como: Definir várias versões de um procedimento</span><span class="sxs-lookup"><span data-stu-id="481e0-164">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="481e0-165">Como: Chamar um procedimento sobrecarregado</span><span class="sxs-lookup"><span data-stu-id="481e0-165">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="481e0-166">Como: Sobrecarregar um procedimento que usa parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="481e0-166">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="481e0-167">Como: Sobrecarregar um procedimento que usa um número indefinido de parâmetros</span><span class="sxs-lookup"><span data-stu-id="481e0-167">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="481e0-168">Resolução de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="481e0-168">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="481e0-169">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="481e0-169">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
