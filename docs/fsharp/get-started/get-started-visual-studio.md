---
title: "Introdução à linguagem F # no Visual Studio"
description: 'Saiba como usar o F # com o Visual Studio.'
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 02/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8db75596-19a9-4eda-b20d-a12d517c8cc1
ms.openlocfilehash: 944bbbba6a26634ace269d86cbbdde9ef9de7bcd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="4f9f4-104">Introdução à linguagem F # no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4f9f4-104">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="4f9f4-105">F # e as ferramentas do Visual F # têm suporte no Visual Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-105">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>  <span data-ttu-id="4f9f4-106">Para começar, você deve [baixar o Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs), se ainda não o fez.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-106">To begin, you should [download Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs), if you haven't already.</span></span>  <span data-ttu-id="4f9f4-107">Este artigo usa o Visual Studio 2017 Community Edition, mas você pode usar F # com a versão de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-107">This article uses the Visual Studio 2017 Community Edition, but you can use F# with the version of your choice.</span></span>

## <a name="installing-f"></a><span data-ttu-id="4f9f4-108">Instalando a F #</span><span class="sxs-lookup"><span data-stu-id="4f9f4-108">Installing F#</span></span> #

<span data-ttu-id="4f9f4-109">Se você estiver baixando o Visual Studio pela primeira vez, ele será instalado primeiro o instalador do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-109">If you're downloading Visual Studio for the first time, it will first install the Visual Studio installer.</span></span>  <span data-ttu-id="4f9f4-110">Instale qualquer versão do Visual Studio de 2017 do instalador.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-110">Install any version of Visual Studio 2017 from the installer.</span></span> <span data-ttu-id="4f9f4-111">Se você já tiver instalado, clique em **modificar**.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-111">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="4f9f4-112">Em seguida, você verá uma lista de cargas de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-112">You'll next see a list of Workloads.</span></span> <span data-ttu-id="4f9f4-113">Você pode instalar o F # por meio de qualquer uma das seguintes cargas de trabalho:</span><span class="sxs-lookup"><span data-stu-id="4f9f4-113">You can install F# through any of the following workloads:</span></span>

|<span data-ttu-id="4f9f4-114">Carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="4f9f4-114">Workload</span></span>|<span data-ttu-id="4f9f4-115">Ação</span><span class="sxs-lookup"><span data-stu-id="4f9f4-115">Action</span></span>|
|--------|------|
| <span data-ttu-id="4f9f4-116">Desenvolvimento de plataforma cruzada do .NET Core</span><span class="sxs-lookup"><span data-stu-id="4f9f4-116">.NET Core cross-platform development</span></span> | <span data-ttu-id="4f9f4-117">Nenhuma ação - F # é instalada por padrão</span><span class="sxs-lookup"><span data-stu-id="4f9f4-117">No action - F# is installed by default</span></span> |
| <span data-ttu-id="4f9f4-118">Desenvolvimento do ASP.NET e para a Web</span><span class="sxs-lookup"><span data-stu-id="4f9f4-118">ASP.NET and web development</span></span> | <span data-ttu-id="4f9f4-119">Nenhuma ação - F # é instalada por padrão</span><span class="sxs-lookup"><span data-stu-id="4f9f4-119">No action - F# is installed by default</span></span> |
| <span data-ttu-id="4f9f4-120">Desenvolvimento do Azure</span><span class="sxs-lookup"><span data-stu-id="4f9f4-120">Azure development</span></span> | <span data-ttu-id="4f9f4-121">Nenhuma ação - F # é instalada por padrão</span><span class="sxs-lookup"><span data-stu-id="4f9f4-121">No action - F# is installed by default</span></span> |
| <span data-ttu-id="4f9f4-122">Desenvolvimento móvel com o .NET</span><span class="sxs-lookup"><span data-stu-id="4f9f4-122">Mobile development with .NET</span></span> | <span data-ttu-id="4f9f4-123">Nenhuma ação - F # é instalada por padrão</span><span class="sxs-lookup"><span data-stu-id="4f9f4-123">No action - F# is installed by default</span></span> |
| <span data-ttu-id="4f9f4-124">Ciência de dados e aplicativos analíticos</span><span class="sxs-lookup"><span data-stu-id="4f9f4-124">Data science and analytical applications</span></span> | <span data-ttu-id="4f9f4-125">Nenhuma ação - F # é instalada por padrão</span><span class="sxs-lookup"><span data-stu-id="4f9f4-125">No action - F# is installed by default</span></span> |
| <span data-ttu-id="4f9f4-126">Desenvolvimento de área de trabalho do .NET</span><span class="sxs-lookup"><span data-stu-id="4f9f4-126">.NET desktop development</span></span> | <span data-ttu-id="4f9f4-127">Selecione **suporte de idioma da área de trabalho do F #** do lado direito</span><span class="sxs-lookup"><span data-stu-id="4f9f4-127">Select **F# desktop language support** from the right-hand side</span></span> |
| <span data-ttu-id="4f9f4-128">Armazenamento de dados e processamento</span><span class="sxs-lookup"><span data-stu-id="4f9f4-128">Data storage and processing</span></span> | <span data-ttu-id="4f9f4-129">Selecione **suporte de idioma da área de trabalho do F #** do lado direito</span><span class="sxs-lookup"><span data-stu-id="4f9f4-129">Select **F# desktop language support** from the right-hand side</span></span> |

