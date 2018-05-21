---
title: Novidades no C# 7.1
description: Uma visão geral dos novos recursos no C# 7.1.
ms.date: 08/16/2017
ms.openlocfilehash: 00baec45d7582d3ac12c7b0865241f5cd8159246
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="49d92-103">Novidades no C# 7.1</span><span class="sxs-lookup"><span data-stu-id="49d92-103">What's new in C# 7.1</span></span>

<span data-ttu-id="49d92-104">O C# 7.1 é a primeira versão de ponto da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="49d92-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="49d92-105">Ele marca uma cadência de versão maior para a linguagem.</span><span class="sxs-lookup"><span data-stu-id="49d92-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="49d92-106">Use os novos recursos mais cedo, de preferência, quando cada novo recurso estiver pronto.</span><span class="sxs-lookup"><span data-stu-id="49d92-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="49d92-107">O C# 7.1 adiciona a capacidade de configurar o compilador para que ele corresponda a uma versão especificada da linguagem.</span><span class="sxs-lookup"><span data-stu-id="49d92-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="49d92-108">Isso permite que você separe a decisão de atualizar ferramentas da decisão de atualizar versões da linguagem.</span><span class="sxs-lookup"><span data-stu-id="49d92-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="49d92-109">O C# 7.1 adiciona a [seleção de versão da linguagem](#language-version-selection) elemento de configuração, três novos recursos de linguagem e um novo comportamento do compilador.</span><span class="sxs-lookup"><span data-stu-id="49d92-109">C# 7.1 adds the [language version selection](#language-version-selection) configuration element, three new language features and new compiler behavior.</span></span>

<span data-ttu-id="49d92-110">Os novos recursos de linguagem nesta versão são:</span><span class="sxs-lookup"><span data-stu-id="49d92-110">The new language features in this release are:</span></span>

