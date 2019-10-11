---
title: Introdução ao F# no Visual Studio
description: Saiba como usar F# o com o Visual Studio.
ms.date: 07/03/2018
ms.openlocfilehash: e573af67a1fc00b0a340f8c73ab1ee0ed2b97810
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082694"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="58afc-103">Introdução ao F# no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="58afc-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="58afc-104">O IDE do Visual Studio tem suporte ao F# e às ferramentas do Visual F#.</span><span class="sxs-lookup"><span data-stu-id="58afc-104">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>

<span data-ttu-id="58afc-105">Para começar, verifique se você tem o [Visual Studio instalado F#com ](install-fsharp.md#install-f-with-visual-studio)o.</span><span class="sxs-lookup"><span data-stu-id="58afc-105">To begin, ensure that you have [Visual Studio installed with F#](install-fsharp.md#install-f-with-visual-studio).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="58afc-106">Criando um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="58afc-106">Creating a console application</span></span>

<span data-ttu-id="58afc-107">Um dos projetos mais básicos do Visual Studio é o aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="58afc-107">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="58afc-108">Veja como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="58afc-108">Here's how to do it.</span></span>  <span data-ttu-id="58afc-109">Quando o Visual Studio estiver aberto:</span><span class="sxs-lookup"><span data-stu-id="58afc-109">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="58afc-110">No menu **arquivo** , selecione a opção **novo** e, em seguida, escolha **projeto**.</span><span class="sxs-lookup"><span data-stu-id="58afc-110">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2. <span data-ttu-id="58afc-111">Na caixa de diálogo novo projeto, em **modelos**, você deve **Ver F#Visual** .</span><span class="sxs-lookup"><span data-stu-id="58afc-111">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="58afc-112">Escolha esta seleção para mostrar F# os modelos.</span><span class="sxs-lookup"><span data-stu-id="58afc-112">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="58afc-113">Selecione o aplicativo de **console do .NET Core** ou o **aplicativo de console**.</span><span class="sxs-lookup"><span data-stu-id="58afc-113">Select either **.NET Core Console app** or **Console app**.</span></span>

4. <span data-ttu-id="58afc-114">Escolha o botão **OK** para criar o projeto de F#!</span><span class="sxs-lookup"><span data-stu-id="58afc-114">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="58afc-115">Agora você deve ver um projeto de F# no Gerenciador de soluções.</span><span class="sxs-lookup"><span data-stu-id="58afc-115">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="58afc-116">Escrevendo seu código</span><span class="sxs-lookup"><span data-stu-id="58afc-116">Writing your code</span></span>

<span data-ttu-id="58afc-117">Vamos começar escrevendo um pouco de código.</span><span class="sxs-lookup"><span data-stu-id="58afc-117">Let's get started by writing some code first.</span></span>  <span data-ttu-id="58afc-118">Verifique se o arquivo `Program.fs` está aberto e, em seguida, substitua seu conteúdo pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="58afc-118">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="58afc-119">No exemplo de código anterior, foi definida uma função `square` que recebe uma entrada chamada `x` e a multiplica por si só.</span><span class="sxs-lookup"><span data-stu-id="58afc-119">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="58afc-120">Como o F# usa a [inferência de tipos](../language-reference/type-inference.md), o tipo de  `x` não precisa ser especificado.</span><span class="sxs-lookup"><span data-stu-id="58afc-120">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="58afc-121">O compilador do F# compreende os tipos em que uma multiplicação é válida e atribuirá um tipo para `x` com base em como `square` é chamada.</span><span class="sxs-lookup"><span data-stu-id="58afc-121">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="58afc-122">Se você passar o mouse por cima de `square`, verá o seguinte:</span><span class="sxs-lookup"><span data-stu-id="58afc-122">If you hover over `square`, you should see the following:</span></span>

```fsharp
val square: x:int -> int
```

<span data-ttu-id="58afc-123">Isso é o que é conhecido como assinatura de tipo da função.</span><span class="sxs-lookup"><span data-stu-id="58afc-123">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="58afc-124">Ele pode ser lido da seguinte maneira: "Square é uma função que usa um inteiro chamado x e produz um inteiro".</span><span class="sxs-lookup"><span data-stu-id="58afc-124">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="58afc-125">Observe que o compilador `square` fornecia `int` o tipo por enquanto-isso ocorre porque a multiplicação não é genérica em *todos os* tipos, mas sim em um conjunto fechado de tipos.</span><span class="sxs-lookup"><span data-stu-id="58afc-125">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="58afc-126">O F# compilador escolheu `int` neste ponto, mas ajustará a assinatura de tipo se você chamar `square` com um tipo de entrada diferente, como um `float`.</span><span class="sxs-lookup"><span data-stu-id="58afc-126">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="58afc-127">Outra função, `main`, é definida e decorada com  o atributo `EntryPoint` para informar ao compilador do F# que a execução do programa deve iniciar lá.</span><span class="sxs-lookup"><span data-stu-id="58afc-127">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="58afc-128">Ele segue a mesma convenção que outras [linguagens de programação em estilo C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), em que argumentos de linha de comando podem ser passados para essa função e um código inteiro é retornado (normalmente `0`).</span><span class="sxs-lookup"><span data-stu-id="58afc-128">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="58afc-129">É nessa função que chamamos a `square` função com um argumento de. `12`</span><span class="sxs-lookup"><span data-stu-id="58afc-129">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="58afc-130">Em F# seguida, o compilador atribui o tipo de `square` a `int -> int` (ou seja, uma função que usa um `int` e produz um `int`).</span><span class="sxs-lookup"><span data-stu-id="58afc-130">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="58afc-131">A chamada para `printfn` é uma função de impressão formatada que usa uma cadeia de caracteres de formato, semelhante a linguagens de programação em estilo C, parâmetros que correspondem àquelas especificadas na cadeia de caracteres de formato e, em seguida, imprime o resultado e uma nova linha.</span><span class="sxs-lookup"><span data-stu-id="58afc-131">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="58afc-132">Execução do código</span><span class="sxs-lookup"><span data-stu-id="58afc-132">Running your code</span></span>

<span data-ttu-id="58afc-133">Você pode executar o código e ver os resultados pressionando **Ctrl**+**F5**.</span><span class="sxs-lookup"><span data-stu-id="58afc-133">You can run the code and see results by pressing **Ctrl**+**F5**.</span></span>  <span data-ttu-id="58afc-134">Isso executa o programa sem depuração e permite que você veja os resultados.</span><span class="sxs-lookup"><span data-stu-id="58afc-134">This runs the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="58afc-135">Como alternativa, você pode escolher o item de menu de nível superior de **depuração** no Visual Studio e escolher **Iniciar sem depuração**.</span><span class="sxs-lookup"><span data-stu-id="58afc-135">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="58afc-136">Agora você deve ver o seguinte texto impresso na janela do console que o Visual Studio abriu:</span><span class="sxs-lookup"><span data-stu-id="58afc-136">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```console
12 squared is 144!
```

<span data-ttu-id="58afc-137">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="58afc-137">Congratulations!</span></span>  <span data-ttu-id="58afc-138">Você criou seu primeiro projeto de F# no Visual Studio, escreveu uma função de F#, imprimiu os resultados da chamada dessa função e executou o projeto para ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="58afc-138">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="58afc-139">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="58afc-139">Next steps</span></span>

<span data-ttu-id="58afc-140">Se você ainda não fez isso, confira o [Tour do F# ](../tour.md), que abrange alguns dos principais recursos da linguagem F#.</span><span class="sxs-lookup"><span data-stu-id="58afc-140">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="58afc-141">Ele fornecerá uma visão geral de alguns dos recursos do F# e amplos exemplos de código que você pode copiar para o Visual Studio e executar.</span><span class="sxs-lookup"><span data-stu-id="58afc-141">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="58afc-142">Também há alguns ótimos recursos externos que você pode usar, demonstrados no [ guia do F#](../index.md).</span><span class="sxs-lookup"><span data-stu-id="58afc-142">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="58afc-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58afc-143">See also</span></span>

- [<span data-ttu-id="58afc-144">Tour do F#</span><span class="sxs-lookup"><span data-stu-id="58afc-144">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="58afc-145">F#referência de linguagem</span><span class="sxs-lookup"><span data-stu-id="58afc-145">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="58afc-146">Inferência de tipos</span><span class="sxs-lookup"><span data-stu-id="58afc-146">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="58afc-147">Referência de símbolo e operador</span><span class="sxs-lookup"><span data-stu-id="58afc-147">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
