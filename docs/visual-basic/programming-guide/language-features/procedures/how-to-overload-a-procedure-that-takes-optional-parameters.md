---
title: Como sobrecarregar um procedimento que usa parâmetros opcionais
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: 4d31980e4b968cff274091ba4f307dffddab1100
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350860"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="071dd-102">Como sobrecarregar um procedimento que usa parâmetros opcionais (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="071dd-102">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="071dd-103">Se um procedimento tiver um ou mais parâmetros [opcionais](../../../../visual-basic/language-reference/modifiers/optional.md) , você não poderá definir uma versão sobrecarregada que corresponda a qualquer uma de suas sobrecargas implícitas.</span><span class="sxs-lookup"><span data-stu-id="071dd-103">If a procedure has one or more [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="071dd-104">Para obter mais informações, consulte "sobrecargas implícitas para parâmetros opcionais" em [Considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="071dd-104">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="071dd-105">Um parâmetro opcional</span><span class="sxs-lookup"><span data-stu-id="071dd-105">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="071dd-106">Para sobrecarregar um procedimento que recebe um parâmetro opcional</span><span class="sxs-lookup"><span data-stu-id="071dd-106">To overload a procedure that takes one optional parameter</span></span>  
  
1. <span data-ttu-id="071dd-107">Escreva uma instrução de declaração de `Sub` ou `Function` que inclua o parâmetro opcional na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="071dd-107">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="071dd-108">Não use a palavra-chave `Optional` nesta versão sobrecarregada.</span><span class="sxs-lookup"><span data-stu-id="071dd-108">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2. <span data-ttu-id="071dd-109">Preceda a palavra-chave `Sub` ou `Function` com a palavra-chave [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) .</span><span class="sxs-lookup"><span data-stu-id="071dd-109">Precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3. <span data-ttu-id="071dd-110">Escreva o código de procedimento que deve ser executado quando o código de chamada fornecer o argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="071dd-110">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4. <span data-ttu-id="071dd-111">Encerre o procedimento com a instrução `End Sub` ou `End Function`, conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="071dd-111">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5. <span data-ttu-id="071dd-112">Escreva uma segunda declaração de declaração que seja idêntica à primeira declaração, exceto que ela não inclui o parâmetro opcional na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="071dd-112">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6. <span data-ttu-id="071dd-113">Escreva o código de procedimento que deve ser executado quando o código de chamada não fornecer o argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="071dd-113">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="071dd-114">Encerre o procedimento com a instrução `End Sub` ou `End Function`, conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="071dd-114">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="071dd-115">O exemplo a seguir mostra um procedimento definido com um parâmetro opcional, um conjunto equivalente de dois procedimentos sobrecarregados e, por fim, exemplos de versões sobrecarregadas válidas e válidas.</span><span class="sxs-lookup"><span data-stu-id="071dd-115">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="071dd-116">Vários parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="071dd-116">Multiple Optional Parameters</span></span>  
 <span data-ttu-id="071dd-117">Para um procedimento com mais de um parâmetro opcional, normalmente você precisa de mais de duas versões sobrecarregadas.</span><span class="sxs-lookup"><span data-stu-id="071dd-117">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="071dd-118">Por exemplo, se houver dois parâmetros opcionais e o código de chamada puder fornecer ou omitir cada um independente do outro, você precisará de quatro versões sobrecarregadas, uma para cada combinação possível de argumentos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="071dd-118">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="071dd-119">À medida que aumenta o número de parâmetros opcionais, a complexidade da sobrecarga aumenta.</span><span class="sxs-lookup"><span data-stu-id="071dd-119">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="071dd-120">A menos que algumas combinações de argumentos fornecidos não sejam aceitáveis, para N parâmetros opcionais, você precisará de 2 ^ N versões sobrecarregadas.</span><span class="sxs-lookup"><span data-stu-id="071dd-120">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="071dd-121">Dependendo da natureza do procedimento, você pode achar que a clareza da lógica justifica o esforço extra de definir todas as versões sobrecarregadas.</span><span class="sxs-lookup"><span data-stu-id="071dd-121">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="071dd-122">Para sobrecarregar um procedimento que usa mais de um parâmetro opcional</span><span class="sxs-lookup"><span data-stu-id="071dd-122">To overload a procedure that takes more than one optional parameter</span></span>  
  
1. <span data-ttu-id="071dd-123">Determine quais combinações de argumentos opcionais fornecidos são aceitáveis para a lógica do procedimento.</span><span class="sxs-lookup"><span data-stu-id="071dd-123">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="071dd-124">Uma combinação inaceitável pode surgir se um parâmetro opcional depender de outro.</span><span class="sxs-lookup"><span data-stu-id="071dd-124">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="071dd-125">Por exemplo, se um parâmetro aceitar o nome de uma pessoa e outro aceitar a idade da pessoa, uma combinação de argumentos que fornece a idade, mas omitir o nome, será inaceitável.</span><span class="sxs-lookup"><span data-stu-id="071dd-125">For example, if one parameter accepts a person's name and another accepts the person's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2. <span data-ttu-id="071dd-126">Para cada combinação aceitável de argumentos opcionais fornecidos, escreva uma instrução de declaração de `Sub` ou de `Function` que define a lista de parâmetros correspondente.</span><span class="sxs-lookup"><span data-stu-id="071dd-126">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="071dd-127">Não use a palavra-chave `Optional`.</span><span class="sxs-lookup"><span data-stu-id="071dd-127">Do not use the `Optional` keyword.</span></span>  
  
3. <span data-ttu-id="071dd-128">Em cada declaração, preceda a palavra-chave `Sub` ou `Function` com a palavra-chave [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) .</span><span class="sxs-lookup"><span data-stu-id="071dd-128">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4. <span data-ttu-id="071dd-129">Após cada declaração, escreva o código do procedimento que deve ser executado quando o código de chamada fornecer uma lista de argumentos correspondente à lista de parâmetros da declaração.</span><span class="sxs-lookup"><span data-stu-id="071dd-129">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5. <span data-ttu-id="071dd-130">Encerre cada procedimento com a instrução `End Sub` ou `End Function`, conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="071dd-130">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="071dd-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="071dd-131">See also</span></span>

- [<span data-ttu-id="071dd-132">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="071dd-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="071dd-133">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="071dd-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="071dd-134">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="071dd-134">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="071dd-135">Matrizes de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="071dd-135">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="071dd-136">Sobrecarga de Procedimento</span><span class="sxs-lookup"><span data-stu-id="071dd-136">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="071dd-137">Solução de problemas de Procedimentos</span><span class="sxs-lookup"><span data-stu-id="071dd-137">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="071dd-138">Como definir várias versões de um procedimento</span><span class="sxs-lookup"><span data-stu-id="071dd-138">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="071dd-139">Como chamar um procedimento sobrecarregado</span><span class="sxs-lookup"><span data-stu-id="071dd-139">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="071dd-140">Como sobrecarregar um procedimento que usa um número indefinido de parâmetros</span><span class="sxs-lookup"><span data-stu-id="071dd-140">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="071dd-141">Resolução de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="071dd-141">Overload Resolution</span></span>](./overload-resolution.md)
