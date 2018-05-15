---
title: 'Introdução ao F # no Visual Studio para Mac'
description: 'Saiba como usar F # com o Visual Studio para Mac.'
ms.date: 02/13/2017
ms.openlocfilehash: 58e65e703b092f2ee5d74386051b158c932013b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a><span data-ttu-id="a9135-103">Introdução ao F # no Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="a9135-103">Get started with F# in Visual Studio for Mac</span></span>

<span data-ttu-id="a9135-104">F # e as ferramentas do Visual F # têm suporte no Visual Studio para Mac IDE.</span><span class="sxs-lookup"><span data-stu-id="a9135-104">F# and the Visual F# tooling are supported in the Visual Studio for Mac IDE.</span></span>  <span data-ttu-id="a9135-105">Para começar, você deve [baixar o Visual Studio para Mac](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), se ainda não o fez.</span><span class="sxs-lookup"><span data-stu-id="a9135-105">To begin, you should [download Visual Studio for Mac](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), if you haven't already.</span></span>  <span data-ttu-id="a9135-106">Este artigo usa o Visual Studio de 2017 de comunidade para Mac, mas você pode usar F # com a versão de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="a9135-106">This article uses the Visual Studio Community 2017 for Mac, but you can use F# with the version of your choice.</span></span>

## <a name="installing-f"></a><span data-ttu-id="a9135-107">Instalando a F #</span><span class="sxs-lookup"><span data-stu-id="a9135-107">Installing F#</span></span> #

<span data-ttu-id="a9135-108">Depois de baixar o Visual Studio para Mac, ele solicitará que você escolher o que você deseja instalar.</span><span class="sxs-lookup"><span data-stu-id="a9135-108">After downloading Visual Studio for Mac, it will prompt you to choose what you want to install.</span></span>  <span data-ttu-id="a9135-109">Para os fins deste artigo, estará deixando os padrões.</span><span class="sxs-lookup"><span data-stu-id="a9135-109">For the purposes of this article we will be leaving the defaults.</span></span>  <span data-ttu-id="a9135-110">Em contraste com o Visual Studio para Windows, não é necessário instalar especificamente o suporte de F #.</span><span class="sxs-lookup"><span data-stu-id="a9135-110">In contrast to Visual Studio for Windows, you do not need to specifically install F# support.</span></span>  <span data-ttu-id="a9135-111">Clique em "Instalar" para continuar.</span><span class="sxs-lookup"><span data-stu-id="a9135-111">Press "Install" to proceed.</span></span>

<span data-ttu-id="a9135-112">Depois de concluir a instalação, escolha "Iniciar o Visual Studio".</span><span class="sxs-lookup"><span data-stu-id="a9135-112">After the install completes, choose "Start Visual Studio".</span></span>  <span data-ttu-id="a9135-113">Você também pode iniciá-lo por meio de localizador em macOS.</span><span class="sxs-lookup"><span data-stu-id="a9135-113">You can also launch it through Finder on macOS.</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="a9135-114">Criando um aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="a9135-114">Creating a console application</span></span>

<span data-ttu-id="a9135-115">Um dos projetos no Visual Studio para Mac mais básicos é o aplicativo de Console.</span><span class="sxs-lookup"><span data-stu-id="a9135-115">One of the most basic projects in Visual Studio for Mac is the Console Application.</span></span>  <span data-ttu-id="a9135-116">Veja como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="a9135-116">Here's how to do it.</span></span>  <span data-ttu-id="a9135-117">Depois de abrir o Visual Studio para Mac:</span><span class="sxs-lookup"><span data-stu-id="a9135-117">Once Visual Studio for Mac is open:</span></span>

1. <span data-ttu-id="a9135-118">Sobre o **arquivo** , aponte para **nova solução**.</span><span class="sxs-lookup"><span data-stu-id="a9135-118">On the **File** menu, point to **New Solution**.</span></span>

