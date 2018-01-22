---
title: "Interpolação de cadeia de caracteres - C#"
description: "Saiba como funciona o interpolação de cadeia de caracteres no C# 6"
keywords: .NET, .NET Core, C#, cadeia de caracteres
author: mgroves
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: f8806f6b-3ac7-4ee6-9b3e-c524d5301ae9
ms.openlocfilehash: b6b3ce53a08cfacfacb19266b0be216a40633352
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="f7486-104">Interpolação de cadeia de caracteres no C#</span><span class="sxs-lookup"><span data-stu-id="f7486-104">String Interpolation in C#</span></span> #

<span data-ttu-id="f7486-105">A interpolação de cadeia de caracteres é a maneira que os espaços reservados em uma cadeia de caracteres são substituídos pelo valor de uma variável de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f7486-105">String Interpolation is the way that placeholders in a string are replaced by the value of a string variable.</span></span> <span data-ttu-id="f7486-106">Antes do C# 6, a maneira de fazer isso era com `System.String.Format`.</span><span class="sxs-lookup"><span data-stu-id="f7486-106">Before C# 6, the way to do this is with `System.String.Format`.</span></span> <span data-ttu-id="f7486-107">Isso funciona, mas como ele usa espaços reservados numerados, pode ser mais difícil de ler e ser mais detalhado.</span><span class="sxs-lookup"><span data-stu-id="f7486-107">This works okay, but since it uses numbered placeholders, it can be harder to read and more verbose.</span></span>

<span data-ttu-id="f7486-108">Outras linguagens de programação tiveram interpolação de cadeia de caracteres integradas à linguagem por algum tempo.</span><span class="sxs-lookup"><span data-stu-id="f7486-108">Other programming languages have had string interpolation built into the language for a while.</span></span> <span data-ttu-id="f7486-109">Por exemplo, em PHP:</span><span class="sxs-lookup"><span data-stu-id="f7486-109">For instance, in PHP:</span></span>

```php
$name = "Jonas";
echo "My name is $name.";
// This will output "My name is Jonas."
```

<span data-ttu-id="f7486-110">No C# 6, finalmente temos esse estilo de interpolação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f7486-110">In C# 6, we finally have that style of string interpolation.</span></span> <span data-ttu-id="f7486-111">Você pode usar um `$` antes de uma cadeia de caracteres para indicar que ele deve substituir variáveis/expressões para seus valores.</span><span class="sxs-lookup"><span data-stu-id="f7486-111">You can use a `$` before a string to indicate that it should substitute variables/expressions for their values.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f7486-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f7486-112">Prerequisites</span></span>
<span data-ttu-id="f7486-113">Você precisará configurar seu computador para executar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f7486-113">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="f7486-114">Você encontrará as instruções de instalação na página do [.NET Core](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="f7486-114">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="f7486-115">Você pode executar esse aplicativo no Windows, Ubuntu Linux, macOS ou em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="f7486-115">You can run this application on Windows, Ubuntu Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="f7486-116">Será necessário instalar o editor de código de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="f7486-116">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="f7486-117">As descrições a seguir usam o [Visual Studio Code](https://code.visualstudio.com/), que é uma software livre, no editor de plataforma.</span><span class="sxs-lookup"><span data-stu-id="f7486-117">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="f7486-118">No entanto, você pode usar quaisquer ferramentas que esteja familiarizado.</span><span class="sxs-lookup"><span data-stu-id="f7486-118">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="f7486-119">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="f7486-119">Create the Application</span></span>

<span data-ttu-id="f7486-120">Agora que você instalou todas as ferramentas, crie um novo aplicativo do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f7486-120">Now that you've installed all the tools, create a new .NET Core application.</span></span> <span data-ttu-id="f7486-121">Para usar o gerador de linha de comando, crie um diretório para seu projeto, como `interpolated`e execute o seguinte comando no shell de sua preferência:</span><span class="sxs-lookup"><span data-stu-id="f7486-121">To use the command line generator, create a directory for your project, such as `interpolated`, and execute the following command in your favorite shell:</span></span>