<span data-ttu-id="4f9f4-130">Em seguida, clique em **modificar** na parte inferior direita.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-130">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="4f9f4-131">Isso irá instalar tudo o que você selecionou.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-131">This will install everything you have selected.</span></span>  <span data-ttu-id="4f9f4-132">Você pode em seguida, abra 2017 do Visual Studio com o suporte da linguagem F # **iniciar**.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-132">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="4f9f4-133">Criando um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="4f9f4-133">Creating a console application</span></span>

<span data-ttu-id="4f9f4-134">Um dos projetos mais básicos no Visual Studio é o aplicativo de Console.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-134">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="4f9f4-135">Veja como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-135">Here's how to do it.</span></span>  <span data-ttu-id="4f9f4-136">Depois de abrir o Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="4f9f4-136">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="4f9f4-137">Sobre o **arquivo** , aponte para **novo**e, em seguida, escolha **projeto**.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-137">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2.  <span data-ttu-id="4f9f4-138">No novo projeto caixa de diálogo, em **modelos**, você deve ver **Visual F #**.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-138">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="4f9f4-139">Escolha esta opção para mostrar os modelos de F #.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-139">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="4f9f4-140">Selecione **.NET Core aplicativo de Console** ou **aplicativo de Console**.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-140">Select either **.NET Core Console app** or **Console app**.</span></span>

3. <span data-ttu-id="4f9f4-141">Escolha o **Okey** botão para criar o projeto F #!</span><span class="sxs-lookup"><span data-stu-id="4f9f4-141">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="4f9f4-142">Agora você deve ver um projeto F # no Gerenciador de soluções.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-142">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="4f9f4-143">Escrever seu código</span><span class="sxs-lookup"><span data-stu-id="4f9f4-143">Writing your code</span></span>