2.  <span data-ttu-id="a9135-119">Na caixa de diálogo Novo projeto, há 2 modelos diferentes para o aplicativo de Console.</span><span class="sxs-lookup"><span data-stu-id="a9135-119">In the New Project dialog, there are 2 different templates for Console Application.</span></span>  <span data-ttu-id="a9135-120">Há um sob outros -> .NET que tem como alvo o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a9135-120">There is one under Other -> .NET which targets the .NET Framework.</span></span>  <span data-ttu-id="a9135-121">O outro modelo é em .NET Core -> aplicativo que tem como alvo o núcleo do .NET.</span><span class="sxs-lookup"><span data-stu-id="a9135-121">The other template is under .NET Core -> App which targets .NET Core.</span></span>  <span data-ttu-id="a9135-122">O modelo deve funcionar com a finalidade deste artigo.</span><span class="sxs-lookup"><span data-stu-id="a9135-122">Either template should work for the purpose of this article.</span></span>

3. <span data-ttu-id="a9135-123">Em aplicativo de console, altere c# para F # se necessário.</span><span class="sxs-lookup"><span data-stu-id="a9135-123">Under console app, change C# to F# if needed.</span></span>  <span data-ttu-id="a9135-124">Escolha o **próximo** botão Avançar!</span><span class="sxs-lookup"><span data-stu-id="a9135-124">Choose the **Next** button to move forward!</span></span>  

4. <span data-ttu-id="a9135-125">Nomeie o projeto e escolha as opções desejadas para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a9135-125">Give your project a name, and choose the options you want for the app.</span></span>  <span data-ttu-id="a9135-126">Observe, o painel de visualização para o lado da tela que mostra a estrutura de diretório será criada com base nas opções selecionadas.</span><span class="sxs-lookup"><span data-stu-id="a9135-126">Notice, the preview pane to the side of the screen that will show the directory structure that will be created based on the options selected.</span></span>  

5. <span data-ttu-id="a9135-127">Clique em **Criar**.</span><span class="sxs-lookup"><span data-stu-id="a9135-127">Click **Create**.</span></span>  <span data-ttu-id="a9135-128">Agora você deve ver um projeto F # no Gerenciador de soluções.</span><span class="sxs-lookup"><span data-stu-id="a9135-128">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="a9135-129">Escrever seu código</span><span class="sxs-lookup"><span data-stu-id="a9135-129">Writing your code</span></span>

<span data-ttu-id="a9135-130">Vamos começar escrevendo um código primeiro.</span><span class="sxs-lookup"><span data-stu-id="a9135-130">Let's get started by writing some code first.</span></span>  <span data-ttu-id="a9135-131">Verifique se o `Program.fs` arquivo está aberto e, em seguida, substitua o seu conteúdo com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a9135-131">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="a9135-132">No exemplo de código anterior, uma função `square` foi definido que usa uma entrada denominada `x` e multiplica por si só.</span><span class="sxs-lookup"><span data-stu-id="a9135-132">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="a9135-133">Como F # usa [inferência de tipo](../language-reference/type-inference.md), o tipo de `x` não precisa ser especificado.</span><span class="sxs-lookup"><span data-stu-id="a9135-133">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="a9135-134">O compilador F # compreende os tipos de onde a multiplicação é válida e atribuirá um tipo para `x` com base em como `square` é chamado.</span><span class="sxs-lookup"><span data-stu-id="a9135-134">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="a9135-135">Se você focalizar `square`, você deve ver o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a9135-135">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="a9135-136">Isso é conhecido como assinatura de tipo da função.</span><span class="sxs-lookup"><span data-stu-id="a9135-136">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="a9135-137">Ele pode ser lido como esta: "quadrada é uma função que usa um número inteiro denominado x e produz um número inteiro".</span><span class="sxs-lookup"><span data-stu-id="a9135-137">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="a9135-138">Observe que o compilador deu `square` o `int` tipo agora - isso é porque a multiplicação não é genérica em *todos os* tipos, mas em vez disso é genérico em um conjunto fechado de tipos.</span><span class="sxs-lookup"><span data-stu-id="a9135-138">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="a9135-139">O compilador F # escolhido `int` neste ponto, mas ele ajustará a assinatura de tipo se você chamar `square` com outro tipo de entrada, como um `float`.</span><span class="sxs-lookup"><span data-stu-id="a9135-139">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="a9135-140">Outra função, `main`, é definido, que é decorado com o `EntryPoint` atributo para informar ao compilador F # que a execução do programa deve iniciar de lá.</span><span class="sxs-lookup"><span data-stu-id="a9135-140">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="a9135-141">Ele segue a mesma convenção de outros [linguagens de programação C-style](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), onde argumentos de linha de comando podem ser transmitidos para a função e um código inteiro será retornado (geralmente `0`).</span><span class="sxs-lookup"><span data-stu-id="a9135-141">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="a9135-142">É nessa função que chamamos de `square` função com um argumento de `12`.</span><span class="sxs-lookup"><span data-stu-id="a9135-142">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="a9135-143">O compilador F #, em seguida, atribui o tipo de `square` ser `int -> int` (ou seja, uma função que leva um `int` e produz um `int`).</span><span class="sxs-lookup"><span data-stu-id="a9135-143">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="a9135-144">A chamada para `printfn` é uma função de impressão formatada que usa uma cadeia de formato, semelhante a linguagens de programação C-style, os parâmetros que correspondem aos especificados na cadeia de formato e imprime os resultados e uma nova linha.</span><span class="sxs-lookup"><span data-stu-id="a9135-144">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="a9135-145">Execução do código</span><span class="sxs-lookup"><span data-stu-id="a9135-145">Running your code</span></span>

