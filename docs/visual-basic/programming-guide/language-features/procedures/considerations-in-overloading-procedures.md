---
title: "Considerações sobre procedimentos de sobrecarga (Visual Basic) | Documentos do Microsoft"
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
- signatures, ParamArray arguments
- ParamArray keyword, parameter arrays
- ParamArray keyword, arguments and signatures
- function overloading, implicit overloads for ParamArray
- ParamArray keyword, signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures, overloading
- parameters, lists
- function overloading, typeless programming
- typeless programming
- function overloading, restrictions
- arguments [Visual Basic], optional
- optional arguments, overloading
- signatures, procedure
- parameter lists
- parameter arrays, overloading arguments
- Visual Basic code, parameter lists
- procedure overloading, considerations
- Option Explicit statement
- restrictions, overloading procedures
- procedures, parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
caps.latest.revision: 26
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
ms.openlocfilehash: 486e6c08fe6284cc9b5856fb848f7307a5651120
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="5e2e1-102">Considerações sobre procedimentos de sobrecarga (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e2e1-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="5e2e1-103">Quando você sobrecarrega um procedimento, você deve usar um outro *assinatura* para cada versão sobrecarregada.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="5e2e1-104">Isso geralmente significa que cada versão deve especificar uma lista de parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="5e2e1-105">Para obter mais informações, consulte "Assinatura diferente" em [sobrecarga de procedimento](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="5e2e1-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="5e2e1-106">Você pode sobrecarregar uma `Function` procedimento com uma `Sub` procedimento e vice-versa, que tenham assinaturas diferentes.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="5e2e1-107">Duas sobrecargas não podem diferir somente em que um tem um valor de retorno e o outro não.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="5e2e1-108">Você pode sobrecarregar uma propriedade da mesma maneira que sobrecarrega um procedimento e com as mesmas restrições.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="5e2e1-109">No entanto, você não pode sobrecarregar um procedimento com uma propriedade, ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="5e2e1-110">Alternativas para versões sobrecarregadas</span><span class="sxs-lookup"><span data-stu-id="5e2e1-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="5e2e1-111">Às vezes, você tem alternativas para versões sobrecarregadas, particularmente quando a presença dos argumentos é opcional ou seu número é variável.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="5e2e1-112">Tenha em mente que argumentos opcionais não são necessariamente suportados por todos os idiomas, e matrizes de parâmetros são limitadas a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="5e2e1-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="5e2e1-113">Se você estiver escrevendo um procedimento que é provável de ser chamado a partir do código escrito em qualquer um dos vários idiomas diferentes, versões sobrecarregadas oferecem a maior flexibilidade.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="5e2e1-114">Sobrecargas e argumentos opcionais</span><span class="sxs-lookup"><span data-stu-id="5e2e1-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="5e2e1-115">Quando o código de chamada pode opcionalmente fornecer ou omitir um ou mais argumentos, você pode definir várias versões sobrecarregados ou usar parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="5e2e1-116">Quando usar versões sobrecarregadas</span><span class="sxs-lookup"><span data-stu-id="5e2e1-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="5e2e1-117">Você pode considerar definir uma série de versões sobrecarregadas nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="5e2e1-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="5e2e1-118">A lógica no código do procedimento é significativamente diferente dependendo se o código de chamada fornece um argumento opcional ou não.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
-   <span data-ttu-id="5e2e1-119">O código do procedimento não pode testar com confiança se o código de chamada forneceu um argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="5e2e1-120">Esse é o caso, por exemplo, se não houver nenhum candidato possível para um valor padrão que o código de chamada pode não ser esperado para fornecer.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="5e2e1-121">Quando usar parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="5e2e1-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="5e2e1-122">Talvez você prefira um ou mais parâmetros opcionais nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="5e2e1-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
-   <span data-ttu-id="5e2e1-123">A única ação necessária quando o código de chamada não fornece um argumento opcional é definir o parâmetro como um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="5e2e1-124">Nesse caso, o código do procedimento pode ser menos complicado se você definir uma única versão com um ou mais `Optional` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="5e2e1-125">Para obter mais informações, consulte [parâmetros opcionais](./optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="5e2e1-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="5e2e1-126">Sobrecargas e ParamArrays</span><span class="sxs-lookup"><span data-stu-id="5e2e1-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="5e2e1-127">Quando o código de chamada pode passar um número variável de argumentos, você pode definir várias versões sobrecarregados ou usar uma matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="5e2e1-128">Quando usar versões sobrecarregadas</span><span class="sxs-lookup"><span data-stu-id="5e2e1-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="5e2e1-129">Você pode considerar definir uma série de versões sobrecarregadas nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="5e2e1-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="5e2e1-130">Você sabe que o código de chamada nunca passa mais do que um pequeno número de valores para a matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
-   <span data-ttu-id="5e2e1-131">A lógica no código do procedimento é significativamente diferente dependendo de quantos valores o código de chamada passa.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
-   <span data-ttu-id="5e2e1-132">O código de chamada pode passar valores de diferentes tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="5e2e1-133">Quando usar uma matriz de parâmetros</span><span class="sxs-lookup"><span data-stu-id="5e2e1-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="5e2e1-134">Você é mais bem atendidas por um `ParamArray` parâmetro nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="5e2e1-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
-   <span data-ttu-id="5e2e1-135">Não é possível prever quantos valores o código de chamada pode passar para a matriz de parâmetros, e pode ser um número grande.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
-   <span data-ttu-id="5e2e1-136">A lógica do procedimento presta-se à iteração em todos os valores que o código de chamada passa, executando essencialmente as mesmas operações em cada valor.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="5e2e1-137">Para obter mais informações, consulte [matrizes de parâmetros](./parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="5e2e1-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="5e2e1-138">Sobrecargas implícitas para parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="5e2e1-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="5e2e1-139">Um procedimento com um [opcional](../../../../visual-basic/language-reference/modifiers/optional.md) parâmetro é equivalente a dois procedimentos sobrecarregados, um com o parâmetro opcional e outro sem ele.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-139">A procedure with an [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="5e2e1-140">Você não pode sobrecarregar tal procedimento com uma lista de parâmetros correspondente a um deles.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="5e2e1-141">As declarações a seguir ilustram isso.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-141">The following declarations illustrate this.</span></span>  
  
 <span data-ttu-id="5e2e1-142">[!code-vb[VbVbcnProcedures&#58;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5e2e1-142">[!code-vb[VbVbcnProcedures#58](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]</span></span>  
  
 <span data-ttu-id="5e2e1-143">[!code-vb[VbVbcnProcedures&#60;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="5e2e1-143">[!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]</span></span>  
  
 <span data-ttu-id="5e2e1-144">[!code-vb[VbVbcnProcedures&#61;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="5e2e1-144">[!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]</span></span>  
  
 <span data-ttu-id="5e2e1-145">Para um procedimento com mais de um parâmetro opcional, há um conjunto de sobrecargas implícitas, acessou por lógica semelhante ao exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-145">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="5e2e1-146">Sobrecargas implícitas para um parâmetro ParamArray</span><span class="sxs-lookup"><span data-stu-id="5e2e1-146">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="5e2e1-147">O compilador considera um procedimento com um [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parâmetro deverá ter um número infinito de sobrecargas, com diferenças no que o código de chamada passa para a matriz de parâmetros, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="5e2e1-147">The compiler considers a procedure with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
-   <span data-ttu-id="5e2e1-148">Uma sobrecarga para quando o código de chamada não fornece um argumento para o`ParamArray`</span><span class="sxs-lookup"><span data-stu-id="5e2e1-148">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
-   <span data-ttu-id="5e2e1-149">Uma sobrecarga para quando o código de chamada fornece uma matriz unidimensional do `ParamArray` tipo de elemento</span><span class="sxs-lookup"><span data-stu-id="5e2e1-149">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
-   <span data-ttu-id="5e2e1-150">Para cada inteiro positivo, uma sobrecarga para quando o código de chamada fornece esse número de argumentos, cada um a `ParamArray` tipo de elemento</span><span class="sxs-lookup"><span data-stu-id="5e2e1-150">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="5e2e1-151">As seguintes declarações ilustram essas sobrecargas implícitas.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-151">The following declarations illustrate these implicit overloads.</span></span>  
  
 <span data-ttu-id="5e2e1-152">[!code-vb[VbVbcnProcedures&#68;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="5e2e1-152">[!code-vb[VbVbcnProcedures#68](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]</span></span>  
  
 <span data-ttu-id="5e2e1-153">[!code-vb[VbVbcnProcedures&#70;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="5e2e1-153">[!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]</span></span>  
  
 <span data-ttu-id="5e2e1-154">Você não pode sobrecarregar tal procedimento com uma lista de parâmetros que usa uma matriz unidimensional para a matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-154">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="5e2e1-155">No entanto, você pode usar as assinaturas das outras sobrecargas implícitas.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-155">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="5e2e1-156">As declarações a seguir ilustram isso.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-156">The following declarations illustrate this.</span></span>  
  
 <span data-ttu-id="5e2e1-157">[!code-vb[VbVbcnProcedures&#71;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="5e2e1-157">[!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]</span></span>  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="5e2e1-158">Programação sem tipo como uma alternativa para sobrecarga</span><span class="sxs-lookup"><span data-stu-id="5e2e1-158">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="5e2e1-159">Se você quiser permitir que o código de chamada passe diferentes tipos de dados para um parâmetro, uma abordagem alternativa é programação sem tipo.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-159">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="5e2e1-160">Você pode definir o tipo de verificação alternar para `Off` utilizando o [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) ou o [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-160">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) or the [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="5e2e1-161">Em seguida, você não precisa declarar o tipo de dados do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-161">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="5e2e1-162">No entanto, essa abordagem tem as seguintes desvantagens comparadas à sobrecarga:</span><span class="sxs-lookup"><span data-stu-id="5e2e1-162">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
-   <span data-ttu-id="5e2e1-163">Programação sem tipo produz código de execução menos eficiente.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-163">Typeless programming produces less efficient execution code.</span></span>  
  
-   <span data-ttu-id="5e2e1-164">O procedimento deve testar cada tipo de dados que ele prevê que está sendo passada.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-164">The procedure must test for every data type it anticipates being passed.</span></span>  
  
-   <span data-ttu-id="5e2e1-165">O compilador não pode sinalizar um erro se o código de chamada passa um tipo de dados que o procedimento não oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="5e2e1-165">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e2e1-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e2e1-166">See Also</span></span>  
 <span data-ttu-id="5e2e1-167">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="5e2e1-167">[Procedures](./index.md) </span></span>  
<span data-ttu-id="5e2e1-168"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="5e2e1-168"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="5e2e1-169"> [Procedimentos de solução de problemas](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="5e2e1-169"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="5e2e1-170"> [Como: definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="5e2e1-170"> [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md) </span></span>  
<span data-ttu-id="5e2e1-171"> [Como: chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="5e2e1-171"> [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md) </span></span>  
<span data-ttu-id="5e2e1-172"> [Como: sobrecarregar um procedimento que recebe parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="5e2e1-172"> [How to: Overload a Procedure that Takes Optional Parameters](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span></span>  
<span data-ttu-id="5e2e1-173"> [Como: sobrecarregar um procedimento que recebe um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="5e2e1-173"> [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span></span>  
<span data-ttu-id="5e2e1-174"> [Resolução de sobrecarga](./overload-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="5e2e1-174"> [Overload Resolution](./overload-resolution.md) </span></span>  
<span data-ttu-id="5e2e1-175"> [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md)</span><span class="sxs-lookup"><span data-stu-id="5e2e1-175"> [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)</span></span>
