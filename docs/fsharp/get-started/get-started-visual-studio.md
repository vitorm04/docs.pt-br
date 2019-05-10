---
title: Introdução ao F# no Visual Studio
description: Saiba como usar F# com o Visual Studio.
ms.date: 07/03/2018
ms.openlocfilehash: 9b02a5d295f982b1911dab567213fa9a2b6c4304
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754869"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="77ac0-103">Introdução ao F# no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="77ac0-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="77ac0-104">F#e o Visual F# ferramentas têm suporte no IDE do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="77ac0-104">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>

<span data-ttu-id="77ac0-105">Para começar, certifique-se de que você tenha [com o Visual Studio instalado F# ](install-fsharp.md#install-f-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="77ac0-105">To begin, ensure that you have [Visual Studio installed with F#](install-fsharp.md#install-f-with-visual-studio).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="77ac0-106">Criando um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="77ac0-106">Creating a console application</span></span>

<span data-ttu-id="77ac0-107">Um dos projetos mais básicos no Visual Studio é o aplicativo de Console.</span><span class="sxs-lookup"><span data-stu-id="77ac0-107">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="77ac0-108">Veja como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="77ac0-108">Here's how to do it.</span></span>  <span data-ttu-id="77ac0-109">Após abrir o Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="77ac0-109">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="77ac0-110">Sobre o **arquivo** , aponte para **New**e, em seguida, escolha **projeto**.</span><span class="sxs-lookup"><span data-stu-id="77ac0-110">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2. <span data-ttu-id="77ac0-111">Na nova caixa de diálogo projeto, sob **modelos**, você deverá ver **Visual F#** .</span><span class="sxs-lookup"><span data-stu-id="77ac0-111">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="77ac0-112">Escolha esta opção para mostrar o F# modelos.</span><span class="sxs-lookup"><span data-stu-id="77ac0-112">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="77ac0-113">Selecione a **aplicativo de Console do .NET Core** ou **aplicativo de Console**.</span><span class="sxs-lookup"><span data-stu-id="77ac0-113">Select either **.NET Core Console app** or **Console app**.</span></span>

4. <span data-ttu-id="77ac0-114">Escolha o **Okey** botão para criar o F# projeto!</span><span class="sxs-lookup"><span data-stu-id="77ac0-114">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="77ac0-115">Agora você deve ver uma F# projeto no Gerenciador de soluções.</span><span class="sxs-lookup"><span data-stu-id="77ac0-115">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="77ac0-116">Escrever seu código</span><span class="sxs-lookup"><span data-stu-id="77ac0-116">Writing your code</span></span>

<span data-ttu-id="77ac0-117">Vamos começar escrevendo um código pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="77ac0-117">Let's get started by writing some code first.</span></span>  <span data-ttu-id="77ac0-118">Certifique-se de que o `Program.fs` arquivo está aberto e, em seguida, substitua seu conteúdo pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="77ac0-118">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="77ac0-119">No exemplo de código anterior, uma função `square` tenha sido definido, que usa uma entrada denominada `x` e multiplica por si só.</span><span class="sxs-lookup"><span data-stu-id="77ac0-119">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="77ac0-120">Porque F# usa [inferência de tipo](../language-reference/type-inference.md), o tipo de `x` não precisa ser especificado.</span><span class="sxs-lookup"><span data-stu-id="77ac0-120">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="77ac0-121">O F# compilador entende os tipos em que a multiplicação é válida e atribuirá um tipo para `x` com base em como `square` é chamado.</span><span class="sxs-lookup"><span data-stu-id="77ac0-121">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="77ac0-122">Se você focalizar `square`, você deve ver o seguinte:</span><span class="sxs-lookup"><span data-stu-id="77ac0-122">If you hover over `square`, you should see the following:</span></span>

```fsharp
val square: x:int -> int
```

<span data-ttu-id="77ac0-123">Esse é o que é conhecido como assinatura de tipo da função.</span><span class="sxs-lookup"><span data-stu-id="77ac0-123">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="77ac0-124">Ele pode ser lido como este: "Quadrado é uma função que usa um número inteiro denominado x e produz um número inteiro".</span><span class="sxs-lookup"><span data-stu-id="77ac0-124">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="77ac0-125">Observe que o compilador forneceu `square` as `int` tipo por ora - isso é porque a multiplicação não é genérica entre *todos os* tipos, mas em vez disso, é genérico em um conjunto fechado de tipos.</span><span class="sxs-lookup"><span data-stu-id="77ac0-125">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="77ac0-126">O F# compilador escolhido `int` neste ponto, mas ele se ajustará a assinatura de tipo se você chamar `square` com outro tipo de entrada, como um `float`.</span><span class="sxs-lookup"><span data-stu-id="77ac0-126">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="77ac0-127">Outra função, `main`, é definido, que é decorado com o `EntryPoint` atributo para informar o F# compilador que a execução do programa deve iniciar lá.</span><span class="sxs-lookup"><span data-stu-id="77ac0-127">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="77ac0-128">Ele segue a mesma convenção que outro [linguagens de programação C-style](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), em que os argumentos de linha de comando podem ser passados para essa função, e um código inteiro será retornado (normalmente `0`).</span><span class="sxs-lookup"><span data-stu-id="77ac0-128">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="77ac0-129">É nessa função que podemos chamar o `square` função com um argumento de `12`.</span><span class="sxs-lookup"><span data-stu-id="77ac0-129">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="77ac0-130">O F# compilador, em seguida, atribui o tipo de `square` seja `int -> int` (ou seja, uma função que leva um `int` e produz um `int`).</span><span class="sxs-lookup"><span data-stu-id="77ac0-130">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="77ac0-131">A chamada para `printfn` é uma função de impressão formatada que usa uma cadeia de formato, semelhante a linguagens de programação C-style, parâmetros que correspondem aos especificados na cadeia de caracteres de formato e, em seguida, imprime o resultado e uma nova linha.</span><span class="sxs-lookup"><span data-stu-id="77ac0-131">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="77ac0-132">Execução do código</span><span class="sxs-lookup"><span data-stu-id="77ac0-132">Running your code</span></span>

<span data-ttu-id="77ac0-133">Você pode executar o código e ver resultados pressionando **Ctrl**+**F5**.</span><span class="sxs-lookup"><span data-stu-id="77ac0-133">You can run the code and see results by pressing **Ctrl**+**F5**.</span></span>  <span data-ttu-id="77ac0-134">Isso executa o programa sem depuração e permite que você veja os resultados.</span><span class="sxs-lookup"><span data-stu-id="77ac0-134">This runs the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="77ac0-135">Como alternativa, você pode escolher o **Debug** menu de nível superior do item no Visual Studio e escolha **Start Without Debugging**.</span><span class="sxs-lookup"><span data-stu-id="77ac0-135">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="77ac0-136">Agora, você verá o seguinte mostrado na janela de console que surge do Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="77ac0-136">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="77ac0-137">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="77ac0-137">Congratulations!</span></span>  <span data-ttu-id="77ac0-138">Você criou seu primeiro F# projeto no Visual Studio, escrito um F# função impresso os resultados da chamada de função e execute o projeto para ver alguns resultados.</span><span class="sxs-lookup"><span data-stu-id="77ac0-138">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="77ac0-139">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="77ac0-139">Next steps</span></span>

<span data-ttu-id="77ac0-140">Se você ainda não fez isso, confira a [Tour do F# ](../tour.md), que aborda alguns dos principais recursos do F# linguagem.</span><span class="sxs-lookup"><span data-stu-id="77ac0-140">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="77ac0-141">Ele lhe fornecerá uma visão geral de alguns dos recursos do F#e fornecem exemplos de código amplo que você pode copiar para o Visual Studio e executar.</span><span class="sxs-lookup"><span data-stu-id="77ac0-141">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="77ac0-142">Também existem alguns ótimos recursos externos, você pode usar, foi apresentada na [ F# guia de](../index.md).</span><span class="sxs-lookup"><span data-stu-id="77ac0-142">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="77ac0-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77ac0-143">See also</span></span>

- [<span data-ttu-id="77ac0-144">Tour do F#</span><span class="sxs-lookup"><span data-stu-id="77ac0-144">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="77ac0-145">F#referência da linguagem</span><span class="sxs-lookup"><span data-stu-id="77ac0-145">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="77ac0-146">Inferência de tipo</span><span class="sxs-lookup"><span data-stu-id="77ac0-146">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="77ac0-147">Referência de símbolo e o operador</span><span class="sxs-lookup"><span data-stu-id="77ac0-147">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
