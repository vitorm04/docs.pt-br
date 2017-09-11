---
title: "Resolução de sobrecarga (Visual Basic) | Documentos do Microsoft"
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
- Visual Basic code, procedures
- overload resolution
- procedures, overloading
- procedures, calling
- procedure overloading, overload resolution
- signatures, procedure
- overloads, resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
caps.latest.revision: 21
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
ms.openlocfilehash: a4f350af0f7d964df45974990991a2e94b26551e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="overload-resolution-visual-basic"></a><span data-ttu-id="e7493-102">Resolução de sobrecarga (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7493-102">Overload Resolution (Visual Basic)</span></span>
<span data-ttu-id="e7493-103">Quando o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador encontra uma chamada para um procedimento que é definido em várias versões sobrecarregadas, o compilador deve decidir qual das sobrecargas para chamar.</span><span class="sxs-lookup"><span data-stu-id="e7493-103">When the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler encounters a call to a procedure that is defined in several overloaded versions, the compiler must decide which of the overloads to call.</span></span> <span data-ttu-id="e7493-104">Ele faz isso executando as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="e7493-104">It does this by performing the following steps:</span></span>  
  
1.  <span data-ttu-id="e7493-105">**Acessibilidade.**</span><span class="sxs-lookup"><span data-stu-id="e7493-105">**Accessibility.**</span></span> <span data-ttu-id="e7493-106">Elimina qualquer sobrecarregamento com um nível de acesso que impede o código de chamada de chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="e7493-106">It eliminates any overload with an access level that prevents the calling code from calling it.</span></span>  
  
2.  <span data-ttu-id="e7493-107">**Número de parâmetros.**</span><span class="sxs-lookup"><span data-stu-id="e7493-107">**Number of Parameters.**</span></span> <span data-ttu-id="e7493-108">Elimina qualquer sobrecarregamento que define um número diferente de parâmetros que são fornecidos na chamada.</span><span class="sxs-lookup"><span data-stu-id="e7493-108">It eliminates any overload that defines a different number of parameters than are supplied in the call.</span></span>  
  
3.  <span data-ttu-id="e7493-109">**Tipos de dados do parâmetro.**</span><span class="sxs-lookup"><span data-stu-id="e7493-109">**Parameter Data Types.**</span></span> <span data-ttu-id="e7493-110">O compilador dá preferência de métodos de instância sobre métodos de extensão.</span><span class="sxs-lookup"><span data-stu-id="e7493-110">The compiler gives instance methods preference over extension methods.</span></span> <span data-ttu-id="e7493-111">Se qualquer método de instância for encontrado que requer somente conversões para coincidir com a chamada de procedimento de expansão, todos os métodos de extensão são descartados e o compilador continua com apenas os candidatos a método de instância.</span><span class="sxs-lookup"><span data-stu-id="e7493-111">If any instance method is found that requires only widening conversions to match the procedure call, all extension methods are dropped and the compiler continues with only the instance method candidates.</span></span> <span data-ttu-id="e7493-112">Se esse método de instância não for encontrado, ele continua com métodos de extensão e de instância.</span><span class="sxs-lookup"><span data-stu-id="e7493-112">If no such instance method is found, it continues with both instance and extension methods.</span></span>  
  
     <span data-ttu-id="e7493-113">Nesta etapa, ele elimina qualquer sobrecarregamento para o qual os tipos de dados dos argumentos de chamada não podem ser convertidos para os tipos de parâmetro definidos no sobrecarregamento.</span><span class="sxs-lookup"><span data-stu-id="e7493-113">In this step, it eliminates any overload for which the data types of the calling arguments cannot be converted to the parameter types defined in the overload.</span></span>  
  
4.  <span data-ttu-id="e7493-114">**Conversões de estreitamento.**</span><span class="sxs-lookup"><span data-stu-id="e7493-114">**Narrowing Conversions.**</span></span> <span data-ttu-id="e7493-115">Elimina qualquer sobrecarregamento que exige uma conversão de restrição dos tipos de argumento de chamada para os tipos de parâmetro definido.</span><span class="sxs-lookup"><span data-stu-id="e7493-115">It eliminates any overload that requires a narrowing conversion from the calling argument types to the defined parameter types.</span></span> <span data-ttu-id="e7493-116">Isso é verdadeiro se a verificação de tipo muda ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) é `On` ou `Off`.</span><span class="sxs-lookup"><span data-stu-id="e7493-116">This is true whether the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `On` or `Off`.</span></span>  
  
