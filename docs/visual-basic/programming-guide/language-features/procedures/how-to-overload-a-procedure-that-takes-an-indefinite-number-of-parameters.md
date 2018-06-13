---
title: Como sobrecarregar um procedimento que use um número indefinido de parâmetros (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: 026dd59db135e8b195ae014aaff5e3a6a7846fc7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651486"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="bfb91-102">Como sobrecarregar um procedimento que use um número indefinido de parâmetros (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bfb91-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="bfb91-103">Se um procedimento tem um [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parâmetro, você não pode definir uma versão sobrecarregada colocar uma matriz unidimensional para a matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="bfb91-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="bfb91-104">Para obter mais informações, consulte "Implícita sobrecargas para um parâmetro ParamArray" em [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="bfb91-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="bfb91-105">Para sobrecarregar um procedimento que usa um número variável de parâmetros</span><span class="sxs-lookup"><span data-stu-id="bfb91-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1.  <span data-ttu-id="bfb91-106">Verificar se o procedimento e chamar os benefícios de lógica de código de sobrecarregado versões mais de um `ParamArray` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bfb91-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="bfb91-107">Consulte "Sobrecargas e ParamArrays" [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="bfb91-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2.  <span data-ttu-id="bfb91-108">Determine quais números de valores fornecidos o procedimento deve aceitar a variável parte da lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="bfb91-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="bfb91-109">Isso pode incluir o caso de nenhum valor, e podem incluir no caso de uma matriz unidimensional.</span><span class="sxs-lookup"><span data-stu-id="bfb91-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3.  <span data-ttu-id="bfb91-110">Para cada número aceitável de valores fornecidos, escreva uma `Sub` ou `Function` declaração que define a lista de parâmetros correspondentes.</span><span class="sxs-lookup"><span data-stu-id="bfb91-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="bfb91-111">Não use o `Optional` ou `ParamArray` palavra-chave nesta versão sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="bfb91-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4.  <span data-ttu-id="bfb91-112">Em cada declaração, preceda o `Sub` ou `Function` palavra-chave with a [sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="bfb91-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5.  <span data-ttu-id="bfb91-113">Seguindo cada declaração, escreva o código de procedimento que deve ser executado quando o código de chamada fornece valores correspondentes à lista de parâmetros que da declaração.</span><span class="sxs-lookup"><span data-stu-id="bfb91-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6.  <span data-ttu-id="bfb91-114">Termine cada procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="bfb91-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfb91-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bfb91-115">Example</span></span>  
 <span data-ttu-id="bfb91-116">O exemplo a seguir mostra um procedimento definido com um [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parâmetro e, em seguida, um conjunto equivalente de procedimentos sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="bfb91-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]  
  
 <span data-ttu-id="bfb91-117">Você não pode sobrecarregar tal procedimento com uma lista de parâmetros que usa uma matriz unidimensional para a matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="bfb91-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="bfb91-118">No entanto, você pode usar as assinaturas das outras sobrecargas implícitas.</span><span class="sxs-lookup"><span data-stu-id="bfb91-118">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="bfb91-119">As declarações a seguir ilustram isso.</span><span class="sxs-lookup"><span data-stu-id="bfb91-119">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]  
  
 <span data-ttu-id="bfb91-120">Não tem o código nas versões sobrecarregados testar se o código de chamada fornecido um ou mais valores para o `ParamArray` parâmetro, ou em caso afirmativo, a quantidade.</span><span class="sxs-lookup"><span data-stu-id="bfb91-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="bfb91-121">Visual Basic passa o controle para a versão correspondente a lista de argumentos de chamada.</span><span class="sxs-lookup"><span data-stu-id="bfb91-121">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bfb91-122">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="bfb91-122">Compiling the Code</span></span>  
 <span data-ttu-id="bfb91-123">Porque um procedimento com um `ParamArray` parâmetro é equivalente a um conjunto de versões sobrecarregadas, você não pode sobrecarregar tal procedimento com uma lista de parâmetros que corresponde a qualquer essas sobrecargas implícitas.</span><span class="sxs-lookup"><span data-stu-id="bfb91-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="bfb91-124">Para obter mais informações, consulte [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="bfb91-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="bfb91-125">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bfb91-125">.NET Framework Security</span></span>  
 <span data-ttu-id="bfb91-126">Sempre que você lidar com uma matriz que pode ser indefinidamente grande, há um risco de ultrapassar alguma capacidade interna de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bfb91-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="bfb91-127">Se você aceitar uma matriz de parâmetros, deve-se de teste para o comprimento da matriz passado pelo código de chamada e execute as etapas apropriadas se ele é muito grande para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bfb91-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfb91-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bfb91-128">See Also</span></span>  
 [<span data-ttu-id="bfb91-129">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="bfb91-129">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="bfb91-130">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="bfb91-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="bfb91-131">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="bfb91-131">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="bfb91-132">Matrizes de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bfb91-132">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="bfb91-133">Sobrecarga de Procedimento</span><span class="sxs-lookup"><span data-stu-id="bfb91-133">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="bfb91-134">Solução de problemas de Procedimentos</span><span class="sxs-lookup"><span data-stu-id="bfb91-134">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="bfb91-135">Como definir várias versões de um procedimento</span><span class="sxs-lookup"><span data-stu-id="bfb91-135">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="bfb91-136">Como chamar um procedimento sobrecarregado</span><span class="sxs-lookup"><span data-stu-id="bfb91-136">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="bfb91-137">Como sobrecarregar um procedimento que usa parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="bfb91-137">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="bfb91-138">Resolução de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="bfb91-138">Overload Resolution</span></span>](./overload-resolution.md)
