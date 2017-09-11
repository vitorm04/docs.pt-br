---
title: "Passando argumentos por posição e nome (Visual Basic) | Documentos do Microsoft"
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
- arguments [Visual Basic], passing by name
- procedures, arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments, passing arguments
- arguments [Visual Basic], passing by position
- Function procedures, passing arguments
- named parameters, passing arguments
- named arguments
- passing parameters, named parameter arguments
- passing parameters, by position
- procedures, calling
- named parameters
- Sub procedures, passing arguments
- argument passing
- passing parameters, by name
- argument passing, by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
caps.latest.revision: 13
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
ms.openlocfilehash: c1ada26386376cb38c4b128911a2e2e1f38ade42
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="a1620-102">Passando argumentos por posição e nome (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1620-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>
<span data-ttu-id="a1620-103">Quando você chama um `Sub` ou `Function` procedimento, você pode passar argumentos *por posição* — na ordem em que aparecem na definição do procedimento — ou você pode passá-los *por nome*, independentemente da posição.</span><span class="sxs-lookup"><span data-stu-id="a1620-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>  
  
 <span data-ttu-id="a1620-104">Quando você passa um argumento pelo nome, especifique o argumento declarado do nome seguido por dois-pontos e um sinal de igual (`:=`), seguido pelo valor do argumento.</span><span class="sxs-lookup"><span data-stu-id="a1620-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="a1620-105">Você pode fornecer argumentos nomeados em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="a1620-105">You can supply named arguments in any order.</span></span>  
  
 <span data-ttu-id="a1620-106">Por exemplo, a seguinte `Sub` procedimento utiliza três argumentos:</span><span class="sxs-lookup"><span data-stu-id="a1620-106">For example, the following `Sub` procedure takes three arguments:</span></span>  
  
 <span data-ttu-id="a1620-107">[!code-vb[41 VbVbcnProcedures](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a1620-107">[!code-vb[VbVbcnProcedures#41](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_1.vb)]</span></span>  
  
 <span data-ttu-id="a1620-108">Quando você chamar esse procedimento, você pode fornecer os argumentos por posição, por nome ou usando uma mistura de ambos.</span><span class="sxs-lookup"><span data-stu-id="a1620-108">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>  
  
## <a name="passing-arguments-by-position"></a><span data-ttu-id="a1620-109">Passando argumentos por posição</span><span class="sxs-lookup"><span data-stu-id="a1620-109">Passing Arguments by Position</span></span>  
 <span data-ttu-id="a1620-110">Você pode chamar o procedimento `studentInfo` com seus argumentos passados por posição e delimitados por vírgulas, como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="a1620-110">You can call the procedure `studentInfo` with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>  
  
 <span data-ttu-id="a1620-111">[!code-vb[VbVbcnProcedures&42;](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="a1620-111">[!code-vb[VbVbcnProcedures#42](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_2.vb)]</span></span>  
  
 <span data-ttu-id="a1620-112">Se você omitir um argumento opcional em uma lista de argumentos posicionais, você deve manter seu lugar com uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="a1620-112">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="a1620-113">A exemplo a seguir chama `studentInfo` sem o `age` argumento:</span><span class="sxs-lookup"><span data-stu-id="a1620-113">The following example calls `studentInfo` without the `age` argument:</span></span>  
  
 <span data-ttu-id="a1620-114">[!code-vb[VbVbcnProcedures&#43;](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="a1620-114">[!code-vb[VbVbcnProcedures#43](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_3.vb)]</span></span>  
  
## <a name="passing-arguments-by-name"></a><span data-ttu-id="a1620-115">Passando argumentos por nome</span><span class="sxs-lookup"><span data-stu-id="a1620-115">Passing Arguments by Name</span></span>  
 <span data-ttu-id="a1620-116">Como alternativa, você pode chamar `studentInfo` com os argumentos passados pelo nome, também delimitado por vírgulas, como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="a1620-116">Alternatively, you can call `studentInfo` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>  
  
 <span data-ttu-id="a1620-117">[!code-vb[VbVbcnProcedures&#44;](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="a1620-117">[!code-vb[VbVbcnProcedures#44](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_4.vb)]</span></span>  
  
## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="a1620-118">Misturando argumentos por posição e nome</span><span class="sxs-lookup"><span data-stu-id="a1620-118">Mixing Arguments by Position and by Name</span></span>  
 <span data-ttu-id="a1620-119">Você pode fornecer argumentos por posição e por nome em uma única chamada de procedimento, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="a1620-119">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>  
  
 <span data-ttu-id="a1620-120">[!code-vb[45 VbVbcnProcedures](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="a1620-120">[!code-vb[VbVbcnProcedures#45](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_5.vb)]</span></span>  
  
 <span data-ttu-id="a1620-121">No exemplo anterior, nenhuma vírgula extra é necessária para manter o lugar do omitido `age` argumento, uma vez que `birth` é passado por nome.</span><span class="sxs-lookup"><span data-stu-id="a1620-121">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>  
  
 <span data-ttu-id="a1620-122">Quando você fornecer argumentos por uma mistura de posição e nome, os argumentos posicionais devem todos vir primeiro.</span><span class="sxs-lookup"><span data-stu-id="a1620-122">When you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="a1620-123">Depois que você fornecer um argumento pelo nome, os argumentos restantes devem ser todos por nome.</span><span class="sxs-lookup"><span data-stu-id="a1620-123">Once you supply an argument by name, the remaining arguments must all be by name.</span></span>  
  
## <a name="supplying-optional-arguments-by-name"></a><span data-ttu-id="a1620-124">Fornecendo argumentos opcionais por nome</span><span class="sxs-lookup"><span data-stu-id="a1620-124">Supplying Optional Arguments by Name</span></span>  
 <span data-ttu-id="a1620-125">Passando argumentos por nome é especialmente útil quando você chama um procedimento que tem mais de um argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="a1620-125">Passing arguments by name is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="a1620-126">Se você fornecer argumentos pelo nome, você não precisa usar vírgulas consecutivas para indicar argumentos posicionais ausentes.</span><span class="sxs-lookup"><span data-stu-id="a1620-126">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="a1620-127">Passando argumentos por nome também facilita manter controle de quais argumentos você está passando e quais você está omitindo.</span><span class="sxs-lookup"><span data-stu-id="a1620-127">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>  
  
## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="a1620-128">Restrições no fornecimento de argumentos por nome</span><span class="sxs-lookup"><span data-stu-id="a1620-128">Restrictions on Supplying Arguments by Name</span></span>  
 <span data-ttu-id="a1620-129">Você não pode passar argumentos pelo nome para evitar digitar argumentos necessários.</span><span class="sxs-lookup"><span data-stu-id="a1620-129">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="a1620-130">Você pode omitir somente os argumentos opcionais.</span><span class="sxs-lookup"><span data-stu-id="a1620-130">You can omit only the optional arguments.</span></span>  
  
 <span data-ttu-id="a1620-131">Você não pode passar uma matriz de parâmetros por nome.</span><span class="sxs-lookup"><span data-stu-id="a1620-131">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="a1620-132">Isso ocorre porque quando você chama o procedimento, você fornece um número indefinido de argumentos separados por vírgula para a matriz de parâmetros e o compilador não pode associar mais de um argumento com um único nome.</span><span class="sxs-lookup"><span data-stu-id="a1620-132">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1620-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1620-133">See Also</span></span>  
 <span data-ttu-id="a1620-134">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="a1620-134">[Procedures](./index.md) </span></span>  
<span data-ttu-id="a1620-135"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="a1620-135"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="a1620-136"> [Como: passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="a1620-136"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="a1620-137"> [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a1620-137"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="a1620-138"> [Parâmetros opcionais](./optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="a1620-138"> [Optional Parameters](./optional-parameters.md) </span></span>  
<span data-ttu-id="a1620-139"> [Matrizes de parâmetros](./parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="a1620-139"> [Parameter Arrays](./parameter-arrays.md) </span></span>  
<span data-ttu-id="a1620-140"> [Opcional](../../../../visual-basic/language-reference/modifiers/optional.md) </span><span class="sxs-lookup"><span data-stu-id="a1620-140"> [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) </span></span>  
<span data-ttu-id="a1620-141"> [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)</span><span class="sxs-lookup"><span data-stu-id="a1620-141"> [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)</span></span>
