---
title: Passando argumentos por posição e nome (Visual Basic)
ms.date: 02/01/2018
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49e313b2d5aa8302ea4b99e643e09f7b43659785
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="1aa58-102">Passando argumentos por posição e nome (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1aa58-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>
<span data-ttu-id="1aa58-103">Quando você chama um `Sub` ou `Function` procedimento, você pode passar argumentos *por posição* — na ordem em que aparecem na definição do procedimento — ou você pode passá-los *por nome*, sem consideração à posição.</span><span class="sxs-lookup"><span data-stu-id="1aa58-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>  
  
 <span data-ttu-id="1aa58-104">Quando você passar um argumento por nome, especifique o argumento declarado do nome seguido por dois-pontos e um sinal de igual (`:=`), seguido pelo valor do argumento.</span><span class="sxs-lookup"><span data-stu-id="1aa58-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="1aa58-105">Você pode fornecer argumentos nomeados em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="1aa58-105">You can supply named arguments in any order.</span></span>  
  
 <span data-ttu-id="1aa58-106">Por exemplo, a seguinte `Sub` procedimento utiliza três argumentos:</span><span class="sxs-lookup"><span data-stu-id="1aa58-106">For example, the following `Sub` procedure takes three arguments:</span></span>  
  
 [!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]  
  
 <span data-ttu-id="1aa58-107">Quando você chamar esse procedimento, você pode fornecer os argumentos por posição, por nome ou usando uma combinação dos dois.</span><span class="sxs-lookup"><span data-stu-id="1aa58-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>  
  
## <a name="passing-arguments-by-position"></a><span data-ttu-id="1aa58-108">Passando argumentos por posição</span><span class="sxs-lookup"><span data-stu-id="1aa58-108">Passing Arguments by Position</span></span>  
 <span data-ttu-id="1aa58-109">Você pode chamar o `Display` método com os argumentos transmitidos por posição e delimitados por vírgulas, como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1aa58-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>  
  
[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)] 
  
 <span data-ttu-id="1aa58-110">Se você omitir um argumento opcional em uma lista de argumento posicional, você deve manter seu lugar com uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="1aa58-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="1aa58-111">A exemplo a seguir chama o `Display` método sem o `age` argumento:</span><span class="sxs-lookup"><span data-stu-id="1aa58-111">The following example calls the `Display` method without the `age` argument:</span></span>  
  
[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)] 
  
## <a name="passing-arguments-by-name"></a><span data-ttu-id="1aa58-112">Passando argumentos por nome</span><span class="sxs-lookup"><span data-stu-id="1aa58-112">Passing Arguments by Name</span></span>  
 <span data-ttu-id="1aa58-113">Como alternativa, você pode chamar `Display` com os argumentos passados pelo nome, também delimitado por vírgulas, como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1aa58-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>  
  
[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)] 

 <span data-ttu-id="1aa58-114">Passando argumentos por nome dessa maneira é especialmente útil quando você chama um procedimento que tem mais de um argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="1aa58-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="1aa58-115">Se você fornecer argumentos pelo nome, você não precisa usar vírgulas consecutivas para indicar argumentos posicionais ausentes.</span><span class="sxs-lookup"><span data-stu-id="1aa58-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="1aa58-116">Passando argumentos por nome também torna mais fácil controlar quais argumentos que você está passando e quais você está omitindo.</span><span class="sxs-lookup"><span data-stu-id="1aa58-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>  
  
## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="1aa58-117">Misturando argumentos por posição e nome</span><span class="sxs-lookup"><span data-stu-id="1aa58-117">Mixing Arguments by Position and by Name</span></span>  

<span data-ttu-id="1aa58-118">Você pode fornecer argumentos por posição e por nome em uma única chamada de procedimento, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1aa58-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>  
  
[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)] 
  
 <span data-ttu-id="1aa58-119">No exemplo anterior, é necessária para manter o lugar do omitido sem uma vírgula extra `age` argumento, pois `birth` é passado por nome.</span><span class="sxs-lookup"><span data-stu-id="1aa58-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>  
  
