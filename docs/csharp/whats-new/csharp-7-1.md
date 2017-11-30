---
title: "O que há de novo no c# 7.1"
description: "Uma visão geral dos novos recursos no c# 7.1."
keywords: Design de linguagem c#, 7.1, Visual Studio de 2017,
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: 02f1f8fc8f0a3221e00e2a3c43ce06423ca43672
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="f1f91-104">O que há de novo no c# 7.1</span><span class="sxs-lookup"><span data-stu-id="f1f91-104">What's new in C# 7.1</span></span>

<span data-ttu-id="f1f91-105">7.1 c# é a primeira versão de ponto para a linguagem c#.</span><span class="sxs-lookup"><span data-stu-id="f1f91-105">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="f1f91-106">Marca uma cadência de lançamento maior para o idioma.</span><span class="sxs-lookup"><span data-stu-id="f1f91-106">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="f1f91-107">Você pode usar os novos recursos mais cedo, idealmente quando cada novo recurso está pronto.</span><span class="sxs-lookup"><span data-stu-id="f1f91-107">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="f1f91-108">7.1 c# adiciona a capacidade de configurar o compilador para corresponder a uma versão especificada do idioma.</span><span class="sxs-lookup"><span data-stu-id="f1f91-108">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="f1f91-109">Que permite que você separe a decisão de atualizar ferramentas de decisão para atualizar versões de idioma.</span><span class="sxs-lookup"><span data-stu-id="f1f91-109">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="f1f91-110">7.1 c# adiciona o [seleção de versão de idioma](#language-version-selection) elemento de configuração, três novos recursos de idioma e o novo comportamento do compilador.</span><span class="sxs-lookup"><span data-stu-id="f1f91-110">C# 7.1 adds the [language version selection](#language-version-selection) configuration element, three new language features and new compiler behavior.</span></span>

<span data-ttu-id="f1f91-111">Os novos recursos de idioma nesta versão são:</span><span class="sxs-lookup"><span data-stu-id="f1f91-111">The new language features in this release are:</span></span>

