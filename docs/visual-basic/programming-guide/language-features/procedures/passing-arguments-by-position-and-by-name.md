---
title: "Passando argumentos por posição e nome (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 164f69fcf23049441a0acbe05058c792d5363a03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="47251-102">Passando argumentos por posição e nome (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47251-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>
<span data-ttu-id="47251-103">Quando você chama um `Sub` ou `Function` procedimento, você pode passar argumentos *por posição* — na ordem em que aparecem na definição do procedimento — ou você pode passá-los *por nome*, sem consideração à posição.</span><span class="sxs-lookup"><span data-stu-id="47251-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>  
  
 <span data-ttu-id="47251-104">Quando você passar um argumento por nome, especifique o argumento declarado do nome seguido por dois-pontos e um sinal de igual (`:=`), seguido pelo valor do argumento.</span><span class="sxs-lookup"><span data-stu-id="47251-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="47251-105">Você pode fornecer argumentos nomeados em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="47251-105">You can supply named arguments in any order.</span></span>  
  
 <span data-ttu-id="47251-106">Por exemplo, a seguinte `Sub` procedimento utiliza três argumentos:</span><span class="sxs-lookup"><span data-stu-id="47251-106">For example, the following `Sub` procedure takes three arguments:</span></span>  
  
 [!code-vb[VbVbcnProcedures#41](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_1.vb)]  
  
 <span data-ttu-id="47251-107">Quando você chamar esse procedimento, você pode fornecer os argumentos por posição, por nome ou usando uma combinação dos dois.</span><span class="sxs-lookup"><span data-stu-id="47251-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>  
  
## <a name="passing-arguments-by-position"></a><span data-ttu-id="47251-108">Passando argumentos por posição</span><span class="sxs-lookup"><span data-stu-id="47251-108">Passing Arguments by Position</span></span>  
 <span data-ttu-id="47251-109">Você pode chamar o procedimento `studentInfo` com os argumentos transmitidos por posição e delimitados por vírgulas, como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="47251-109">You can call the procedure `studentInfo` with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#42](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_2.vb)]  
  
 <span data-ttu-id="47251-110">Se você omitir um argumento opcional em uma lista de argumento posicional, você deve manter seu lugar com uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="47251-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="47251-111">A exemplo a seguir chama `studentInfo` sem o `age` argumento:</span><span class="sxs-lookup"><span data-stu-id="47251-111">The following example calls `studentInfo` without the `age` argument:</span></span>  
  
 [!code-vb[VbVbcnProcedures#43](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_3.vb)]  
  
## <a name="passing-arguments-by-name"></a><span data-ttu-id="47251-112">Passando argumentos por nome</span><span class="sxs-lookup"><span data-stu-id="47251-112">Passing Arguments by Name</span></span>  
 <span data-ttu-id="47251-113">Como alternativa, você pode chamar `studentInfo` com os argumentos passados pelo nome, também delimitado por vírgulas, como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="47251-113">Alternatively, you can call `studentInfo` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#44](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_4.vb)]  
  
## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="47251-114">Misturando argumentos por posição e nome</span><span class="sxs-lookup"><span data-stu-id="47251-114">Mixing Arguments by Position and by Name</span></span>  
 <span data-ttu-id="47251-115">Você pode fornecer argumentos por posição e por nome em uma única chamada de procedimento, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="47251-115">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#45](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_5.vb)]  
  
 <span data-ttu-id="47251-116">No exemplo anterior, é necessária para manter o lugar do omitido sem uma vírgula extra `age` argumento, pois `birth` é passado por nome.</span><span class="sxs-lookup"><span data-stu-id="47251-116">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>  
  
 <span data-ttu-id="47251-117">Quando você fornecer argumentos por uma mistura de posição e nome, os argumentos posicionais devem todos vir primeiro.</span><span class="sxs-lookup"><span data-stu-id="47251-117">When you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="47251-118">Depois que você fornecer um argumento pelo nome, os argumentos restantes devem ser por nome.</span><span class="sxs-lookup"><span data-stu-id="47251-118">Once you supply an argument by name, the remaining arguments must all be by name.</span></span>  
  
## <a name="supplying-optional-arguments-by-name"></a><span data-ttu-id="47251-119">Fornecendo argumentos opcionais por nome</span><span class="sxs-lookup"><span data-stu-id="47251-119">Supplying Optional Arguments by Name</span></span>  
 <span data-ttu-id="47251-120">Passando argumentos por nome é especialmente útil quando você chama um procedimento que tem mais de um argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="47251-120">Passing arguments by name is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="47251-121">Se você fornecer argumentos pelo nome, você não precisa usar vírgulas consecutivas para indicar argumentos posicionais ausentes.</span><span class="sxs-lookup"><span data-stu-id="47251-121">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="47251-122">Passando argumentos por nome também torna mais fácil controlar quais argumentos que você está passando e quais você está omitindo.</span><span class="sxs-lookup"><span data-stu-id="47251-122">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>  
  
## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="47251-123">Restrições no fornecimento de argumentos por nome</span><span class="sxs-lookup"><span data-stu-id="47251-123">Restrictions on Supplying Arguments by Name</span></span>  
 <span data-ttu-id="47251-124">Você não pode passar argumentos por nome para evitar digitar argumentos necessários.</span><span class="sxs-lookup"><span data-stu-id="47251-124">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="47251-125">Você pode omitir somente os argumentos opcionais.</span><span class="sxs-lookup"><span data-stu-id="47251-125">You can omit only the optional arguments.</span></span>  
  
 <span data-ttu-id="47251-126">Você não pode passar uma matriz de parâmetros por nome.</span><span class="sxs-lookup"><span data-stu-id="47251-126">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="47251-127">Isso ocorre porque quando você chamar o procedimento, você fornece um número indefinido de argumentos separados por vírgula para a matriz de parâmetros, e o compilador não é possível associar mais de um argumento com um único nome.</span><span class="sxs-lookup"><span data-stu-id="47251-127">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47251-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47251-128">See Also</span></span>  
 [<span data-ttu-id="47251-129">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="47251-129">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="47251-130">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="47251-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="47251-131">Como passar argumentos para um procedimento</span><span class="sxs-lookup"><span data-stu-id="47251-131">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="47251-132">Passando Argumentos por Valor e por Referência</span><span class="sxs-lookup"><span data-stu-id="47251-132">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="47251-133">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="47251-133">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="47251-134">Matrizes de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="47251-134">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="47251-135">Opcional</span><span class="sxs-lookup"><span data-stu-id="47251-135">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [<span data-ttu-id="47251-136">ParamArray</span><span class="sxs-lookup"><span data-stu-id="47251-136">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
