---
title: Como sobrecarregar um procedimento que usa um número indefinido de parâmetros
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
ms.openlocfilehash: 047d566c13f03803d2e5c3bc6cce0db56df4a3f0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345843"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="eaeed-102">Como sobrecarregar um procedimento que use um número indefinido de parâmetros (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eaeed-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="eaeed-103">Se um procedimento tiver um parâmetro [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) , você não poderá definir uma versão sobrecarregada usando uma matriz unidimensional para a matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="eaeed-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="eaeed-104">Para obter mais informações, consulte "sobrecargas implícitas para um parâmetro ParamArray" em [Considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="eaeed-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="eaeed-105">Para sobrecarregar um procedimento que usa um número variável de parâmetros</span><span class="sxs-lookup"><span data-stu-id="eaeed-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1. <span data-ttu-id="eaeed-106">Verifique se o procedimento e a chamada lógica de código se beneficia de versões sobrecarregadas mais do que de um parâmetro `ParamArray`.</span><span class="sxs-lookup"><span data-stu-id="eaeed-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="eaeed-107">Consulte "sobrecargas e ParamArrays" em [Considerações sobre os procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="eaeed-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2. <span data-ttu-id="eaeed-108">Determine quais números de valores fornecidos o procedimento deve aceitar na parte variável da lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="eaeed-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="eaeed-109">Isso pode incluir o caso de nenhum valor e pode incluir o caso de uma única matriz unidimensional.</span><span class="sxs-lookup"><span data-stu-id="eaeed-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3. <span data-ttu-id="eaeed-110">Para cada número aceitável de valores fornecidos, grave uma instrução de declaração de `Sub` ou `Function` que define a lista de parâmetros correspondente.</span><span class="sxs-lookup"><span data-stu-id="eaeed-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="eaeed-111">Não use a palavra-chave `Optional` ou `ParamArray` nessa versão sobrecarregada.</span><span class="sxs-lookup"><span data-stu-id="eaeed-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4. <span data-ttu-id="eaeed-112">Em cada declaração, preceda a palavra-chave `Sub` ou `Function` com a palavra-chave [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) .</span><span class="sxs-lookup"><span data-stu-id="eaeed-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5. <span data-ttu-id="eaeed-113">Após cada declaração, escreva o código do procedimento que deve ser executado quando o código de chamada fornecer valores correspondentes à lista de parâmetros da declaração.</span><span class="sxs-lookup"><span data-stu-id="eaeed-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6. <span data-ttu-id="eaeed-114">Encerre cada procedimento com a instrução `End Sub` ou `End Function`, conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="eaeed-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eaeed-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eaeed-115">Example</span></span>  
 <span data-ttu-id="eaeed-116">O exemplo a seguir mostra um procedimento definido com um parâmetro [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) e, em seguida, um conjunto equivalente de procedimentos sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="eaeed-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="eaeed-117">Não é possível sobrecarregar esse procedimento com uma lista de parâmetros que usa uma matriz unidimensional para a matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="eaeed-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="eaeed-118">No entanto, você pode usar as assinaturas das outras sobrecargas implícitas.</span><span class="sxs-lookup"><span data-stu-id="eaeed-118">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="eaeed-119">As declarações a seguir ilustram isso.</span><span class="sxs-lookup"><span data-stu-id="eaeed-119">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 <span data-ttu-id="eaeed-120">O código nas versões sobrecarregadas não precisa testar se o código de chamada forneceu um ou mais valores para o parâmetro `ParamArray` ou, nesse caso, quantos.</span><span class="sxs-lookup"><span data-stu-id="eaeed-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="eaeed-121">Visual Basic passa o controle para a versão que corresponde à lista de argumentos de chamada.</span><span class="sxs-lookup"><span data-stu-id="eaeed-121">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="eaeed-122">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="eaeed-122">Compiling the Code</span></span>  
 <span data-ttu-id="eaeed-123">Como um procedimento com um parâmetro `ParamArray` é equivalente a um conjunto de versões sobrecarregadas, não é possível sobrecarregar esse procedimento com uma lista de parâmetros correspondente a qualquer uma dessas sobrecargas implícitas.</span><span class="sxs-lookup"><span data-stu-id="eaeed-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="eaeed-124">Para obter mais informações, consulte [Considerações sobre sobrecarga de procedimentos](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="eaeed-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="eaeed-125">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="eaeed-125">.NET Framework Security</span></span>  
 <span data-ttu-id="eaeed-126">Sempre que você lida com uma matriz que pode ser indefinidamente grande, há um risco de sobreexecutar alguma capacidade interna de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eaeed-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="eaeed-127">Se você aceitar uma matriz de parâmetros, deverá testar o comprimento da matriz que o código de chamada passou e tomar as medidas apropriadas se for muito grande para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eaeed-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaeed-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eaeed-128">See also</span></span>

- [<span data-ttu-id="eaeed-129">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="eaeed-129">Procedures</span></span>](./index.md)
- [<span data-ttu-id="eaeed-130">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="eaeed-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="eaeed-131">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="eaeed-131">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="eaeed-132">Matrizes de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eaeed-132">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="eaeed-133">Sobrecarga de Procedimento</span><span class="sxs-lookup"><span data-stu-id="eaeed-133">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="eaeed-134">Solução de problemas de Procedimentos</span><span class="sxs-lookup"><span data-stu-id="eaeed-134">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="eaeed-135">Como definir várias versões de um procedimento</span><span class="sxs-lookup"><span data-stu-id="eaeed-135">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="eaeed-136">Como chamar um procedimento sobrecarregado</span><span class="sxs-lookup"><span data-stu-id="eaeed-136">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="eaeed-137">Como sobrecarregar um procedimento que usa parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="eaeed-137">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="eaeed-138">Resolução de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="eaeed-138">Overload Resolution</span></span>](./overload-resolution.md)