* [<span data-ttu-id="f1f91-112">`async``Main` método</span><span class="sxs-lookup"><span data-stu-id="f1f91-112">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="f1f91-113">O ponto de entrada para um aplicativo pode ter o `async` modificador.</span><span class="sxs-lookup"><span data-stu-id="f1f91-113">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="f1f91-114">`default`expressões literais</span><span class="sxs-lookup"><span data-stu-id="f1f91-114">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="f1f91-115">Você pode usar expressões de literal padrão em expressões de valor padrão quando o tipo de destino pode ser inferido.</span><span class="sxs-lookup"><span data-stu-id="f1f91-115">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="f1f91-116">Nomes de elemento de tupla deduzido</span><span class="sxs-lookup"><span data-stu-id="f1f91-116">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="f1f91-117">Os nomes dos elementos de tupla podem ser inferidos de inicialização de tupla em muitos casos.</span><span class="sxs-lookup"><span data-stu-id="f1f91-117">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>

<span data-ttu-id="f1f91-118">Por fim, o compilador tem duas opções `/refout` e `/refonly` que controlam [fazem referência a geração de assembly](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="f1f91-118">Finally, the compiler has two options `/refout` and `/refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

## <a name="language-version-selection"></a><span data-ttu-id="f1f91-119">Seleção de versão de idioma</span><span class="sxs-lookup"><span data-stu-id="f1f91-119">Language version selection</span></span>

<span data-ttu-id="f1f91-120">O compilador c# oferece suporte a c# 7.1 começando com Visual Studio 2017 versão 15,3 ou o .NET Core SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="f1f91-120">The C# compiler supports C# 7.1 starting with Visual Studio 2017 version 15.3, or the .NET Core SDK 2.0.</span></span> <span data-ttu-id="f1f91-121">No entanto, os 7.1 recursos são desativados por padrão.</span><span class="sxs-lookup"><span data-stu-id="f1f91-121">However, the 7.1 features are turned off by default.</span></span> <span data-ttu-id="f1f91-122">Para habilitar os 7.1 recursos, você precisa alterar a configuração de versão de idioma para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="f1f91-122">To enable the 7.1 features, you need to change the language version setting for your project.</span></span>

<span data-ttu-id="f1f91-123">No Visual Studio, clique com botão direito no nó do projeto no Gerenciador de soluções e selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="f1f91-123">In Visual Studio, right-click on the project node in Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="f1f91-124">Selecione o **criar** guia e selecione o **avançado** botão.</span><span class="sxs-lookup"><span data-stu-id="f1f91-124">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="f1f91-125">No menu suspenso, selecione **c# versão secundária mais recente (mais recente)**, ou a versão específica **c# 7.1** conforme mostrado na seguinte imagem.</span><span class="sxs-lookup"><span data-stu-id="f1f91-125">In the dropdown, select **C# latest minor version (latest)**, or the specific version **C# 7.1** as shown in the image following.</span></span> <span data-ttu-id="f1f91-126">O `latest` valor significa que você deseja usar a versão secundária mais recente no computador atual.</span><span class="sxs-lookup"><span data-stu-id="f1f91-126">The `latest` value means you want to use the latest minor version on the current machine.</span></span> <span data-ttu-id="f1f91-127">O `C# 7.1` significa que você deseja usar o c# 7.1, mesmo depois que são lançadas novas versões secundárias.</span><span class="sxs-lookup"><span data-stu-id="f1f91-127">The `C# 7.1` means that you want to use C# 7.1, even after newer minor versions are released.</span></span>

![Definindo a versão de idioma](./media/csharp-7-1/advanced-build-settings.png)

<span data-ttu-id="f1f91-129">Como alternativa, você pode editar o arquivo "csproj" e adicionar ou modificar as seguintes linhas:</span><span class="sxs-lookup"><span data-stu-id="f1f91-129">Alternatively, you can edit the "csproj" file and add or modify the following lines:</span></span>

```xml
<PropertyGroup>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="f1f91-130">Se você usar o IDE do Visual Studio para atualizar seus arquivos csproj, o IDE criará nós separados para cada configuração de compilação.</span><span class="sxs-lookup"><span data-stu-id="f1f91-130">If you use the Visual Studio IDE to update your csproj files, the IDE creates separate nodes for each build configuration.</span></span> <span data-ttu-id="f1f91-131">Você normalmente definirá o valor a mesma em todas as configurações de compilação, mas é necessário defini-las explicitamente para cada configuração de compilação, ou selecione "Todas as configurações de" quando você modificar essa configuração.</span><span class="sxs-lookup"><span data-stu-id="f1f91-131">You'll typically set the value the same in all build configurations, but you need to set it explicitly for each build configuration, or select "All Configurations" when you modify this setting.</span></span> <span data-ttu-id="f1f91-132">Você verá o seguinte no arquivo csproj:</span><span class="sxs-lookup"><span data-stu-id="f1f91-132">You'll see the following in your csproj file:</span></span>

```xml
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="f1f91-133">As configurações válidas para o `LangVersion` elemento são:</span><span class="sxs-lookup"><span data-stu-id="f1f91-133">Valid settings for the `LangVersion` element are:</span></span>

* `ISO-1`
* `ISO-2`
* `3`
* `4`
* `5`
* `6`
* `7`
* `7.1`
* `default`
* `latest`

<span data-ttu-id="f1f91-134">As cadeias de caracteres especiais `default` e `latest` resolver para as versões de idioma principal e secundária mais recentes instaladas no computador de build, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="f1f91-134">The special strings `default` and `latest` resolve to the latest major and minor language versions installed on the build machine, respectively.</span></span>

<span data-ttu-id="f1f91-135">Essa configuração separa instalar novas versões do SDK e ferramentas em seu ambiente de desenvolvimento de escolher incorporar os novos recursos de idioma em um projeto.</span><span class="sxs-lookup"><span data-stu-id="f1f91-135">This setting decouples installing new versions of the SDK and tools in your development environment from choosing to incorporate new language features in a project.</span></span> <span data-ttu-id="f1f91-136">Você pode instalar o SDK e as ferramentas mais recentes no seu computador de compilação.</span><span class="sxs-lookup"><span data-stu-id="f1f91-136">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="f1f91-137">Cada projeto pode ser configurado para usar uma versão específica do idioma de sua compilação.</span><span class="sxs-lookup"><span data-stu-id="f1f91-137">Each project can be configured to use a specific version of the language for its build.</span></span>

## <a name="async-main"></a><span data-ttu-id="f1f91-138">Assíncrono principal</span><span class="sxs-lookup"><span data-stu-id="f1f91-138">Async main</span></span>

<span data-ttu-id="f1f91-139">Um *async principal* método permite que você use `await` no seu `Main` método.</span><span class="sxs-lookup"><span data-stu-id="f1f91-139">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="f1f91-140">Anteriormente, era necessário escrever:</span><span class="sxs-lookup"><span data-stu-id="f1f91-140">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="f1f91-141">Agora você pode escrever:</span><span class="sxs-lookup"><span data-stu-id="f1f91-141">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="f1f91-142">Se o programa não retorna um código de saída, você pode declarar uma `Main` método que retorna um <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="f1f91-142">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="f1f91-143">Você pode ler mais sobre os detalhes no [async principal](../programming-guide/main-and-command-args/index.md) tópico no guia de programação.</span><span class="sxs-lookup"><span data-stu-id="f1f91-143">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) topic in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="f1f91-144">Expressões de literal padrão</span><span class="sxs-lookup"><span data-stu-id="f1f91-144">Default literal expressions</span></span>

<span data-ttu-id="f1f91-145">Expressões literais padrão são um aprimoramento de expressões de valor padrão.</span><span class="sxs-lookup"><span data-stu-id="f1f91-145">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="f1f91-146">Essas expressões inicializar uma variável com o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="f1f91-146">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="f1f91-147">Onde você anteriormente escreve:</span><span class="sxs-lookup"><span data-stu-id="f1f91-147">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="f1f91-148">Agora você pode omitir o tipo do lado direito da inicialização:</span><span class="sxs-lookup"><span data-stu-id="f1f91-148">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="f1f91-149">Você pode aprender mais sobre esse aprimoramento do tópico do guia de programação em c# em [padrão de expressões de valor](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f1f91-149">You can learn more about this enhancement in the C# Programming Guide topic on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="f1f91-150">Esse aprimoramento altera algumas das regras de análise para o [palavra-chave default](../language-reference/keywords/default.md).</span><span class="sxs-lookup"><span data-stu-id="f1f91-150">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="f1f91-151">Nomes de elemento de tupla deduzido</span><span class="sxs-lookup"><span data-stu-id="f1f91-151">Inferred tuple element names</span></span>

<span data-ttu-id="f1f91-152">Esse recurso é um aprimoramento pequeno para o recurso de tuplas, introduzido no c# 7.0.</span><span class="sxs-lookup"><span data-stu-id="f1f91-152">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="f1f91-153">Muitas vezes quando você inicializa uma tupla, as variáveis usadas para o lado direito da atribuição são iguais aos nomes que você deseja para os elementos de tupla:</span><span class="sxs-lookup"><span data-stu-id="f1f91-153">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="f1f91-154">Os nomes dos elementos de tupla podem ser inferidos de variáveis usadas para inicializar a tupla no c# 7.1:</span><span class="sxs-lookup"><span data-stu-id="f1f91-154">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="f1f91-155">Você pode aprender mais sobre esse recurso no [tuplas](../tuples.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="f1f91-155">You can learn more about this feature in the [Tuples](../tuples.md) topic.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="f1f91-156">Geração de assembly de referência</span><span class="sxs-lookup"><span data-stu-id="f1f91-156">Reference assembly generation</span></span>

<span data-ttu-id="f1f91-157">Há duas novas opções de compilador que geram *assemblies de referência*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) e [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="f1f91-157">There are two new compiler options that generate *reference-only assemblies*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) and [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="f1f91-158">Os tópicos vinculados explicam essas opções e os assemblies de referência em mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="f1f91-158">The linked topics explain these options and reference assemblies in more detail.</span></span>
