---
title: Introdução ao F# no Visual Studio
description: Saiba como usar F# o com o Visual Studio.
ms.date: 07/03/2018
ms.openlocfilehash: 80b4fc5b7631eace719832fe32003cad578ead27
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552830"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="903b6-103">Introdução ao F# no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="903b6-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="903b6-104">F#e as ferramentas F# visuais têm suporte no IDE do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="903b6-104">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>

<span data-ttu-id="903b6-105">Para começar, verifique se você tem o [Visual Studio instalado F#com ](install-fsharp.md#install-f-with-visual-studio)o.</span><span class="sxs-lookup"><span data-stu-id="903b6-105">To begin, ensure that you have [Visual Studio installed with F#](install-fsharp.md#install-f-with-visual-studio).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="903b6-106">Criando um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="903b6-106">Creating a console application</span></span>

<span data-ttu-id="903b6-107">Um dos projetos mais básicos do Visual Studio é o aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="903b6-107">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="903b6-108">Veja como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="903b6-108">Here's how to do it.</span></span>  <span data-ttu-id="903b6-109">Quando o Visual Studio estiver aberto:</span><span class="sxs-lookup"><span data-stu-id="903b6-109">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="903b6-110">No menu **arquivo** , aponte para **novo**e, em seguida, escolha **projeto**.</span><span class="sxs-lookup"><span data-stu-id="903b6-110">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2. <span data-ttu-id="903b6-111">Na caixa de diálogo novo projeto, em **modelos**, você deve **Ver F#Visual** .</span><span class="sxs-lookup"><span data-stu-id="903b6-111">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="903b6-112">Escolha esta seleção para mostrar F# os modelos.</span><span class="sxs-lookup"><span data-stu-id="903b6-112">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="903b6-113">Selecione o aplicativo de **console do .NET Core** ou o **aplicativo de console**.</span><span class="sxs-lookup"><span data-stu-id="903b6-113">Select either **.NET Core Console app** or **Console app**.</span></span>

4. <span data-ttu-id="903b6-114">Escolha o botão **OK** para criar o F# projeto!</span><span class="sxs-lookup"><span data-stu-id="903b6-114">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="903b6-115">Agora você deve ver um F# projeto no Gerenciador de soluções.</span><span class="sxs-lookup"><span data-stu-id="903b6-115">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="903b6-116">Escrevendo seu código</span><span class="sxs-lookup"><span data-stu-id="903b6-116">Writing your code</span></span>

<span data-ttu-id="903b6-117">Vamos começar escrevendo um pouco de código primeiro.</span><span class="sxs-lookup"><span data-stu-id="903b6-117">Let's get started by writing some code first.</span></span>  <span data-ttu-id="903b6-118">Verifique se o arquivo de `Program.fs` está aberto e, em seguida, substitua seu conteúdo pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="903b6-118">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="903b6-119">No exemplo de código anterior, uma função `square` foi definida, o que recebe uma entrada chamada `x` e a multiplica por si só.</span><span class="sxs-lookup"><span data-stu-id="903b6-119">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="903b6-120">Como F# o usa a [inferência de tipos](../language-reference/type-inference.md), o tipo de `x` não precisa ser especificado.</span><span class="sxs-lookup"><span data-stu-id="903b6-120">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="903b6-121">O F# compilador compreende os tipos em que a multiplicação é válida e atribuirá um tipo a `x` com base em como `square` é chamado.</span><span class="sxs-lookup"><span data-stu-id="903b6-121">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="903b6-122">Se você passar o mouse sobre `square`, verá o seguinte:</span><span class="sxs-lookup"><span data-stu-id="903b6-122">If you hover over `square`, you should see the following:</span></span>

```fsharp
val square: x:int -> int
```

<span data-ttu-id="903b6-123">Isso é o que é conhecido como assinatura do tipo da função.</span><span class="sxs-lookup"><span data-stu-id="903b6-123">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="903b6-124">Ele pode ser lido da seguinte maneira: "Square é uma função que recebe um inteiro chamado x e produz um inteiro".</span><span class="sxs-lookup"><span data-stu-id="903b6-124">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="903b6-125">Observe que o compilador define por hora o tipo do `square` como `int` – isso ocorre porque a multiplicação não é genérica em *todos os* tipos, mas sim em um conjunto fechado de tipos.</span><span class="sxs-lookup"><span data-stu-id="903b6-125">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="903b6-126">O compilador do F# escolheu `int` neste caso, mas ajustará a assinatura de tipo se você chamar `square` com um tipo de entrada diferente, como um `float`.</span><span class="sxs-lookup"><span data-stu-id="903b6-126">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="903b6-127">Outra função, `main`, é definida, que é decorada com o atributo `EntryPoint` para informar F# ao compilador que a execução do programa deve iniciar lá.</span><span class="sxs-lookup"><span data-stu-id="903b6-127">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="903b6-128">Ele segue a mesma convenção que outras [linguagens de programação em estilo C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), em que argumentos de linha de comando podem ser passados para essa função e um código inteiro é retornado (normalmente `0`).</span><span class="sxs-lookup"><span data-stu-id="903b6-128">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="903b6-129">É nessa função que chamamos a função `square` com um argumento de `12`.</span><span class="sxs-lookup"><span data-stu-id="903b6-129">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="903b6-130">Em F# seguida, o compilador atribui o tipo de `square` a ser `int -> int` (ou seja, uma função que usa um `int` e produz um `int`).</span><span class="sxs-lookup"><span data-stu-id="903b6-130">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="903b6-131">A chamada para `printfn` é uma função de impressão formatada que usa uma cadeia de caracteres de formato, semelhante a linguagens de programação em estilo C, parâmetros que correspondem àquelas especificadas na cadeia de caracteres de formato e, em seguida, imprime o resultado e uma nova linha.</span><span class="sxs-lookup"><span data-stu-id="903b6-131">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="903b6-132">Execução do código</span><span class="sxs-lookup"><span data-stu-id="903b6-132">Running your code</span></span>

<span data-ttu-id="903b6-133">Você pode executar o código e ver os resultados pressionando **Ctrl**+**F5**.</span><span class="sxs-lookup"><span data-stu-id="903b6-133">You can run the code and see results by pressing **Ctrl**+**F5**.</span></span>  <span data-ttu-id="903b6-134">Isso executa o programa sem depuração e permite que você veja os resultados.</span><span class="sxs-lookup"><span data-stu-id="903b6-134">This runs the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="903b6-135">Como alternativa, você pode escolher o item de menu de nível superior de **depuração** no Visual Studio e escolher **Iniciar sem depuração**.</span><span class="sxs-lookup"><span data-stu-id="903b6-135">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="903b6-136">Agora você deve ver o seguinte impresso na janela do console que o Visual Studio abriu:</span><span class="sxs-lookup"><span data-stu-id="903b6-136">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```console
12 squared is 144!
```

<span data-ttu-id="903b6-137">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="903b6-137">Congratulations!</span></span>  <span data-ttu-id="903b6-138">Você criou seu primeiro F# projeto no Visual Studio, escreveu uma F# função imprimiu os resultados da chamada dessa função e executou o projeto para ver alguns resultados.</span><span class="sxs-lookup"><span data-stu-id="903b6-138">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="903b6-139">{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="903b6-139">Next steps</span></span>

<span data-ttu-id="903b6-140">Se você ainda não fez isso, confira o [Tour do F# ](../tour.md), que abrange alguns dos principais recursos do F# idioma.</span><span class="sxs-lookup"><span data-stu-id="903b6-140">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="903b6-141">Ele fornecerá uma visão geral de alguns dos recursos do F#e fornecerá amplos exemplos de código que você pode copiar para o Visual Studio e executar.</span><span class="sxs-lookup"><span data-stu-id="903b6-141">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="903b6-142">Você também pode saber mais sobre a F# documentação na [ F# home page do docs](../index.yml).</span><span class="sxs-lookup"><span data-stu-id="903b6-142">You can also learn more about the F# documentation in the [F# docs homepage](../index.yml).</span></span>

## <a name="see-also"></a><span data-ttu-id="903b6-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="903b6-143">See also</span></span>

- [<span data-ttu-id="903b6-144">Tour do F#</span><span class="sxs-lookup"><span data-stu-id="903b6-144">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="903b6-145">F#referência de linguagem</span><span class="sxs-lookup"><span data-stu-id="903b6-145">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="903b6-146">Inferência de tipos</span><span class="sxs-lookup"><span data-stu-id="903b6-146">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="903b6-147">Referência de símbolo e operador</span><span class="sxs-lookup"><span data-stu-id="903b6-147">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
