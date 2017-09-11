---
title: "Como: sobrecarregar um procedimento que recebe um número indefinido de parâmetros (Visual Basic) | Documentos do Microsoft"
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
- procedures, parameters
- procedure overloading, indefinite number of parameters
- procedures, defining
- Visual Basic code, procedures
- procedure parameters
- procedures, overloading
- procedures, multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
caps.latest.revision: 18
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
ms.openlocfilehash: 3e4ef81049f3b0d3ab1271fb709f07c37f274a88
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="be6d7-102">Como sobrecarregar um procedimento que use um número indefinido de parâmetros (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be6d7-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="be6d7-103">Se um procedimento tem um [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parâmetro, você não pode definir uma versão sobrecarregada, levando a uma matriz unidimensional para a matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="be6d7-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="be6d7-104">Para obter mais informações, consulte "Implícita sobrecargas para um parâmetro ParamArray" [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="be6d7-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="be6d7-105">Para sobrecarregar um procedimento que recebe um número variável de parâmetros</span><span class="sxs-lookup"><span data-stu-id="be6d7-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1.  <span data-ttu-id="be6d7-106">Verificar se o procedimento e chamar os benefícios da lógica de código de versões sobrecarregadas mais do que de um `ParamArray` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="be6d7-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="be6d7-107">Consulte "Sobrecargas e ParamArrays" [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="be6d7-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2.  <span data-ttu-id="be6d7-108">Determine quais números de valores fornecidos o procedimento deve aceitar a variável parte da lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="be6d7-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="be6d7-109">Isso pode incluir o caso de nenhum valor, e podem incluir o caso de uma única matriz unidimensional.</span><span class="sxs-lookup"><span data-stu-id="be6d7-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3.  <span data-ttu-id="be6d7-110">Para cada número aceitável de valores fornecidos, escreva uma `Sub` ou `Function` declaração que define a lista de parâmetros correspondente.</span><span class="sxs-lookup"><span data-stu-id="be6d7-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="be6d7-111">Não usar o `Optional` ou `ParamArray` palavra-chave nesta versão sobrecarregada.</span><span class="sxs-lookup"><span data-stu-id="be6d7-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4.  <span data-ttu-id="be6d7-112">Em cada declaração, preceda o `Sub` ou `Function` palavra-chave com o [sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="be6d7-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5.  <span data-ttu-id="be6d7-113">Seguindo cada declaração, escreva o código de procedimento que deve ser executado quando o código de chamada fornece valores correspondentes à lista de parâmetros da declaração.</span><span class="sxs-lookup"><span data-stu-id="be6d7-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6.  <span data-ttu-id="be6d7-114">Termine cada procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="be6d7-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be6d7-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="be6d7-115">Example</span></span>  
 <span data-ttu-id="be6d7-116">O exemplo a seguir mostra um procedimento definido com um [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parâmetro e, em seguida, um conjunto equivalente de procedimentos sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="be6d7-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 <span data-ttu-id="be6d7-117">[!code-vb[VbVbcnProcedures&#69;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="be6d7-117">[!code-vb[VbVbcnProcedures#69](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]</span></span>  
  
 <span data-ttu-id="be6d7-118">[!code-vb[VbVbcnProcedures&#70;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="be6d7-118">[!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]</span></span>  
  
 <span data-ttu-id="be6d7-119">Você não pode sobrecarregar tal procedimento com uma lista de parâmetros que usa uma matriz unidimensional para a matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="be6d7-119">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="be6d7-120">No entanto, você pode usar as assinaturas das outras sobrecargas implícitas.</span><span class="sxs-lookup"><span data-stu-id="be6d7-120">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="be6d7-121">As declarações a seguir ilustram isso.</span><span class="sxs-lookup"><span data-stu-id="be6d7-121">The following declarations illustrate this.</span></span>  
  
 <span data-ttu-id="be6d7-122">[!code-vb[VbVbcnProcedures&#71;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="be6d7-122">[!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]</span></span>  
  
 <span data-ttu-id="be6d7-123">O código nas versões sobrecarregadas não precisa testar se o código de chamada fornecido um ou mais valores para o `ParamArray` parâmetro, ou em caso afirmativo, quantos.</span><span class="sxs-lookup"><span data-stu-id="be6d7-123">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="be6d7-124">passa o controle para a versão correspondente a lista de argumentos de chamada.</span><span class="sxs-lookup"><span data-stu-id="be6d7-124"> passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="be6d7-125">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="be6d7-125">Compiling the Code</span></span>  
 <span data-ttu-id="be6d7-126">Porque um procedimento com um `ParamArray` parâmetro é equivalente a um conjunto de versões sobrecarregadas, você não pode sobrecarregar tal procedimento com uma lista de parâmetros correspondente a qualquer essas sobrecargas implícitas.</span><span class="sxs-lookup"><span data-stu-id="be6d7-126">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="be6d7-127">Para obter mais informações, consulte [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="be6d7-127">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="be6d7-128">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="be6d7-128">.NET Framework Security</span></span>  
 <span data-ttu-id="be6d7-129">Sempre que você lida com uma matriz que pode ser indefinidamente grande, há um risco de ultrapassar alguma capacidade interna de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="be6d7-129">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="be6d7-130">Se você aceitar uma matriz de parâmetros, deve testar o comprimento da matriz, o código de chamada passado para ele e tomar as medidas adequadas se ele for muito grande para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="be6d7-130">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be6d7-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be6d7-131">See Also</span></span>  
 <span data-ttu-id="be6d7-132">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="be6d7-132">[Procedures](./index.md) </span></span>  
<span data-ttu-id="be6d7-133"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="be6d7-133"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="be6d7-134"> [Parâmetros opcionais](./optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="be6d7-134"> [Optional Parameters](./optional-parameters.md) </span></span>  
<span data-ttu-id="be6d7-135"> [Matrizes de parâmetros](./parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="be6d7-135"> [Parameter Arrays](./parameter-arrays.md) </span></span>  
<span data-ttu-id="be6d7-136"> [Sobrecarga de procedimento](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="be6d7-136"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="be6d7-137"> [Procedimentos de solução de problemas](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="be6d7-137"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="be6d7-138"> [Como: definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="be6d7-138"> [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md) </span></span>  
<span data-ttu-id="be6d7-139"> [Como: chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="be6d7-139"> [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md) </span></span>  
<span data-ttu-id="be6d7-140"> [Como: sobrecarregar um procedimento que recebe parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="be6d7-140"> [How to: Overload a Procedure that Takes Optional Parameters](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span></span>  
<span data-ttu-id="be6d7-141"> [Resolução de Sobrecarga](./overload-resolution.md)</span><span class="sxs-lookup"><span data-stu-id="be6d7-141"> [Overload Resolution](./overload-resolution.md)</span></span>