* [<span data-ttu-id="49d92-111">`async` Método `Main`</span><span class="sxs-lookup"><span data-stu-id="49d92-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="49d92-112">O ponto de entrada para um aplicativo pode ter o modificador `async`.</span><span class="sxs-lookup"><span data-stu-id="49d92-112">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="49d92-113">`default` Expressões literais</span><span class="sxs-lookup"><span data-stu-id="49d92-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="49d92-114">Use expressões literais padrão em expressões de valor padrão quando o tipo de destino pode ser inferido.</span><span class="sxs-lookup"><span data-stu-id="49d92-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="49d92-115">Nomes de elementos de tupla inferidos</span><span class="sxs-lookup"><span data-stu-id="49d92-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="49d92-116">Em muitos casos, os nomes dos elementos de tupla podem ser inferidos com base na inicialização da tupla.</span><span class="sxs-lookup"><span data-stu-id="49d92-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>

<span data-ttu-id="49d92-117">Por fim, o compilador traz duas opções `/refout` e `/refonly`, que controlam a [geração de assembly de referência](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="49d92-117">Finally, the compiler has two options `/refout` and `/refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

## <a name="language-version-selection"></a><span data-ttu-id="49d92-118">Seleção de versão da linguagem</span><span class="sxs-lookup"><span data-stu-id="49d92-118">Language version selection</span></span>

<span data-ttu-id="49d92-119">O compilador do C# dá suporte ao C# 7.1 desde o Visual Studio 2017 versão 15.3 ou o SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="49d92-119">The C# compiler supports C# 7.1 starting with Visual Studio 2017 version 15.3, or the .NET Core SDK 2.0.</span></span> <span data-ttu-id="49d92-120">No entanto, os recursos do 7.1 estão desativados por padrão.</span><span class="sxs-lookup"><span data-stu-id="49d92-120">However, the 7.1 features are turned off by default.</span></span> <span data-ttu-id="49d92-121">Para habilitar os recursos do 7.1, é necessário alterar a configuração da versão da linguagem do projeto.</span><span class="sxs-lookup"><span data-stu-id="49d92-121">To enable the 7.1 features, you need to change the language version setting for your project.</span></span>

<span data-ttu-id="49d92-122">No Visual Studio, clique com o botão direito do mouse no nó do projeto no Gerenciador de Soluções e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="49d92-122">In Visual Studio, right-click on the project node in Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="49d92-123">Selecione a guia **Build** e o botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="49d92-123">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="49d92-124">No menu suspenso, selecione **Última versão secundária do C# (última)** ou o **C# 7.1** com a versão específica, conforme mostrado na imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="49d92-124">In the dropdown, select **C# latest minor version (latest)**, or the specific version **C# 7.1** as shown in the image following.</span></span> <span data-ttu-id="49d92-125">O valor `latest` significa que você deseja usar a última versão secundária no computador atual.</span><span class="sxs-lookup"><span data-stu-id="49d92-125">The `latest` value means you want to use the latest minor version on the current machine.</span></span> <span data-ttu-id="49d92-126">O `C# 7.1` significa que você desejará usar o C# 7.1, mesmo depois que forem liberadas novas versões secundárias.</span><span class="sxs-lookup"><span data-stu-id="49d92-126">The `C# 7.1` means that you want to use C# 7.1, even after newer minor versions are released.</span></span>

![Definindo a versão da linguagem](./media/csharp-7-1/advanced-build-settings.png)

<span data-ttu-id="49d92-128">Como alternativa, você pode editar o arquivo "csproj" e adicionar ou modificar as seguintes linhas:</span><span class="sxs-lookup"><span data-stu-id="49d92-128">Alternatively, you can edit the "csproj" file and add or modify the following lines:</span></span>

```xml
<PropertyGroup>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="49d92-129">Se você usar o IDE do Visual Studio para atualizar os arquivos csproj, o IDE criará nós separados para cada configuração de build.</span><span class="sxs-lookup"><span data-stu-id="49d92-129">If you use the Visual Studio IDE to update your csproj files, the IDE creates separate nodes for each build configuration.</span></span> <span data-ttu-id="49d92-130">Normalmente, você definirá o valor da mesma forma em todas as configurações de build, mas precisará defini-lo explicitamente para cada configuração de build ou selecionar "Todas as Configurações" ao modificar essa configuração.</span><span class="sxs-lookup"><span data-stu-id="49d92-130">You'll typically set the value the same in all build configurations, but you need to set it explicitly for each build configuration, or select "All Configurations" when you modify this setting.</span></span> <span data-ttu-id="49d92-131">Você verá o seguinte no arquivo csproj:</span><span class="sxs-lookup"><span data-stu-id="49d92-131">You'll see the following in your csproj file:</span></span>

```xml
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="49d92-132">As configurações válidas para o elemento `LangVersion` são:</span><span class="sxs-lookup"><span data-stu-id="49d92-132">Valid settings for the `LangVersion` element are:</span></span>

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

<span data-ttu-id="49d92-133">As cadeias de caracteres especiais `default` e `latest` são resolvidas nas últimas versões da linguagem principal e secundária instaladas no computador de build, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="49d92-133">The special strings `default` and `latest` resolve to the latest major and minor language versions installed on the build machine, respectively.</span></span>

<span data-ttu-id="49d92-134">Essa configuração desacopla a instalação de novas versões do SDK e das ferramentas no ambiente de desenvolvimento da escolha de incorporar novos recursos de linguagem em um projeto.</span><span class="sxs-lookup"><span data-stu-id="49d92-134">This setting decouples installing new versions of the SDK and tools in your development environment from choosing to incorporate new language features in a project.</span></span> <span data-ttu-id="49d92-135">Instale o último SDK e as últimas ferramentas no computador de build.</span><span class="sxs-lookup"><span data-stu-id="49d92-135">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="49d92-136">Cada projeto pode ser configurado para usar uma versão específica da linguagem de seu build.</span><span class="sxs-lookup"><span data-stu-id="49d92-136">Each project can be configured to use a specific version of the language for its build.</span></span>

## <a name="async-main"></a><span data-ttu-id="49d92-137">Async main</span><span class="sxs-lookup"><span data-stu-id="49d92-137">Async main</span></span>

<span data-ttu-id="49d92-138">Um método *async main* permite que você use `await` no método `Main`.</span><span class="sxs-lookup"><span data-stu-id="49d92-138">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="49d92-139">Anteriormente, você precisava escrever:</span><span class="sxs-lookup"><span data-stu-id="49d92-139">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="49d92-140">Agora, você pode escrever:</span><span class="sxs-lookup"><span data-stu-id="49d92-140">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="49d92-141">Se o programa não retorna um código de saída, declare um método `Main` que retorna um <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="49d92-141">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="49d92-142">Leia mais sobre os detalhes no tópico [async main](../programming-guide/main-and-command-args/index.md) no guia de programação.</span><span class="sxs-lookup"><span data-stu-id="49d92-142">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) topic in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="49d92-143">Expressões literais padrão</span><span class="sxs-lookup"><span data-stu-id="49d92-143">Default literal expressions</span></span>

<span data-ttu-id="49d92-144">Expressões literais padrão são uma melhoria das expressões de valor padrão.</span><span class="sxs-lookup"><span data-stu-id="49d92-144">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="49d92-145">Essas expressões inicializam uma variável com o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="49d92-145">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="49d92-146">Nos casos em que você anteriormente escrevia:</span><span class="sxs-lookup"><span data-stu-id="49d92-146">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="49d92-147">Agora você pode omitir o tipo no lado direito da inicialização:</span><span class="sxs-lookup"><span data-stu-id="49d92-147">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="49d92-148">Saiba mais sobre essa melhoria no tópico do Guia de Programação do C# em [expressões de valor padrão](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="49d92-148">You can learn more about this enhancement in the C# Programming Guide topic on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="49d92-149">Essa melhoria também altera algumas das regras de análise da [palavra-chave padrão](../language-reference/keywords/default.md).</span><span class="sxs-lookup"><span data-stu-id="49d92-149">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="49d92-150">Nomes de elementos de tupla inferidos</span><span class="sxs-lookup"><span data-stu-id="49d92-150">Inferred tuple element names</span></span>

<span data-ttu-id="49d92-151">Esse recurso é uma pequena melhoria do recurso de tuplas introduzido no C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="49d92-151">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="49d92-152">Muitas vezes quando você inicializa uma tupla, as variáveis usadas para o lado direito da atribuição são iguais aos nomes que você deseja usar para os elementos de tupla:</span><span class="sxs-lookup"><span data-stu-id="49d92-152">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="49d92-153">Os nomes dos elementos de tupla podem ser inferidos com base nas variáveis usadas para inicializar a tupla no C# 7.1:</span><span class="sxs-lookup"><span data-stu-id="49d92-153">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="49d92-154">Saiba mais sobre esse recurso no tópico [Tuplas](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="49d92-154">You can learn more about this feature in the [Tuples](../tuples.md) topic.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="49d92-155">Geração de assembly de referência</span><span class="sxs-lookup"><span data-stu-id="49d92-155">Reference assembly generation</span></span>

<span data-ttu-id="49d92-156">Há duas novas opções do compilador que geram *assemblies somente de referência*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) e [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="49d92-156">There are two new compiler options that generate *reference-only assemblies*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) and [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="49d92-157">Os tópicos vinculados explicam essas opções e os assemblies de referência mais detalhadamente.</span><span class="sxs-lookup"><span data-stu-id="49d92-157">The linked topics explain these options and reference assemblies in more detail.</span></span>
