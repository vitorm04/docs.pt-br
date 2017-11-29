---
title: "Como sobrecarregar um procedimento que usa parâmetros opcionais (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b4a863944d4f9ab265aab52578fbb704ca376de5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="c2833-102">Como sobrecarregar um procedimento que usa parâmetros opcionais (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2833-102">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="c2833-103">Se um procedimento tem um ou mais [opcional](../../../../visual-basic/language-reference/modifiers/optional.md) parâmetros, você não pode definir uma versão sobrecarregada corresponde a nenhuma das suas sobrecargas implícitas.</span><span class="sxs-lookup"><span data-stu-id="c2833-103">If a procedure has one or more [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="c2833-104">Para obter mais informações, consulte "Sobrecargas implícitas para parâmetros opcionais" em [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c2833-104">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="c2833-105">Um parâmetro opcional</span><span class="sxs-lookup"><span data-stu-id="c2833-105">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="c2833-106">Para sobrecarregar um procedimento que recebe um parâmetro opcional</span><span class="sxs-lookup"><span data-stu-id="c2833-106">To overload a procedure that takes one optional parameter</span></span>  
  
1.  <span data-ttu-id="c2833-107">Gravar um `Sub` ou `Function` declaração que inclua o parâmetro opcional na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c2833-107">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="c2833-108">Não use o `Optional` palavra-chave nesta versão sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="c2833-108">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2.  <span data-ttu-id="c2833-109">Preceder o `Sub` ou `Function` palavra-chave with a [sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="c2833-109">Precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3.  <span data-ttu-id="c2833-110">Escreva o código de procedimento que deve ser executado quando o código de chamada fornece o argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="c2833-110">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4.  <span data-ttu-id="c2833-111">Termine o procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="c2833-111">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5.  <span data-ttu-id="c2833-112">Grave uma segunda instrução de declaração que é idêntica à primeira, exceto que ele não inclui o parâmetro opcional na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c2833-112">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6.  <span data-ttu-id="c2833-113">Escreva o código de procedimento que deve ser executado quando o código de chamada não fornecer o argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="c2833-113">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="c2833-114">Termine o procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="c2833-114">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="c2833-115">O exemplo a seguir mostra um procedimento definido com um parâmetro opcional, um conjunto equivalente de dois procedimentos sobrecarregados e finalmente exemplos de versões sobrecarregadas inválidos e válidos.</span><span class="sxs-lookup"><span data-stu-id="c2833-115">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_2.vb)]  
  
     [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_3.vb)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="c2833-116">Vários parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="c2833-116">Multiple Optional Parameters</span></span>  
 <span data-ttu-id="c2833-117">Para um procedimento com mais de um parâmetro opcional, você normalmente precisa de mais de duas versões sobrecarregadas.</span><span class="sxs-lookup"><span data-stu-id="c2833-117">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="c2833-118">Por exemplo, se houver dois parâmetros opcionais, e o código de chamada pode fornecer ou omitir cada um deles independentemente uns dos outros, você precisa de quatro versões sobrecarregadas, uma para cada combinação possível de argumentos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="c2833-118">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="c2833-119">Como o número de parâmetros opcionais aumenta, aumenta a complexidade do sobrecarregamento.</span><span class="sxs-lookup"><span data-stu-id="c2833-119">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="c2833-120">A menos que algumas combinações de argumentos fornecidos não são aceitáveis, para parâmetros opcionais N você precisa de 2 ^ N sobrecarregado versões.</span><span class="sxs-lookup"><span data-stu-id="c2833-120">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="c2833-121">Dependendo da natureza do procedimento, você pode achar que a clareza da lógica justifica o esforço extra de definir todas as versões sobrecarregadas.</span><span class="sxs-lookup"><span data-stu-id="c2833-121">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="c2833-122">Para sobrecarregar um procedimento que usa mais de um parâmetro opcional</span><span class="sxs-lookup"><span data-stu-id="c2833-122">To overload a procedure that takes more than one optional parameter</span></span>  
  
1.  <span data-ttu-id="c2833-123">Determine quais combinações de argumentos opcionais fornecidos são aceitáveis para a lógica do procedimento.</span><span class="sxs-lookup"><span data-stu-id="c2833-123">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="c2833-124">Uma combinação inaceitável pode surgir se um parâmetro opcional depende de outro.</span><span class="sxs-lookup"><span data-stu-id="c2833-124">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="c2833-125">Por exemplo, se um parâmetro aceita um cônjuge e outro aceita a idade do cônjuge, uma combinação de argumentos fornecendo a idade mas omitindo o nome é inaceitável.</span><span class="sxs-lookup"><span data-stu-id="c2833-125">For example, if one parameter accepts a spouse's name and another accepts the spouse's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2.  <span data-ttu-id="c2833-126">Para cada combinação aceitável de argumentos opcionais fornecidos, escreva uma `Sub` ou `Function` declaração que define a lista de parâmetros correspondentes.</span><span class="sxs-lookup"><span data-stu-id="c2833-126">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="c2833-127">Não use o `Optional` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="c2833-127">Do not use the `Optional` keyword.</span></span>  
  
3.  <span data-ttu-id="c2833-128">Em cada declaração, preceda o `Sub` ou `Function` palavra-chave with a [sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="c2833-128">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4.  <span data-ttu-id="c2833-129">Seguindo cada declaração, escreva o código de procedimento que deve ser executado quando o código de chamada fornece uma lista de argumentos correspondente à lista de parâmetros que da declaração.</span><span class="sxs-lookup"><span data-stu-id="c2833-129">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5.  <span data-ttu-id="c2833-130">Termine cada procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="c2833-130">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2833-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2833-131">See Also</span></span>  
 [<span data-ttu-id="c2833-132">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="c2833-132">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="c2833-133">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="c2833-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="c2833-134">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="c2833-134">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="c2833-135">Matrizes de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2833-135">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="c2833-136">Sobrecarga de Procedimento</span><span class="sxs-lookup"><span data-stu-id="c2833-136">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="c2833-137">Solução de problemas de Procedimentos</span><span class="sxs-lookup"><span data-stu-id="c2833-137">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="c2833-138">Como definir várias versões de um procedimento</span><span class="sxs-lookup"><span data-stu-id="c2833-138">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="c2833-139">Como chamar um procedimento sobrecarregado</span><span class="sxs-lookup"><span data-stu-id="c2833-139">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="c2833-140">Como sobrecarregar um procedimento que usa um número indefinido de parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2833-140">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="c2833-141">Resolução de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="c2833-141">Overload Resolution</span></span>](./overload-resolution.md)
