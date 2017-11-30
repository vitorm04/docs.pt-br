---
title: "Considerações sobre procedimentos de sobrecarga (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c9a9a4759d4ec2dd87778c49c4fd82a08c081a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="aa262-102">Considerações sobre procedimentos de sobrecarga (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa262-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="aa262-103">Ao sobrecarregar um procedimento, você deve usar outro *assinatura* para cada versão sobrecarregada.</span><span class="sxs-lookup"><span data-stu-id="aa262-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="aa262-104">Geralmente, isso significa que cada versão deve especificar uma lista de parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="aa262-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="aa262-105">Para obter mais informações, consulte "Assinatura diferente" em [sobrecarga de procedimento](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="aa262-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="aa262-106">Você pode sobrecarregar uma `Function` procedimento com uma `Sub` procedimento e vice-versa, que tenham assinaturas diferentes.</span><span class="sxs-lookup"><span data-stu-id="aa262-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="aa262-107">Duas sobrecargas não podem diferir somente em que um tem um valor de retorno e o outro não.</span><span class="sxs-lookup"><span data-stu-id="aa262-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="aa262-108">Você pode sobrecarregar uma propriedade da mesma maneira que você sobrecarregar um procedimento e com as mesmas restrições.</span><span class="sxs-lookup"><span data-stu-id="aa262-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="aa262-109">No entanto, você não pode sobrecarregar um procedimento com uma propriedade, ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="aa262-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="aa262-110">Alternativas para versões sobrecarregadas</span><span class="sxs-lookup"><span data-stu-id="aa262-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="aa262-111">Às vezes, você tem alternativas para versões sobrecarregadas, particularmente quando a presença de argumentos é opcional ou seu número é variável.</span><span class="sxs-lookup"><span data-stu-id="aa262-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="aa262-112">Tenha em mente que argumentos opcionais não são necessariamente suportados por todos os idiomas e matrizes de parâmetros são limitadas a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aa262-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="aa262-113">Se você estiver escrevendo um procedimento que pode ser chamado de código escrito em qualquer um dos vários idiomas diferentes, versões sobrecarregadas oferecem maior flexibilidade.</span><span class="sxs-lookup"><span data-stu-id="aa262-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="aa262-114">Sobrecargas e argumentos opcionais</span><span class="sxs-lookup"><span data-stu-id="aa262-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="aa262-115">Quando o código de chamada pode opcionalmente fornecer ou omitir um ou mais argumentos, você pode definir várias versões sobrecarregados ou usar parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="aa262-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="aa262-116">Quando usar versões sobrecarregadas</span><span class="sxs-lookup"><span data-stu-id="aa262-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="aa262-117">Você pode considerar definir uma série de versões sobrecarregadas nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="aa262-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="aa262-118">A lógica no código do procedimento é significativamente diferente dependendo se o código de chamada fornece um argumento opcional ou não.</span><span class="sxs-lookup"><span data-stu-id="aa262-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
-   <span data-ttu-id="aa262-119">O código do procedimento não pode testar com confiança se o código de chamada forneceu um argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="aa262-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="aa262-120">Esse é o caso, por exemplo, se não houver nenhum candidato possível para um valor padrão que o código de chamada pode não ser esperado para fornecer.</span><span class="sxs-lookup"><span data-stu-id="aa262-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="aa262-121">Quando usar parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="aa262-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="aa262-122">Talvez você prefira uma ou mais parâmetros opcionais nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="aa262-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
-   <span data-ttu-id="aa262-123">A única ação necessária quando o código de chamada não fornece um argumento opcional é definir o parâmetro para um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="aa262-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="aa262-124">Nesse caso, o código do procedimento pode ser menos complicado se você definir uma única versão com um ou mais `Optional` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="aa262-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="aa262-125">Para obter mais informações, consulte [parâmetros opcionais](./optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="aa262-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="aa262-126">Sobrecargas e ParamArrays</span><span class="sxs-lookup"><span data-stu-id="aa262-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="aa262-127">Quando o código de chamada pode passar um número variável de argumentos, você pode definir várias versões sobrecarregados ou usar uma matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="aa262-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="aa262-128">Quando usar versões sobrecarregadas</span><span class="sxs-lookup"><span data-stu-id="aa262-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="aa262-129">Você pode considerar definir uma série de versões sobrecarregadas nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="aa262-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="aa262-130">Você sabe que o código de chamada nunca passa mais do que um pequeno número de valores para a matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="aa262-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
-   <span data-ttu-id="aa262-131">A lógica no código do procedimento é significativamente diferente dependendo de quantos valores o código de chamada passa.</span><span class="sxs-lookup"><span data-stu-id="aa262-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
-   <span data-ttu-id="aa262-132">O código de chamada pode passar valores de diferentes tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="aa262-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="aa262-133">Quando usar uma matriz de parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa262-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="aa262-134">Melhor você é atendidas por um `ParamArray` parâmetro nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="aa262-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
-   <span data-ttu-id="aa262-135">Não é possível prever quantos valores o código de chamada pode passar para a matriz de parâmetros, e pode ser um número grande.</span><span class="sxs-lookup"><span data-stu-id="aa262-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
-   <span data-ttu-id="aa262-136">A lógica do procedimento se presta a iteração de todos os valores que o código de chamada passa, executando essencialmente as mesmas operações em cada valor.</span><span class="sxs-lookup"><span data-stu-id="aa262-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="aa262-137">Para obter mais informações, consulte [matrizes de parâmetro](./parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="aa262-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="aa262-138">Sobrecargas implícitas para parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="aa262-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="aa262-139">Um procedimento com um [opcional](../../../../visual-basic/language-reference/modifiers/optional.md) parâmetro é equivalente a dois procedimentos sobrecarregados, um com o parâmetro opcional e outro sem ele.</span><span class="sxs-lookup"><span data-stu-id="aa262-139">A procedure with an [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="aa262-140">Você não pode sobrecarregar tal procedimento com uma lista de parâmetros correspondentes a qualquer uma delas.</span><span class="sxs-lookup"><span data-stu-id="aa262-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="aa262-141">As declarações a seguir ilustram isso.</span><span class="sxs-lookup"><span data-stu-id="aa262-141">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#58](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]  
  
 <span data-ttu-id="aa262-142">Para um procedimento com mais de um parâmetro opcional, há um conjunto de sobrecargas implícitas, acessou pela lógica semelhante ao exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="aa262-142">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="aa262-143">Sobrecargas implícitas para um parâmetro ParamArray</span><span class="sxs-lookup"><span data-stu-id="aa262-143">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="aa262-144">O compilador considera um procedimento com um [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parâmetro deverá ter um número infinito de sobrecargas, com diferenças no que o código de chamada passa para a matriz de parâmetros, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="aa262-144">The compiler considers a procedure with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
-   <span data-ttu-id="aa262-145">Uma sobrecarga para quando o código de chamada não fornece um argumento para o`ParamArray`</span><span class="sxs-lookup"><span data-stu-id="aa262-145">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
-   <span data-ttu-id="aa262-146">Uma sobrecarga para quando o código de chamada fornece uma matriz unidimensional do `ParamArray` tipo de elemento</span><span class="sxs-lookup"><span data-stu-id="aa262-146">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
-   <span data-ttu-id="aa262-147">Para cada inteiro positivo, uma sobrecarga para quando o código de chamada fornece esse número de argumentos, cada uma da `ParamArray` tipo de elemento</span><span class="sxs-lookup"><span data-stu-id="aa262-147">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="aa262-148">As seguintes declarações ilustram essas sobrecargas implícitas.</span><span class="sxs-lookup"><span data-stu-id="aa262-148">The following declarations illustrate these implicit overloads.</span></span>  
  
 [!code-vb[VbVbcnProcedures#68](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]  
  
 <span data-ttu-id="aa262-149">Você não pode sobrecarregar tal procedimento com uma lista de parâmetros que usa uma matriz unidimensional para a matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="aa262-149">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="aa262-150">No entanto, você pode usar as assinaturas das outras sobrecargas implícitas.</span><span class="sxs-lookup"><span data-stu-id="aa262-150">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="aa262-151">As declarações a seguir ilustram isso.</span><span class="sxs-lookup"><span data-stu-id="aa262-151">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="aa262-152">Programação sem tipo como uma alternativa para sobrecarga</span><span class="sxs-lookup"><span data-stu-id="aa262-152">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="aa262-153">Se você quiser permitir que o código de chamada passe diferentes tipos de dados para um parâmetro, uma abordagem alternativa é programação sem tipo.</span><span class="sxs-lookup"><span data-stu-id="aa262-153">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="aa262-154">Você pode definir o tipo de comutador para a verificação `Off` com o o [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) ou [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="aa262-154">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) or the [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="aa262-155">Em seguida, você não precisa declarar o tipo de dados do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="aa262-155">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="aa262-156">No entanto, essa abordagem tem as seguintes desvantagens comparadas à sobrecarga:</span><span class="sxs-lookup"><span data-stu-id="aa262-156">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
-   <span data-ttu-id="aa262-157">Programação sem tipo produz código de execução menos eficiente.</span><span class="sxs-lookup"><span data-stu-id="aa262-157">Typeless programming produces less efficient execution code.</span></span>  
  
-   <span data-ttu-id="aa262-158">O procedimento deve testar cada tipo de dados que ele prevê que está sendo passado.</span><span class="sxs-lookup"><span data-stu-id="aa262-158">The procedure must test for every data type it anticipates being passed.</span></span>  
  
-   <span data-ttu-id="aa262-159">O compilador não pode sinalizar um erro se o código de chamada passa um tipo de dados que o procedimento não oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="aa262-159">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa262-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa262-160">See Also</span></span>  
 [<span data-ttu-id="aa262-161">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="aa262-161">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="aa262-162">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="aa262-162">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="aa262-163">Solução de problemas de Procedimentos</span><span class="sxs-lookup"><span data-stu-id="aa262-163">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="aa262-164">Como definir várias versões de um procedimento</span><span class="sxs-lookup"><span data-stu-id="aa262-164">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="aa262-165">Como chamar um procedimento sobrecarregado</span><span class="sxs-lookup"><span data-stu-id="aa262-165">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="aa262-166">Como sobrecarregar um procedimento que usa parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="aa262-166">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="aa262-167">Como sobrecarregar um procedimento que usa um número indefinido de parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa262-167">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="aa262-168">Resolução de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="aa262-168">Overload Resolution</span></span>](./overload-resolution.md)  
 [<span data-ttu-id="aa262-169">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="aa262-169">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
