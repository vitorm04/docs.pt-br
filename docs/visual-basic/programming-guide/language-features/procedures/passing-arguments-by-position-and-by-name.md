---
title: Passando argumentos por posição e nome
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
ms.openlocfilehash: b6588335f7634cc87a9fc14cbfc4ba80baad1abb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400851"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="2f25f-102">Passando argumentos por posição e nome (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f25f-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>

<span data-ttu-id="2f25f-103">Quando você `Sub` chama `Function` um ou procedimento, você pode passar argumentos *por posição* - na ordem em que eles aparecem na definição do procedimento - ou você pode passá-los *pelo nome*, sem considerar a posição.</span><span class="sxs-lookup"><span data-stu-id="2f25f-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>

<span data-ttu-id="2f25f-104">Quando você passa um argumento por nome, você especifica o nome declarado do`:=`argumento seguido por um cólon e um sinal igual ( ), seguido pelo valor do argumento.</span><span class="sxs-lookup"><span data-stu-id="2f25f-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="2f25f-105">Você pode fornecer argumentos nomeados em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="2f25f-105">You can supply named arguments in any order.</span></span>

<span data-ttu-id="2f25f-106">Por exemplo, `Sub` o procedimento a seguir requer três argumentos:</span><span class="sxs-lookup"><span data-stu-id="2f25f-106">For example, the following `Sub` procedure takes three arguments:</span></span>

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

<span data-ttu-id="2f25f-107">Quando você chama este procedimento, você pode fornecer os argumentos por posição, por nome ou usando uma mistura de ambos.</span><span class="sxs-lookup"><span data-stu-id="2f25f-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>

## <a name="passing-arguments-by-position"></a><span data-ttu-id="2f25f-108">Passando argumentos por posição</span><span class="sxs-lookup"><span data-stu-id="2f25f-108">Passing Arguments by Position</span></span>

<span data-ttu-id="2f25f-109">Você pode `Display` chamar o método com seus argumentos passados por posição e delimitados por vírgulas, como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2f25f-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

<span data-ttu-id="2f25f-110">Se você omitir um argumento opcional em uma lista de argumentos posicionais, você deve manter seu lugar com uma vírgula.</span><span class="sxs-lookup"><span data-stu-id="2f25f-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="2f25f-111">O exemplo a `Display` seguir `age` chama o método sem o argumento:</span><span class="sxs-lookup"><span data-stu-id="2f25f-111">The following example calls the `Display` method without the `age` argument:</span></span>

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a><span data-ttu-id="2f25f-112">Passando argumentos por nome</span><span class="sxs-lookup"><span data-stu-id="2f25f-112">Passing Arguments by Name</span></span>

<span data-ttu-id="2f25f-113">Alternativamente, você `Display` pode chamar com os argumentos passados pelo nome, também delimitados por vírgulas, como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2f25f-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

<span data-ttu-id="2f25f-114">Passar argumentos por nome dessa forma é especialmente útil quando você chama um procedimento que tem mais de um argumento opcional.</span><span class="sxs-lookup"><span data-stu-id="2f25f-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="2f25f-115">Se você fornecer argumentos por nome, você não precisa usar vírgulas consecutivas para denotar argumentos posicionais ausentes.</span><span class="sxs-lookup"><span data-stu-id="2f25f-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="2f25f-116">Passar argumentos pelo nome também torna mais fácil acompanhar quais argumentos você está passando e quais você está omitindo.</span><span class="sxs-lookup"><span data-stu-id="2f25f-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>

## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="2f25f-117">Misturando Argumentos por Posição e por Nome</span><span class="sxs-lookup"><span data-stu-id="2f25f-117">Mixing Arguments by Position and by Name</span></span>

<span data-ttu-id="2f25f-118">Você pode fornecer argumentos tanto por posição quanto por nome em uma única chamada de procedimento, como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2f25f-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

<span data-ttu-id="2f25f-119">No exemplo anterior, nenhuma comma extra é necessária para `age` manter `birth` o lugar do argumento omitido, uma vez que é passado pelo nome.</span><span class="sxs-lookup"><span data-stu-id="2f25f-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>