<span data-ttu-id="1aa58-120">Em versões do Visual Basic antes 15,5, quando você fornecer argumentos por uma mistura de posição e nome, os argumentos posicionais devem todos vir primeiro.</span><span class="sxs-lookup"><span data-stu-id="1aa58-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="1aa58-121">Depois que você fornecer um argumento pelo nome, argumentos restantes devem todas ser transmitidos por nome.</span><span class="sxs-lookup"><span data-stu-id="1aa58-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="1aa58-122">Por exemplo, a seguinte chamada para o `Display` método exibe o erro do compilador [BC30241: argumento esperado nomeado](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="1aa58-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)] 

<span data-ttu-id="1aa58-123">A partir do Visual Basic 15,5, argumentos posicionais podem seguir argumentos nomeados se os argumentos de posição finais estão na posição correta.</span><span class="sxs-lookup"><span data-stu-id="1aa58-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="1aa58-124">Se compilado no Visual Basic 15,5, a chamada anterior a `Display` método compilado com êxito e não gera erro do compilador [BC30241](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="1aa58-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>  

<span data-ttu-id="1aa58-125">Essa capacidade de misturar e combinar argumentos nomeados e posicionais em qualquer ordem é particularmente útil quando você quiser usar um argumento nomeado para tornar o código mais legível.</span><span class="sxs-lookup"><span data-stu-id="1aa58-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="1aa58-126">Por exemplo, a seguinte `Person` construtor de classe exige dois argumentos de tipo `Person`, que podem ser `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="1aa58-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span> 

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)] 

<span data-ttu-id="1aa58-127">Usando mistos argumentos nomeados e posicionais ajuda a tornar a intenção do código limpar quando o valor de `father` e `mother` argumentos é `Nothing`:</span><span class="sxs-lookup"><span data-stu-id="1aa58-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)] 

<span data-ttu-id="1aa58-128">Para seguir argumentos posicionais com argumentos nomeados, adicione o seguinte elemento ao seu projeto do Visual Basic (\*. vbproj) arquivo:</span><span class="sxs-lookup"><span data-stu-id="1aa58-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="1aa58-129">Restrições no fornecimento de argumentos por nome</span><span class="sxs-lookup"><span data-stu-id="1aa58-129">Restrictions on Supplying Arguments by Name</span></span>  

<span data-ttu-id="1aa58-130">Você não pode passar argumentos por nome para evitar digitar argumentos necessários.</span><span class="sxs-lookup"><span data-stu-id="1aa58-130">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="1aa58-131">Você pode omitir somente os argumentos opcionais.</span><span class="sxs-lookup"><span data-stu-id="1aa58-131">You can omit only the optional arguments.</span></span>  
  
<span data-ttu-id="1aa58-132">Você não pode passar uma matriz de parâmetros por nome.</span><span class="sxs-lookup"><span data-stu-id="1aa58-132">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="1aa58-133">Isso ocorre porque quando você chamar o procedimento, você fornece um número indefinido de argumentos separados por vírgula para a matriz de parâmetros, e o compilador não é possível associar mais de um argumento com um único nome.</span><span class="sxs-lookup"><span data-stu-id="1aa58-133">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aa58-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1aa58-134">See Also</span></span>  
 [<span data-ttu-id="1aa58-135">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="1aa58-135">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="1aa58-136">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="1aa58-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="1aa58-137">Como passar argumentos para um procedimento</span><span class="sxs-lookup"><span data-stu-id="1aa58-137">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="1aa58-138">Passando Argumentos por Valor e por Referência</span><span class="sxs-lookup"><span data-stu-id="1aa58-138">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="1aa58-139">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="1aa58-139">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="1aa58-140">Matrizes de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1aa58-140">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="1aa58-141">Opcional</span><span class="sxs-lookup"><span data-stu-id="1aa58-141">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [<span data-ttu-id="1aa58-142">ParamArray</span><span class="sxs-lookup"><span data-stu-id="1aa58-142">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