5.  <span data-ttu-id="e7493-117">**Alargamento mínimo.**</span><span class="sxs-lookup"><span data-stu-id="e7493-117">**Least Widening.**</span></span> <span data-ttu-id="e7493-118">O compilador considera as sobrecargas restantes em pares.</span><span class="sxs-lookup"><span data-stu-id="e7493-118">The compiler considers the remaining overloads in pairs.</span></span> <span data-ttu-id="e7493-119">Para cada par, ele compara os tipos de dados dos parâmetros definidos.</span><span class="sxs-lookup"><span data-stu-id="e7493-119">For each pair, it compares the data types of the defined parameters.</span></span> <span data-ttu-id="e7493-120">Se os tipos em uma das sobrecargas de todos os ampliam para os tipos correspondentes no outro, o compilador elimina o último.</span><span class="sxs-lookup"><span data-stu-id="e7493-120">If the types in one of the overloads all widen to the corresponding types in the other, the compiler eliminates the latter.</span></span> <span data-ttu-id="e7493-121">Ou seja, ele retém o sobrecarregamento que exige o mínimo de ampliação.</span><span class="sxs-lookup"><span data-stu-id="e7493-121">That is, it retains the overload that requires the least amount of widening.</span></span>  
  
6.  <span data-ttu-id="e7493-122">**Único candidato.**</span><span class="sxs-lookup"><span data-stu-id="e7493-122">**Single Candidate.**</span></span> <span data-ttu-id="e7493-123">Continua considerando sobrecargas em pares até que apenas uma sobrecarga permanece e resolve a chamada para essa sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="e7493-123">It continues considering overloads in pairs until only one overload remains, and it resolves the call to that overload.</span></span> <span data-ttu-id="e7493-124">Se o compilador não pode reduzir as sobrecargas para uma única candidata, ele gera um erro.</span><span class="sxs-lookup"><span data-stu-id="e7493-124">If the compiler cannot reduce the overloads to a single candidate, it generates an error.</span></span>  
  
 <span data-ttu-id="e7493-125">A ilustração a seguir mostra o processo que determina que um conjunto de versões sobrecarregadas para chamar.</span><span class="sxs-lookup"><span data-stu-id="e7493-125">The following illustration shows the process that determines which of a set of overloaded versions to call.</span></span>  
  
 <span data-ttu-id="e7493-126">![Diagrama de fluxo do processo de resolução de sobrecarga](./media/overloadres.gif "OverloadRes")</span><span class="sxs-lookup"><span data-stu-id="e7493-126">![Flow diagram of overload resolution process](./media/overloadres.gif "OverloadRes")</span></span>  
