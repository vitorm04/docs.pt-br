---
title: "Como: sobrecarregar um procedimento que recebe parâmetros opcionais (Visual Basic) | Documentos do Microsoft"
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
- procedure overloading, optional parameters
- procedures, defining
- Visual Basic code, procedures
- procedure parameters
- procedures, overloading
- procedures, multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
caps.latest.revision: 17
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
ms.openlocfilehash: f85fa957595f58c58d87f783baae71540eda07ba
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="50732-102">Como sobrecarregar um procedimento que usa parâmetros opcionais (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50732-102">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="50732-103">Se um procedimento possui um ou mais [opcional](../../../../visual-basic/language-reference/modifiers/optional.md) parâmetros, você não pode definir uma versão sobrecarregada coincidindo com qualquer uma de suas sobrecargas implícitas.</span><span class="sxs-lookup"><span data-stu-id="50732-103">If a procedure has one or more [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="50732-104">Para obter mais informações, consulte "Sobrecargas implícitas para parâmetros opcionais" em [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="50732-104">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="50732-105">Um parâmetro opcional</span><span class="sxs-lookup"><span data-stu-id="50732-105">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="50732-106">Para sobrecarregar um procedimento que recebe um parâmetro opcional</span><span class="sxs-lookup"><span data-stu-id="50732-106">To overload a procedure that takes one optional parameter</span></span>  
  
1.  <span data-ttu-id="50732-107">Escrever um `Sub` ou `Function` declaração que inclua o parâmetro opcional na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="50732-107">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="50732-108">Não use o `Optional` palavra-chave nesta versão sobrecarregada.</span><span class="sxs-lookup"><span data-stu-id="50732-108">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2.  <span data-ttu-id="50732-109">Preceder o `Sub` ou `Function` palavra-chave com o [sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="50732-109">Precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3.  <span data-ttu-id="50732-110">Escreva o código de procedimento que deve executar quando o código de chamada fornece o argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="50732-110">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4.  <span data-ttu-id="50732-111">Termine o procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="50732-111">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5.  <span data-ttu-id="50732-112">Escreva uma segunda declaração é idêntica à primeira, exceto que ele não inclui o parâmetro opcional na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="50732-112">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6.  <span data-ttu-id="50732-113">Escreva o código de procedimento deve ser executado quando o código de chamada não fornecer o argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="50732-113">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="50732-114">Termine o procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="50732-114">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="50732-115">O exemplo a seguir mostra um procedimento definido com um parâmetro opcional, um conjunto equivalente de dois procedimentos sobrecarregados e finalmente exemplos de versões sobrecarregadas válidos e inválidos.</span><span class="sxs-lookup"><span data-stu-id="50732-115">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     <span data-ttu-id="50732-116">[!code-vb[VbVbcnProcedures&#59;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="50732-116">[!code-vb[VbVbcnProcedures#59](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_1.vb)]</span></span>  
  
     <span data-ttu-id="50732-117">[!code-vb[VbVbcnProcedures&#60;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="50732-117">[!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_2.vb)]</span></span>  
  
     <span data-ttu-id="50732-118">[!code-vb[VbVbcnProcedures&#61;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="50732-118">[!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_3.vb)]</span></span>  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="50732-119">Vários parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="50732-119">Multiple Optional Parameters</span></span>  
 <span data-ttu-id="50732-120">Para um procedimento com mais de um parâmetro opcional, você normalmente precisa de mais de duas versões sobrecarregadas.</span><span class="sxs-lookup"><span data-stu-id="50732-120">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="50732-121">Por exemplo, se houver dois parâmetros opcionais, e o código de chamada pode fornecer ou omitir cada um deles independentemente uns dos outros, você precisa de quatro versões sobrecarregadas, uma para cada combinação possível de argumentos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="50732-121">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="50732-122">Como o número de parâmetros opcionais aumenta, aumenta a complexidade do sobrecarregamento.</span><span class="sxs-lookup"><span data-stu-id="50732-122">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="50732-123">A menos que algumas combinações de argumentos fornecidos não sejam aceitáveis, para parâmetros opcionais de N é necessário 2 ^ N versões sobrecarregadas.</span><span class="sxs-lookup"><span data-stu-id="50732-123">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="50732-124">Dependendo da natureza do procedimento, você pode achar que a clareza da lógica justifica o esforço extra de definir todas as versões sobrecarregadas.</span><span class="sxs-lookup"><span data-stu-id="50732-124">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="50732-125">Para sobrecarregar um procedimento que recebe mais de um parâmetro opcional</span><span class="sxs-lookup"><span data-stu-id="50732-125">To overload a procedure that takes more than one optional parameter</span></span>  
  
1.  <span data-ttu-id="50732-126">Determine quais combinações de argumentos opcionais fornecidos são aceitáveis à lógica do procedimento.</span><span class="sxs-lookup"><span data-stu-id="50732-126">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="50732-127">Uma combinação inaceitável pode surgir se um parâmetro opcional depende de outro.</span><span class="sxs-lookup"><span data-stu-id="50732-127">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="50732-128">Por exemplo, se um parâmetro aceita o nome do cônjuge e outro aceita a idade do cônjuge, uma combinação de argumentos fornecendo a idade mas omitindo o nome é inaceitável.</span><span class="sxs-lookup"><span data-stu-id="50732-128">For example, if one parameter accepts a spouse's name and another accepts the spouse's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2.  <span data-ttu-id="50732-129">Para cada combinação aceitável de argumentos opcionais fornecidos, escreva uma `Sub` ou `Function` declaração que define a lista de parâmetros correspondente.</span><span class="sxs-lookup"><span data-stu-id="50732-129">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="50732-130">Não use o `Optional` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="50732-130">Do not use the `Optional` keyword.</span></span>  
  
3.  <span data-ttu-id="50732-131">Em cada declaração, preceda o `Sub` ou `Function` palavra-chave com o [sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="50732-131">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4.  <span data-ttu-id="50732-132">Seguindo cada declaração, escreva o código de procedimento que deve ser executado quando o código de chamada fornece uma lista de argumentos correspondente à lista de parâmetros da declaração.</span><span class="sxs-lookup"><span data-stu-id="50732-132">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5.  <span data-ttu-id="50732-133">Termine cada procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="50732-133">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50732-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50732-134">See Also</span></span>  
 <span data-ttu-id="50732-135">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="50732-135">[Procedures](./index.md) </span></span>  
<span data-ttu-id="50732-136"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="50732-136"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="50732-137"> [Parâmetros opcionais](./optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="50732-137"> [Optional Parameters](./optional-parameters.md) </span></span>  
<span data-ttu-id="50732-138"> [Matrizes de parâmetros](./parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="50732-138"> [Parameter Arrays](./parameter-arrays.md) </span></span>  
<span data-ttu-id="50732-139"> [Sobrecarga de procedimento](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="50732-139"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="50732-140"> [Procedimentos de solução de problemas](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="50732-140"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="50732-141"> [Como: definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="50732-141"> [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md) </span></span>  
<span data-ttu-id="50732-142"> [Como: chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="50732-142"> [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md) </span></span>  
<span data-ttu-id="50732-143"> [Como: sobrecarregar um procedimento que recebe um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="50732-143"> [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span></span>  
<span data-ttu-id="50732-144"> [Resolução de Sobrecarga](./overload-resolution.md)</span><span class="sxs-lookup"><span data-stu-id="50732-144"> [Overload Resolution](./overload-resolution.md)</span></span>