<span data-ttu-id="a9135-146">Você pode executar o código e ver os resultados, basta clicar em **executar** no menu de nível superior e, em seguida, **Start Without Debugging**.</span><span class="sxs-lookup"><span data-stu-id="a9135-146">You can run the code and see results by clicking on **Run** from the top level menu and then **Start Without Debugging**.</span></span>  <span data-ttu-id="a9135-147">Isso executará o programa sem depuração e permite que você veja os resultados.</span><span class="sxs-lookup"><span data-stu-id="a9135-147">This will run the program without debugging and allows you to see the results.</span></span>

<span data-ttu-id="a9135-148">Agora, você verá o seguinte mostrado na janela de console que surge do Visual Studio para Mac:</span><span class="sxs-lookup"><span data-stu-id="a9135-148">You should now see the following printed to the console window that Visual Studio for Mac popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="a9135-149">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="a9135-149">Congratulations!</span></span>  <span data-ttu-id="a9135-150">Criou seu primeiro projeto F # no Visual Studio para Mac, escrito que uma função de F # impressos os resultados da chamada de função e execute o projeto para ver alguns resultados.</span><span class="sxs-lookup"><span data-stu-id="a9135-150">You've created your first F# project in Visual Studio for Mac, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="a9135-151">Usando F # interativo</span><span class="sxs-lookup"><span data-stu-id="a9135-151">Using F# Interactive</span></span>

<span data-ttu-id="a9135-152">Um dos melhores recursos do Visual F # ferramentas no Visual Studio para Mac é a janela interativa F #.</span><span class="sxs-lookup"><span data-stu-id="a9135-152">One of the best features of the Visual F# tooling in Visual Studio for Mac is the F# Interactive Window.</span></span>  <span data-ttu-id="a9135-153">Ele permite que você envie código sobre a um processo em que você pode chamar esse código e ver o resultado de forma interativa.</span><span class="sxs-lookup"><span data-stu-id="a9135-153">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="a9135-154">Para começar a usá-lo, realce o `square` função definida no seu código.</span><span class="sxs-lookup"><span data-stu-id="a9135-154">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="a9135-155">Em seguida, clique em **editar** no menu de nível superior.</span><span class="sxs-lookup"><span data-stu-id="a9135-155">Next, click on **Edit** from the top level menu.</span></span>  <span data-ttu-id="a9135-156">Em seguida selecione **enviar seleção para F # interativo**.</span><span class="sxs-lookup"><span data-stu-id="a9135-156">Next select **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="a9135-157">Isso executa o código na janela interativa F #.</span><span class="sxs-lookup"><span data-stu-id="a9135-157">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="a9135-158">Como alternativa, você pode clique com o botão direito na seleção e escolha **enviar seleção para F # interativo**.</span><span class="sxs-lookup"><span data-stu-id="a9135-158">Alternatively, you can right click on the selection and choose **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="a9135-159">Você deverá ver a janela interativa F # com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a9135-159">You should see the F# Interactive Window appear with the following in it:</span></span>

```
>

val square : x:int -> int

>
```