<span data-ttu-id="e7493-127">Resolução entre versões sobrecarregadas</span><span class="sxs-lookup"><span data-stu-id="e7493-127">Resolving among overloaded versions</span></span>  
  
 <span data-ttu-id="e7493-128">O exemplo a seguir ilustra esse processo de resolução de sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="e7493-128">The following example illustrates this overload resolution process.</span></span>  
  
 <span data-ttu-id="e7493-129">[!code-vb[VbVbcnProcedures&#62;](./codesnippet/VisualBasic/overload-resolution_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e7493-129">[!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/overload-resolution_1.vb)]</span></span>  
  
 <span data-ttu-id="e7493-130">[!code-vb[VbVbcnProcedures&#63;](./codesnippet/VisualBasic/overload-resolution_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="e7493-130">[!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/overload-resolution_2.vb)]</span></span>  
  
 <span data-ttu-id="e7493-131">Na primeira chamada, o compilador elimina a primeira sobrecarga porque o tipo do primeiro argumento (`Short`) estreita ao tipo do parâmetro correspondente (`Byte`).</span><span class="sxs-lookup"><span data-stu-id="e7493-131">In the first call, the compiler eliminates the first overload because the type of the first argument (`Short`) narrows to the type of the corresponding parameter (`Byte`).</span></span> <span data-ttu-id="e7493-132">Então elimina o terceiro sobrecarregamento porque cada tipo de argumento na segunda sobrecarga (`Short` e `Single`) amplia-se para o tipo correspondente no terceiro sobrecarregamento (`Integer` e `Single`).</span><span class="sxs-lookup"><span data-stu-id="e7493-132">It then eliminates the third overload because each argument type in the second overload (`Short` and `Single`) widens to the corresponding type in the third overload (`Integer` and `Single`).</span></span> <span data-ttu-id="e7493-133">O segundo sobrecarregamento requer menos alargamento, então o compilador usa-o para a chamada.</span><span class="sxs-lookup"><span data-stu-id="e7493-133">The second overload requires less widening, so the compiler uses it for the call.</span></span>  
  
 <span data-ttu-id="e7493-134">Na segunda chamada, o compilador não pode eliminar qualquer uma das sobrecargas com base na restrição.</span><span class="sxs-lookup"><span data-stu-id="e7493-134">In the second call, the compiler cannot eliminate any of the overloads on the basis of narrowing.</span></span> <span data-ttu-id="e7493-135">Elimina o terceiro sobrecarregamento pela mesma razão que na primeira chamada, pois ele pode chamar o segundo sobrecarregamento com menos alargamento de tipos de argumento.</span><span class="sxs-lookup"><span data-stu-id="e7493-135">It eliminates the third overload for the same reason as in the first call, because it can call the second overload with less widening of the argument types.</span></span> <span data-ttu-id="e7493-136">No entanto, o compilador não pode resolver entre as primeira e o segunda sobrecargas.</span><span class="sxs-lookup"><span data-stu-id="e7493-136">However, the compiler cannot resolve between the first and second overloads.</span></span> <span data-ttu-id="e7493-137">Cada um tem um tipo definido de parâmetro que amplia para o tipo correspondente no outro (`Byte` para `Short`, mas `Single` para `Double`).</span><span class="sxs-lookup"><span data-stu-id="e7493-137">Each has one defined parameter type that widens to the corresponding type in the other (`Byte` to `Short`, but `Single` to `Double`).</span></span> <span data-ttu-id="e7493-138">Portanto, o compilador gera um erro de resolução de sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="e7493-138">The compiler therefore generates an overload resolution error.</span></span>  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a><span data-ttu-id="e7493-139">Sobrecarregado opcional e argumentos ParamArray</span><span class="sxs-lookup"><span data-stu-id="e7493-139">Overloaded Optional and ParamArray Arguments</span></span>  
 <span data-ttu-id="e7493-140">Se duas sobrecargas de um procedimento possuem assinaturas idênticas exceto que o último parâmetro é declarado [opcional](../../../../visual-basic/language-reference/modifiers/optional.md) em um e [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) no outro, o compilador resolve uma chamada para o procedimento como se segue:</span><span class="sxs-lookup"><span data-stu-id="e7493-140">If two overloads of a procedure have identical signatures except that the last parameter is declared [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) in one and [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) in the other, the compiler resolves a call to that procedure as follows:</span></span>  
  
|<span data-ttu-id="e7493-141">Se a chamada fornecer o último argumento como</span><span class="sxs-lookup"><span data-stu-id="e7493-141">If the call supplies the last argument as</span></span>|<span data-ttu-id="e7493-142">O compilador resolve a chamada ao sobrecarregamento declarando o último argumento como</span><span class="sxs-lookup"><span data-stu-id="e7493-142">The compiler resolves the call to the overload declaring the last argument as</span></span>|  
|---|---|  
|<span data-ttu-id="e7493-143">Nenhum valor (argumento omitido)</span><span class="sxs-lookup"><span data-stu-id="e7493-143">No value (argument omitted)</span></span>|`Optional`|  
|<span data-ttu-id="e7493-144">Um único valor</span><span class="sxs-lookup"><span data-stu-id="e7493-144">A single value</span></span>|`Optional`|  
|<span data-ttu-id="e7493-145">Dois ou mais valores em uma lista separada por vírgulas</span><span class="sxs-lookup"><span data-stu-id="e7493-145">Two or more values in a comma-separated list</span></span>|`ParamArray`|  
|<span data-ttu-id="e7493-146">Uma matriz de qualquer comprimento (incluindo uma matriz vazia)</span><span class="sxs-lookup"><span data-stu-id="e7493-146">An array of any length (including an empty array)</span></span>|`ParamArray`|  
  
## <a name="see-also"></a><span data-ttu-id="e7493-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7493-147">See Also</span></span>  
 <span data-ttu-id="e7493-148">[Parâmetros opcionais](./optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="e7493-148">[Optional Parameters](./optional-parameters.md) </span></span>  
<span data-ttu-id="e7493-149"> [Matrizes de parâmetros](./parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="e7493-149"> [Parameter Arrays](./parameter-arrays.md) </span></span>  
<span data-ttu-id="e7493-150"> [Sobrecarga de procedimento](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="e7493-150"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="e7493-151"> [Procedimentos de solução de problemas](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="e7493-151"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="e7493-152"> [Como: definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="e7493-152"> [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md) </span></span>  
<span data-ttu-id="e7493-153"> [Como: chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="e7493-153"> [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md) </span></span>  
<span data-ttu-id="e7493-154"> [Como: sobrecarregar um procedimento que recebe parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="e7493-154"> [How to: Overload a Procedure that Takes Optional Parameters](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span></span>  
<span data-ttu-id="e7493-155"> [Como: sobrecarregar um procedimento que recebe um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="e7493-155"> [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span></span>  
<span data-ttu-id="e7493-156"> [Considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="e7493-156"> [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md) </span></span>  
<span data-ttu-id="e7493-157"> [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md) </span><span class="sxs-lookup"><span data-stu-id="e7493-157"> [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) </span></span>  
<span data-ttu-id="e7493-158"> [Métodos de Extensão](./extension-methods.md)</span><span class="sxs-lookup"><span data-stu-id="e7493-158"> [Extension Methods](./extension-methods.md)</span></span>