<span data-ttu-id="4f9f4-144">Vamos começar escrevendo um código primeiro.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-144">Let's get started by writing some code first.</span></span>  <span data-ttu-id="4f9f4-145">Verifique se o `Program.fs` arquivo está aberto e, em seguida, substitua o seu conteúdo com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4f9f4-145">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="4f9f4-146">No exemplo de código anterior, uma função `square` foi definido que usa uma entrada denominada `x` e multiplica por si só.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-146">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="4f9f4-147">Como F # usa [inferência de tipo](../language-reference/type-inference.md), o tipo de `x` não precisa ser especificado.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-147">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="4f9f4-148">O compilador F # compreende os tipos de onde a multiplicação é válida e atribuirá um tipo para `x` com base em como `square` é chamado.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-148">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="4f9f4-149">Se você focalizar `square`, você deve ver o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4f9f4-149">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="4f9f4-150">Isso é conhecido como assinatura de tipo da função.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-150">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="4f9f4-151">Ele pode ser lido como esta: "quadrada é uma função que usa um número inteiro denominado x e produz um número inteiro".</span><span class="sxs-lookup"><span data-stu-id="4f9f4-151">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="4f9f4-152">Observe que o compilador deu `square` o `int` tipo agora - isso é porque a multiplicação não é genérica em *todos os* tipos, mas em vez disso é genérico em um conjunto fechado de tipos.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-152">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="4f9f4-153">O compilador F # escolhido `int` neste ponto, mas ele ajustará a assinatura de tipo se você chamar `square` com outro tipo de entrada, como um `float`.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-153">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="4f9f4-154">Outra função, `main`, é definido, que é decorado com o `EntryPoint` atributo para informar ao compilador F # que a execução do programa deve iniciar de lá.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-154">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="4f9f4-155">Ele segue a mesma convenção de outros [linguagens de programação C-style](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), onde argumentos de linha de comando podem ser transmitidos para a função e um código inteiro será retornado (geralmente `0`).</span><span class="sxs-lookup"><span data-stu-id="4f9f4-155">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="4f9f4-156">É nessa função que chamamos de `square` função com um argumento de `12`.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-156">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="4f9f4-157">O compilador F #, em seguida, atribui o tipo de `square` ser `int -> int` (ou seja, uma função que leva um `int` e produz um `int`).</span><span class="sxs-lookup"><span data-stu-id="4f9f4-157">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="4f9f4-158">A chamada para `printfn` é uma função de impressão formatada que usa uma cadeia de formato, semelhante a linguagens de programação C-style, os parâmetros que correspondem aos especificados na cadeia de formato e imprime os resultados e uma nova linha.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-158">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="4f9f4-159">Execução do código</span><span class="sxs-lookup"><span data-stu-id="4f9f4-159">Running your code</span></span>

<span data-ttu-id="4f9f4-160">Você pode executar o código e ver os resultados pressionando **ctrl-f5**.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-160">You can run the code and see results by pressing **ctrl-f5**.</span></span>  <span data-ttu-id="4f9f4-161">Isso executará o programa sem depuração e permite que você veja os resultados.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-161">This will run the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="4f9f4-162">Como alternativa, você pode escolher o **depurar** menus de nível superior do item no Visual Studio e escolha **Start Without Debugging**.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-162">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="4f9f4-163">Agora, você verá o seguinte mostrado na janela de console que surge do Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="4f9f4-163">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="4f9f4-164">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="4f9f4-164">Congratulations!</span></span>  <span data-ttu-id="4f9f4-165">Criou seu primeiro projeto F # no Visual Studio, escrito que uma função de F # impressos os resultados da chamada de função e execute o projeto para ver alguns resultados.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-165">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="4f9f4-166">Usando F # interativo</span><span class="sxs-lookup"><span data-stu-id="4f9f4-166">Using F# Interactive</span></span>

<span data-ttu-id="4f9f4-167">Um dos melhores recursos do Visual F # ferramentas no Visual Studio é a janela interativa F #.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-167">One of the best features of the Visual F# tooling in Visual Studio is the F# Interactive Window.</span></span>  <span data-ttu-id="4f9f4-168">Ele permite que você envie código sobre a um processo em que você pode chamar esse código e ver o resultado de forma interativa.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-168">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="4f9f4-169">Para começar a usá-lo, realce o `square` função definida no seu código.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-169">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="4f9f4-170">Em seguida, mantenha o **Alt** chave e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-170">Next, hold the **Alt** key and press **Enter**.</span></span>  <span data-ttu-id="4f9f4-171">Isso executa o código na janela interativa F #.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-171">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="4f9f4-172">Você deverá ver a janela interativa F # com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4f9f4-172">You should see the F# Interactive Window appear with the following in it:</span></span>

