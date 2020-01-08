---
title: Introdução ao F# no Visual Studio
description: Saiba como usar F# o com o Visual Studio.
ms.date: 12/20/2019
ms.openlocfilehash: 9bf47fb08ea3df0aa0d5064043d94f030d45d568
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337345"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="5c5cd-103">Introdução ao F# no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5c5cd-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="5c5cd-104">F#e as ferramentas F# visuais têm suporte no IDE (ambiente de desenvolvimento integrado) do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-104">F# and the Visual F# tooling are supported in the Visual Studio integrated development environment (IDE).</span></span>

<span data-ttu-id="5c5cd-105">Para começar, verifique se você tem o [Visual Studio instalado F# com suporte](install-fsharp.md#install-f-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="5c5cd-105">To begin, ensure that you have [Visual Studio installed with F# support](install-fsharp.md#install-f-with-visual-studio).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="5c5cd-106">Criar um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="5c5cd-106">Create a console application</span></span>

<span data-ttu-id="5c5cd-107">Um dos projetos mais básicos do Visual Studio é o aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-107">One of the most basic projects in Visual Studio is the console app.</span></span> <span data-ttu-id="5c5cd-108">Veja como criar um:</span><span class="sxs-lookup"><span data-stu-id="5c5cd-108">Here's how to create one:</span></span>

1. <span data-ttu-id="5c5cd-109">Abra o Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-109">Open Visual Studio 2019.</span></span>

2. <span data-ttu-id="5c5cd-110">Na tela Iniciar, selecione **Criar um novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-110">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="5c5cd-111">Na página **criar um novo projeto** , escolha **F#** na lista idioma.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-111">On the **Create a new project** page, choose **F#** from the Language list.</span></span>

4. <span data-ttu-id="5c5cd-112">Escolha o modelo **aplicativo de console (.NET Core)** e, em seguida, escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-112">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

5. <span data-ttu-id="5c5cd-113">Na página **configurar seu novo projeto** , insira um nome na caixa **nome do projeto** .</span><span class="sxs-lookup"><span data-stu-id="5c5cd-113">On the **Configure your new project** page, enter a name in the **Project name** box.</span></span> <span data-ttu-id="5c5cd-114">Em seguida, escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-114">Then, choose **Create**.</span></span>

   <span data-ttu-id="5c5cd-115">O Visual Studio cria o F# novo projeto.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-115">Visual Studio creates the new F# project.</span></span> <span data-ttu-id="5c5cd-116">Você pode vê-lo na janela de Gerenciador de Soluções.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-116">You can see it in the Solution Explorer window.</span></span>

## <a name="write-the-code"></a><span data-ttu-id="5c5cd-117">Escreva o código</span><span class="sxs-lookup"><span data-stu-id="5c5cd-117">Write the code</span></span>

<span data-ttu-id="5c5cd-118">Vamos começar escrevendo um pouco de código.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-118">Let's get started by writing some code.</span></span> <span data-ttu-id="5c5cd-119">Verifique se o arquivo `Program.fs` está aberto e, em seguida, substitua seu conteúdo pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="5c5cd-119">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="5c5cd-120">O exemplo de código anterior define uma função chamada `square` que usa uma entrada chamada `x` e a multiplica por si só.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-120">The previous code sample defines a function called `square` that takes an input named `x` and multiplies it by itself.</span></span> <span data-ttu-id="5c5cd-121">Como F# o usa a [inferência de tipos](../language-reference/type-inference.md), o tipo de `x` não precisa ser especificado.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-121">Because F# uses [Type inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span> <span data-ttu-id="5c5cd-122">O F# compilador compreende os tipos em que a multiplicação é válida e atribui um tipo a `x` com base em como `square` é chamado.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-122">The F# compiler understands the types where multiplication is valid and assigns a type to `x` based on how `square` is called.</span></span> <span data-ttu-id="5c5cd-123">Se você passar o mouse por cima de `square`, verá o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5c5cd-123">If you hover over `square`, you should see the following:</span></span>

```fsharp
val square: x:int -> int
```

<span data-ttu-id="5c5cd-124">Isso é o que é conhecido como assinatura do tipo da função.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-124">This is what is known as the function's type signature.</span></span> <span data-ttu-id="5c5cd-125">Ele pode ser lido da seguinte maneira: "Square é uma função que usa um inteiro chamado x e produz um inteiro".</span><span class="sxs-lookup"><span data-stu-id="5c5cd-125">It can be read like this: "Square is a function that takes an integer named x and produces an integer".</span></span> <span data-ttu-id="5c5cd-126">O compilador ofereceu `square` o tipo de `int` por enquanto; Isso ocorre porque a multiplicação não é genérica em *todos os* tipos, mas sim um conjunto fechado de tipos.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-126">The compiler gave `square` the `int` type for now; this is because multiplication is not generic across *all* types but rather a closed set of types.</span></span> <span data-ttu-id="5c5cd-127">O F# compilador ajustará a assinatura de tipo se você chamar `square` com um tipo de entrada diferente, como um `float`.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-127">The F# compiler will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="5c5cd-128">Outra função, `main`, é definida, que é decorada com o atributo `EntryPoint`.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-128">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute.</span></span> <span data-ttu-id="5c5cd-129">Esse atributo informa ao F# compilador que a execução do programa deve iniciar lá.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-129">This attribute tells the F# compiler that program execution should start there.</span></span> <span data-ttu-id="5c5cd-130">Ele segue a mesma convenção que outras [linguagens de programação em estilo C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), em que argumentos de linha de comando podem ser passados para essa função e um código inteiro é retornado (normalmente `0`).</span><span class="sxs-lookup"><span data-stu-id="5c5cd-130">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="5c5cd-131">Ele está na função de ponto de entrada, `main`, que você chama a função `square` com um argumento de `12`.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-131">It is in the entry point function, `main`, that you call the `square` function with an argument of `12`.</span></span> <span data-ttu-id="5c5cd-132">Em F# seguida, o compilador atribui o tipo de `square` a ser `int -> int` (ou seja, uma função que usa um `int` e produz um `int`).</span><span class="sxs-lookup"><span data-stu-id="5c5cd-132">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function that takes an `int` and produces an `int`).</span></span> <span data-ttu-id="5c5cd-133">A chamada para `printfn` é uma função de impressão formatada que usa uma cadeia de caracteres de formato e imprime o resultado (e uma nova linha).</span><span class="sxs-lookup"><span data-stu-id="5c5cd-133">The call to `printfn` is a formatted printing function that uses a format string and prints the result (and a new line).</span></span> <span data-ttu-id="5c5cd-134">A cadeia de caracteres de formato, semelhante às linguagens de programação em estilo C, tem parâmetros (`%d`) que correspondem aos argumentos que são passados para ele, nesse caso, `12` e `(square 12)`.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-134">The format string, similar to C-style programming languages, has parameters (`%d`) that correspond to the arguments that are passed to it, in this case, `12` and `(square 12)`.</span></span>

## <a name="run-the-code"></a><span data-ttu-id="5c5cd-135">Executar o código</span><span class="sxs-lookup"><span data-stu-id="5c5cd-135">Run the code</span></span>

<span data-ttu-id="5c5cd-136">Você pode executar o código e ver os resultados pressionando **Ctrl**+**F5**.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-136">You can run the code and see the results by pressing **Ctrl**+**F5**.</span></span> <span data-ttu-id="5c5cd-137">Como alternativa, você pode escolher a > de **depuração** **Iniciar sem depuração** na barra de menus de nível superior.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-137">Alternatively, you can choose the **Debug** > **Start Without Debugging** from the top-level menu bar.</span></span> <span data-ttu-id="5c5cd-138">Isso executa o programa sem depuração.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-138">This runs the program without debugging.</span></span>

<span data-ttu-id="5c5cd-139">A saída a seguir é impressa na janela do console aberta pelo Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="5c5cd-139">The following output prints to the console window that Visual Studio opened:</span></span>

```console
12 squared is: 144!
```

<span data-ttu-id="5c5cd-140">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="5c5cd-140">Congratulations!</span></span> <span data-ttu-id="5c5cd-141">Você criou seu primeiro F# projeto no Visual Studio, escreveu uma F# função que calcula e imprime um valor e executa o projeto para ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-141">You've created your first F# project in Visual Studio, written an F# function that calculates and prints a value, and run the project to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5c5cd-142">{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="5c5cd-142">Next steps</span></span>

<span data-ttu-id="5c5cd-143">Se você ainda não fez isso, confira o [Tour do F# ](../tour.md), que abrange alguns dos principais recursos da linguagem F#.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-143">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span> <span data-ttu-id="5c5cd-144">Ele fornece uma visão geral de alguns dos recursos do F# e exemplos de código abrangentes que você pode copiar para o Visual Studio e executar.</span><span class="sxs-lookup"><span data-stu-id="5c5cd-144">It provides an overview of some of the capabilities of F# and ample code samples that you can copy into Visual Studio and run.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5c5cd-145">Tour do F#</span><span class="sxs-lookup"><span data-stu-id="5c5cd-145">Tour of F#</span></span>](../tour.md)

## <a name="see-also"></a><span data-ttu-id="5c5cd-146">Veja também</span><span class="sxs-lookup"><span data-stu-id="5c5cd-146">See also</span></span>

- [<span data-ttu-id="5c5cd-147">F#referência de linguagem</span><span class="sxs-lookup"><span data-stu-id="5c5cd-147">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="5c5cd-148">Inferência de tipos</span><span class="sxs-lookup"><span data-stu-id="5c5cd-148">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="5c5cd-149">Referência de símbolo e operador</span><span class="sxs-lookup"><span data-stu-id="5c5cd-149">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