<span data-ttu-id="a9135-160">Isso mostra a mesma assinatura de função para o `square` função, que você viu anteriormente quando colocado na função.</span><span class="sxs-lookup"><span data-stu-id="a9135-160">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="a9135-161">Porque `square` está agora definido no processo de F # interativo, você pode chamá-lo com valores diferentes:</span><span class="sxs-lookup"><span data-stu-id="a9135-161">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="a9135-162">Isso executa a função e associa o resultado para um novo nome `it`e exibe o tipo e o valor de `it`.</span><span class="sxs-lookup"><span data-stu-id="a9135-162">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="a9135-163">Observe que você deve encerrar a cada linha com `;;`.</span><span class="sxs-lookup"><span data-stu-id="a9135-163">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="a9135-164">Isso é como F # interativo sabe quando a chamada de função for concluída.</span><span class="sxs-lookup"><span data-stu-id="a9135-164">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="a9135-165">Você também pode definir novas funções em F # interativo:</span><span class="sxs-lookup"><span data-stu-id="a9135-165">You can also define new functions in F# Interactive:</span></span>

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="a9135-166">As opções acima define uma nova função, `isOdd`, que usa um `int` e verifica se ele for ímpar!</span><span class="sxs-lookup"><span data-stu-id="a9135-166">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span>  <span data-ttu-id="a9135-167">Você pode chamar essa função para ver o que retorna com entradas diferentes.</span><span class="sxs-lookup"><span data-stu-id="a9135-167">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="a9135-168">Você pode chamar funções em chamadas de função:</span><span class="sxs-lookup"><span data-stu-id="a9135-168">You can call functions within function calls:</span></span>

```
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="a9135-169">Você também pode usar o [operador pipe avanço](../language-reference/symbol-and-operator-reference/index.md) para o valor de pipeline para as duas funções:</span><span class="sxs-lookup"><span data-stu-id="a9135-169">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="a9135-170">O operador de avanço de pipe e muito mais, são abordados em tutoriais subsequentes.</span><span class="sxs-lookup"><span data-stu-id="a9135-170">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="a9135-171">Isso é apenas uma visão rápida sobre o que você pode fazer com F # interativo.</span><span class="sxs-lookup"><span data-stu-id="a9135-171">This is only a glimpse into what you can do with F# Interactive.</span></span>  <span data-ttu-id="a9135-172">Para saber mais, confira [de programação com F # interativo](../tutorials/fsharp-interactive/index.md).</span><span class="sxs-lookup"><span data-stu-id="a9135-172">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="a9135-173">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="a9135-173">Next steps</span></span>

<span data-ttu-id="a9135-174">Se você ainda não fez isso, confira o [Tour do F #](../tour.md), que aborda alguns dos principais recursos da linguagem F #.</span><span class="sxs-lookup"><span data-stu-id="a9135-174">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="a9135-175">Ele fornece uma visão geral de alguns dos recursos do F # e fornece exemplos de código bastante que você pode copiar para o Visual Studio para Mac e executar.</span><span class="sxs-lookup"><span data-stu-id="a9135-175">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio for Mac and run.</span></span>  <span data-ttu-id="a9135-176">Também há alguns ótimos recursos externos, você pode usar, foi apresentada no [guia F #](../index.md).</span><span class="sxs-lookup"><span data-stu-id="a9135-176">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a9135-177">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9135-177">See also</span></span>
 [<span data-ttu-id="a9135-178">Visual F#</span><span class="sxs-lookup"><span data-stu-id="a9135-178">Visual F#</span></span>](../index.md)  
 [<span data-ttu-id="a9135-179">Tour do F#</span><span class="sxs-lookup"><span data-stu-id="a9135-179">Tour of F#</span></span>](../tour.md)  
 [<span data-ttu-id="a9135-180">Referência da linguagem F #</span><span class="sxs-lookup"><span data-stu-id="a9135-180">F# language reference</span></span>](../language-reference/index.md)  
 [<span data-ttu-id="a9135-181">Inferência de tipo</span><span class="sxs-lookup"><span data-stu-id="a9135-181">Type inference</span></span>](../language-reference/type-inference.md)  
 [<span data-ttu-id="a9135-182">Símbolo e o operador de referência</span><span class="sxs-lookup"><span data-stu-id="a9135-182">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)  