```
dotnet new console
```

<span data-ttu-id="f7486-122">Esse comando criará um projeto do .NET Core barebones com um arquivo de projeto, *interpolated.csproj*, e um arquivo de código-fonte, *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="f7486-122">This command will create a barebones .NET core project with a project file, *interpolated.csproj*, and a source code file, *Program.cs*.</span></span> <span data-ttu-id="f7486-123">Você precisará executar `dotnet restore` para restaurar as dependências necessárias para compilar esse projeto.</span><span class="sxs-lookup"><span data-stu-id="f7486-123">You will need to execute `dotnet restore` to restore the dependencies needed to compile this project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="f7486-124">Para executar o programa, use `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="f7486-124">To execute the program, use `dotnet run`.</span></span> <span data-ttu-id="f7486-125">Você deve ver a saída do "Olá, Mundo" no console.</span><span class="sxs-lookup"><span data-stu-id="f7486-125">You should see "Hello, World" output to the console.</span></span>



## <a name="intro-to-string-interpolation"></a><span data-ttu-id="f7486-126">Introdução à interpolação de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f7486-126">Intro to String Interpolation</span></span>

<span data-ttu-id="f7486-127">Com `System.String.Format`, especifique "espaços reservados" em uma cadeia de caracteres que são substituídos pelos parâmetros na cadeia de caracteres a seguir.</span><span class="sxs-lookup"><span data-stu-id="f7486-127">With `System.String.Format`, you specify "placeholders" in a string that are replaced by the parameters following the string.</span></span> <span data-ttu-id="f7486-128">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f7486-128">For instance:</span></span>

[!code-csharp[String.Format example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#StringFormatExample)]  

<span data-ttu-id="f7486-129">Isso produzirá "Meu nome é Matt Groves".</span><span class="sxs-lookup"><span data-stu-id="f7486-129">That will output "My name is Matt Groves".</span></span>

<span data-ttu-id="f7486-130">No C# 6, em vez de usar `String.Format`, você define uma cadeia de caracteres interpolada acrescentando-a com o símbolo `$` e, em seguida, usando as variáveis diretamente na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f7486-130">In C# 6, instead of using `String.Format`, you define an interpolated string by prepending it with the `$` symbol, and then using the variables directly in the string.</span></span> <span data-ttu-id="f7486-131">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f7486-131">For instance:</span></span>

[!code-csharp[Interpolation example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExample)]  

<span data-ttu-id="f7486-132">Você não precisa usar apenas variáveis.</span><span class="sxs-lookup"><span data-stu-id="f7486-132">You don't have to use just variables.</span></span> <span data-ttu-id="f7486-133">Você pode usar qualquer expressão entre colchetes.</span><span class="sxs-lookup"><span data-stu-id="f7486-133">You can use any expression within the brackets.</span></span> <span data-ttu-id="f7486-134">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f7486-134">For instance:</span></span>

[!code-csharp[Interpolation expression example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExpressionExample)]  

<span data-ttu-id="f7486-135">O que resultaria:</span><span class="sxs-lookup"><span data-stu-id="f7486-135">Which would output:</span></span>

```
This is line number 1
This is line number 2
This is line number 3
This is line number 4
This is line number 5
```

## <a name="how-string-interpolation-works"></a><span data-ttu-id="f7486-136">Como funciona o interpolação de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f7486-136">How string interpolation works</span></span>

<span data-ttu-id="f7486-137">Nos bastidores, essa sintaxe de interpolação de cadeia de caracteres é convertida em String.Format pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="f7486-137">Behind the scenes, this string interpolation syntax is translated into String.Format by the compiler.</span></span> <span data-ttu-id="f7486-138">Portanto, você pode fazer o [mesmo que já fez antes com String.Format](https://msdn.microsoft.com/library/dwhawy9k(v=vs.110).aspx).</span><span class="sxs-lookup"><span data-stu-id="f7486-138">So, you can do the [same type of stuff you've done before with String.Format](https://msdn.microsoft.com/library/dwhawy9k(v=vs.110).aspx).</span></span>

<span data-ttu-id="f7486-139">Por exemplo, você pode adicionar preenchimento e formatação numérica:</span><span class="sxs-lookup"><span data-stu-id="f7486-139">For instance, you can add padding and numeric formatting:</span></span>

[!code-csharp[Interpolation formatting example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationFormattingExample)]  

<span data-ttu-id="f7486-140">O item acima resultaria em:</span><span class="sxs-lookup"><span data-stu-id="f7486-140">The above would output something like:</span></span>

```
998        5,177.67
999        6,719.30
1000       9,910.61
1001       529.34
1002       1,349.86
1003       2,660.82
1004       6,227.77
```

<span data-ttu-id="f7486-141">Se um nome de variável não for encontrado, será gerado um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="f7486-141">If a variable name is not found, then a compile time error will be generated.</span></span>

<span data-ttu-id="f7486-142">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f7486-142">For instance:</span></span>

```csharp
var animal = "fox";
var localizeMe = $"The {adj} brown {animal} jumped over the lazy {otheranimal}";
var adj = "quick";
Console.WriteLine(localizeMe);
```

<span data-ttu-id="f7486-143">Se compilar isso, você obterá erros:</span><span class="sxs-lookup"><span data-stu-id="f7486-143">If you compile this, you'll get errors:</span></span>
 
* <span data-ttu-id="f7486-144">`Cannot use local variable 'adj' before it is declared` – a variável `adj` não foi declarada até *depois* da cadeia de caracteres interpolada.</span><span class="sxs-lookup"><span data-stu-id="f7486-144">`Cannot use local variable 'adj' before it is declared` - the `adj` variable wasn't declared until *after* the interpolated string.</span></span>
* <span data-ttu-id="f7486-145">`The name 'otheranimal' does not exist in the current context` – uma variável chamada `otheranimal` nunca foi declarada</span><span class="sxs-lookup"><span data-stu-id="f7486-145">`The name 'otheranimal' does not exist in the current context` - a variable called `otheranimal` was never even declared</span></span>

## <a name="localization-and-internationalization"></a><span data-ttu-id="f7486-146">Internacionalização e localização</span><span class="sxs-lookup"><span data-stu-id="f7486-146">Localization and Internationalization</span></span>

<span data-ttu-id="f7486-147">Uma cadeia de caracteres interpolada dá suporte a `IFormattable` e `FormattableString`, o que pode ser útil para internacionalização.</span><span class="sxs-lookup"><span data-stu-id="f7486-147">An interpolated string supports `IFormattable` and `FormattableString`, which can be useful for internationalization.</span></span>

<span data-ttu-id="f7486-148">Por padrão, uma cadeia de caracteres interpolada usa a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="f7486-148">By default, an interpolated string uses the current culture.</span></span> <span data-ttu-id="f7486-149">Para usar uma cultura diferente, você pode convertê-la como `IFormattable`</span><span class="sxs-lookup"><span data-stu-id="f7486-149">To use a different culture, you could cast it as `IFormattable`</span></span>

<span data-ttu-id="f7486-150">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f7486-150">For instance:</span></span>

[!code-csharp[Interpolation internationalization example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationInternationalizationExample)]  

## <a name="conclusion"></a><span data-ttu-id="f7486-151">Conclusão</span><span class="sxs-lookup"><span data-stu-id="f7486-151">Conclusion</span></span> 

<span data-ttu-id="f7486-152">Neste tutorial, você aprendeu como usar recursos de interpolação de cadeia de caracteres de C# 6.</span><span class="sxs-lookup"><span data-stu-id="f7486-152">In this tutorial, you learned how to use string interpolation features of C# 6.</span></span> <span data-ttu-id="f7486-153">Ele é basicamente uma maneira mais concisa de gravar instruções `String.Format` simples, com algumas restrições para usos mais avançados.</span><span class="sxs-lookup"><span data-stu-id="f7486-153">It's basically a more concise way of writing simple `String.Format` statements, with some caveats for more advanced uses of it.</span></span>