<span data-ttu-id="2f25f-120">Nas versões do Visual Basic antes de 15.5, quando você fornece argumentos por uma mistura de posição e nome, os argumentos posicionais devem vir primeiro.</span><span class="sxs-lookup"><span data-stu-id="2f25f-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="2f25f-121">Uma vez que você forneça um argumento por nome, todos os argumentos restantes devem ser todos passados pelo nome.</span><span class="sxs-lookup"><span data-stu-id="2f25f-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="2f25f-122">Por exemplo, a seguinte `Display` chamada para o método exibe erro do compilador [BC30241: Argumento nomeado esperado](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="2f25f-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

<span data-ttu-id="2f25f-123">A partir do Visual Basic 15.5, os argumentos posicionais podem seguir argumentos nomeados se os argumentos posicionais finais estiverem na posição correta.</span><span class="sxs-lookup"><span data-stu-id="2f25f-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="2f25f-124">Se compilado em Visual Basic 15.5, `Display` a chamada anterior para o método compila com sucesso e não gera mais erro do compilador [BC30241](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="2f25f-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>

<span data-ttu-id="2f25f-125">Essa capacidade de misturar e combinar argumentos nomeados e posicionais em qualquer ordem é particularmente útil quando você deseja usar um argumento nomeado para tornar seu código mais legível.</span><span class="sxs-lookup"><span data-stu-id="2f25f-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="2f25f-126">Por exemplo, `Person` o construtor de classe a `Person`seguir requer dois `Nothing`argumentos do tipo , ambos podem ser .</span><span class="sxs-lookup"><span data-stu-id="2f25f-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

<span data-ttu-id="2f25f-127">O uso de argumentos mistos e posicionais ajuda a tornar `father` `mother` clara a `Nothing`intenção do código quando o valor dos argumentos e argumentos é:</span><span class="sxs-lookup"><span data-stu-id="2f25f-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

<span data-ttu-id="2f25f-128">Para seguir argumentos posicionais com argumentos nomeados, você deve\*adicionar o seguinte elemento ao seu arquivo Visual Basic (.vbproj):</span><span class="sxs-lookup"><span data-stu-id="2f25f-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="2f25f-129">Para obter mais informações, [consulte a configuração da versão visual básica](../../../language-reference/configure-language-version.md)do idioma .</span><span class="sxs-lookup"><span data-stu-id="2f25f-129">For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="2f25f-130">Restrições ao fornecimento de argumentos por nome</span><span class="sxs-lookup"><span data-stu-id="2f25f-130">Restrictions on Supplying Arguments by Name</span></span>

<span data-ttu-id="2f25f-131">Você não pode passar argumentos por nome para evitar inserir argumentos necessários.</span><span class="sxs-lookup"><span data-stu-id="2f25f-131">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="2f25f-132">Você pode omiti-lo apenas os argumentos opcionais.</span><span class="sxs-lookup"><span data-stu-id="2f25f-132">You can omit only the optional arguments.</span></span>

<span data-ttu-id="2f25f-133">Você não pode passar uma matriz de parâmetros pelo nome.</span><span class="sxs-lookup"><span data-stu-id="2f25f-133">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="2f25f-134">Isso porque quando você chama o procedimento, você fornece um número indefinido de argumentos separados por comma para a matriz de parâmetros, e o compilador não pode associar mais de um argumento com um único nome.</span><span class="sxs-lookup"><span data-stu-id="2f25f-134">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f25f-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="2f25f-135">See also</span></span>

- [<span data-ttu-id="2f25f-136">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="2f25f-136">Procedures</span></span>](./index.md)
- [<span data-ttu-id="2f25f-137">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="2f25f-137">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="2f25f-138">Como passar argumentos para um procedimento</span><span class="sxs-lookup"><span data-stu-id="2f25f-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="2f25f-139">Passar argumentos por valor e por referência</span><span class="sxs-lookup"><span data-stu-id="2f25f-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="2f25f-140">Parâmetros opcionais</span><span class="sxs-lookup"><span data-stu-id="2f25f-140">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="2f25f-141">Matrizes de parâmetros</span><span class="sxs-lookup"><span data-stu-id="2f25f-141">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="2f25f-142">Opcional</span><span class="sxs-lookup"><span data-stu-id="2f25f-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
- [<span data-ttu-id="2f25f-143">ParamArray</span><span class="sxs-lookup"><span data-stu-id="2f25f-143">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