```
>

val square : x:int -> int

>
```

<span data-ttu-id="4f9f4-173">Isso mostra a mesma assinatura de função para o `square` função, que você viu anteriormente quando colocado na função.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-173">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="4f9f4-174">Porque `square` está agora definido no processo de F # interativo, você pode chamá-lo com valores diferentes:</span><span class="sxs-lookup"><span data-stu-id="4f9f4-174">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="4f9f4-175">Isso executa a função e associa o resultado para um novo nome `it`e exibe o tipo e o valor de `it`.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-175">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="4f9f4-176">Observe que você deve encerrar a cada linha com `;;`.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-176">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="4f9f4-177">Isso é como F # interativo sabe quando a chamada de função for concluída.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-177">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="4f9f4-178">Você também pode definir novas funções em F # interativo:</span><span class="sxs-lookup"><span data-stu-id="4f9f4-178">You can also define new functions in F# Interactive:</span></span>

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="4f9f4-179">As opções acima define uma nova função, `isOdd`, que usa um `int` e verifica se ele for ímpar!</span><span class="sxs-lookup"><span data-stu-id="4f9f4-179">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span> <span data-ttu-id="4f9f4-180">Você pode chamar essa função para ver o que retorna com entradas diferentes.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-180">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="4f9f4-181">Você pode chamar funções em chamadas de função:</span><span class="sxs-lookup"><span data-stu-id="4f9f4-181">You can call functions within function calls:</span></span>

```
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="4f9f4-182">Você também pode usar o [operador pipe avanço](../language-reference/symbol-and-operator-reference/index.md) para o valor de pipeline para as duas funções:</span><span class="sxs-lookup"><span data-stu-id="4f9f4-182">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="4f9f4-183">O operador de avanço de pipe e muito mais, são abordados em tutoriais subsequentes.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-183">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="4f9f4-184">Isso é apenas uma visão rápida sobre o que você pode fazer com F # interativo.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-184">This is only a glimpse into what you can do with F# Interactive.</span></span> <span data-ttu-id="4f9f4-185">Para saber mais, confira [de programação com F # interativo](../tutorials/fsharp-interactive/index.md).</span><span class="sxs-lookup"><span data-stu-id="4f9f4-185">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="4f9f4-186">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="4f9f4-186">Next steps</span></span>

<span data-ttu-id="4f9f4-187">Se você ainda não fez isso, confira o [Tour do F #](../tour.md), que aborda alguns dos principais recursos da linguagem F #.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-187">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="4f9f4-188">Ele fornece uma visão geral de alguns dos recursos do F # e fornece exemplos de código bastante que você pode copiar para o Visual Studio e executar.</span><span class="sxs-lookup"><span data-stu-id="4f9f4-188">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="4f9f4-189">Também há alguns ótimos recursos externos, você pode usar, foi apresentada no [guia F #](../index.md).</span><span class="sxs-lookup"><span data-stu-id="4f9f4-189">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4f9f4-190">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f9f4-190">See also</span></span>
 [<span data-ttu-id="4f9f4-191">Visual F#</span><span class="sxs-lookup"><span data-stu-id="4f9f4-191">Visual F#</span></span>](index.md)  
 [<span data-ttu-id="4f9f4-192">Tour do F#</span><span class="sxs-lookup"><span data-stu-id="4f9f4-192">Tour of F#</span></span>](../tour.md)  
 [<span data-ttu-id="4f9f4-193">Referência da linguagem F #</span><span class="sxs-lookup"><span data-stu-id="4f9f4-193">F# language reference</span></span>](../language-reference/index.md)  
 [<span data-ttu-id="4f9f4-194">Inferência de tipo</span><span class="sxs-lookup"><span data-stu-id="4f9f4-194">Type inference</span></span>](../language-reference/type-inference.md)  
 [<span data-ttu-id="4f9f4-195">Símbolo e o operador de referência</span><span class="sxs-lookup"><span data-stu-id="4f9f4-195">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)  
