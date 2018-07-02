---
title: Desenvolvendo bibliotecas com as Ferramentas de Plataforma Cruzada
description: Saiba como criar bibliotecas para .NET usando ferramentas da CLI do .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 05/01/2017
ms.openlocfilehash: a6db7a15c484122600afd54814d19ea11bd1abc1
ms.sourcegitcommit: ceca5a1c027627abcca2767567703c3879f33325
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2018
ms.locfileid: "33218141"
---
# <a name="developing-libraries-with-cross-platform-tools"></a><span data-ttu-id="9a9b9-103">Desenvolvendo bibliotecas com as Ferramentas de Plataforma Cruzada</span><span class="sxs-lookup"><span data-stu-id="9a9b9-103">Developing Libraries with Cross Platform Tools</span></span>

<span data-ttu-id="9a9b9-104">Esse artigo aborda como escrever bibliotecas para .NET usando as ferramentas de plataforma cruzada da CLI.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-104">This article covers how to write libraries for .NET using cross-platform CLI tools.</span></span> <span data-ttu-id="9a9b9-105">A CLI fornece uma experiência eficiente e de baixo nível que funciona em qualquer sistema operacional com suporte.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-105">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="9a9b9-106">Você ainda pode criar bibliotecas com o Visual Studio e, se essa for sua experiência preferida, [consultar o guia do Visual Studio](libraries-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9a9b9-106">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](libraries-with-vs.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9a9b9-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="9a9b9-107">Prerequisites</span></span>

<span data-ttu-id="9a9b9-108">Você precisa da [CLI e do SDK do .NET Core](https://www.microsoft.com/net/core) instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-108">You need [the .NET Core SDK and CLI](https://www.microsoft.com/net/core) installed on your machine.</span></span>

<span data-ttu-id="9a9b9-109">Para as seções deste documento que tratam de versões do .NET Framework, é necessário ter o [.NET Framework](http://getdotnet.azurewebsites.net/) instalado em um computador Windows.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-109">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](http://getdotnet.azurewebsites.net/) installed on a Windows machine.</span></span>

<span data-ttu-id="9a9b9-110">Além disso, se você quiser dar suporte a destinos do .NET Framework mais antigos, você precisará instalar pacotes de direcionamento/desenvolvedor para versões mais antigas de estrutura na [página de plataformas de destino do .NET](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html).</span><span class="sxs-lookup"><span data-stu-id="9a9b9-110">Additionally, if you wish to support older .NET Framework targets, you need to install targeting/developer packs for older framework versions from the [.NET target platforms page](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html).</span></span> <span data-ttu-id="9a9b9-111">Consulte esta tabela:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-111">Refer to this table:</span></span>

| <span data-ttu-id="9a9b9-112">Versão do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9a9b9-112">.NET Framework Version</span></span> | <span data-ttu-id="9a9b9-113">O que baixar</span><span class="sxs-lookup"><span data-stu-id="9a9b9-113">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="9a9b9-114">4.6.1</span><span class="sxs-lookup"><span data-stu-id="9a9b9-114">4.6.1</span></span>                  | <span data-ttu-id="9a9b9-115">Pacote de Direcionamento do .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="9a9b9-115">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="9a9b9-116">4.6</span><span class="sxs-lookup"><span data-stu-id="9a9b9-116">4.6</span></span>                    | <span data-ttu-id="9a9b9-117">Pacote de Direcionamento do .NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="9a9b9-117">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="9a9b9-118">4.5.2</span><span class="sxs-lookup"><span data-stu-id="9a9b9-118">4.5.2</span></span>                  | <span data-ttu-id="9a9b9-119">Pacote de Desenvolvedor do .NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="9a9b9-119">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="9a9b9-120">4.5.1</span><span class="sxs-lookup"><span data-stu-id="9a9b9-120">4.5.1</span></span>                  | <span data-ttu-id="9a9b9-121">Pacote de Desenvolvedor do .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="9a9b9-121">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="9a9b9-122">4.5</span><span class="sxs-lookup"><span data-stu-id="9a9b9-122">4.5</span></span>                    | <span data-ttu-id="9a9b9-123">Software Development Kit do Windows (SDK do Windows) para Windows 8</span><span class="sxs-lookup"><span data-stu-id="9a9b9-123">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="9a9b9-124">4.0</span><span class="sxs-lookup"><span data-stu-id="9a9b9-124">4.0</span></span>                    | <span data-ttu-id="9a9b9-125">SDK do Windows para Windows 7 e .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="9a9b9-125">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="9a9b9-126">2.0, 3.0 e 3.5</span><span class="sxs-lookup"><span data-stu-id="9a9b9-126">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="9a9b9-127">Tempo de Execução do .NET Framework 3.5 SP1 (ou versão do Windows 8 ou superior)</span><span class="sxs-lookup"><span data-stu-id="9a9b9-127">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="9a9b9-128">Como direcionar para o .NET Standard</span><span class="sxs-lookup"><span data-stu-id="9a9b9-128">How to target the .NET Standard</span></span>

<span data-ttu-id="9a9b9-129">Se você ainda não conhece o .NET Standard, veja [.NET Standard](../../standard/net-standard.md) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-129">If you're not quite familiar with the .NET Standard, refer to the [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="9a9b9-130">Nesse artigo, há uma tabela que mapeia as versões do .NET Standard para várias implementações:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-130">In that article, there is a table which maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](~/includes/net-standard-table.md)]

<span data-ttu-id="9a9b9-131">Veja aqui o que essa tabela significa para fins de criação de uma biblioteca:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-131">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="9a9b9-132">A versão do .NET Standard que você escolher será uma escolha entre acessar as APIs mais recentes e a capacidade de direcionar para mais implementações do .NET e versões do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-132">The version of the .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="9a9b9-133">Você controla o intervalo das plataformas que podem ser destinos e as versões escolhendo uma versão de `netstandardX.X` (em que `X.X` é um número de versão) e a adicionando ao seu arquivo de projeto (`.csproj` ou `.fsproj`).</span><span class="sxs-lookup"><span data-stu-id="9a9b9-133">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (Where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="9a9b9-134">Você tem três opções principais ao direcionar para o .NET Standard, dependendo das suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-134">You have three primary options when targeting the .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="9a9b9-135">Você pode usar a versão padrão do .NET Standard fornecido por modelos, `netstandard1.4`, que fornece acesso à maioria das APIs no .NET Standard ao mesmo tempo que mantém a compatibilidade com UWP, .NET Framework 4.6.1 e o próximo .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-135">You can use the default version of the .NET Standard supplied by templates - `netstandard1.4` - which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and the forthcoming .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="9a9b9-136">Você pode usar uma versão inferior ou superior do .NET Standard, modificando o valor no nó `TargetFramework` do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-136">You can use a lower or higher version of the .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>
    
    <span data-ttu-id="9a9b9-137">Versões do .NET Standard são compatíveis com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-137">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="9a9b9-138">Isso significa que as bibliotecas `netstandard1.0` são executadas em plataformas `netstandard1.1` e superior.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-138">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="9a9b9-139">No entanto, não há compatibilidade com versões posteriores: plataformas inferiores do .NET Standard não podem fazer referência às superiores.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-139">However, there is no forward compatibility - lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="9a9b9-140">Isso significa que as bibliotecas `netstandard1.0` não podem fazer de referência a bibliotecas direcionadas a `netstandard1.1` ou superior.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-140">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="9a9b9-141">Selecione a versão Standard com a combinação de suporte a APIs e plataformas ideal para suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-141">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="9a9b9-142">É recomendável `netstandard1.4` por enquanto.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-142">We recommend `netstandard1.4` for now.</span></span>
    
3. <span data-ttu-id="9a9b9-143">Se desejar direcionar para o .NET Framework versões 4.0 ou inferior ou se desejar usar uma API disponível no .NET Framework, mas não no .NET Standard (por exemplo, `System.Drawing`), leia as seções a seguir para aprender a usar multiplataformas.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-143">If you want to target the .NET Framework versions 4.0 or below, or you wish to use an API available in the .NET Framework but not in the .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-the-net-framework"></a><span data-ttu-id="9a9b9-144">Como direcionar o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9a9b9-144">How to target the .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="9a9b9-145">Essas instruções pressupõem que você tenha o .NET Framework instalado no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-145">These instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="9a9b9-146">Consulte os [Pré-requisitos](#prerequisites) para obter as dependências instaladas.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-146">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="9a9b9-147">Lembre que algumas das versões do .NET Framework usadas aqui não têm mais suporte.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-147">Keep in mind that some of the .NET Framework versions used here are no longer in support.</span></span> <span data-ttu-id="9a9b9-148">Consulte as [Perguntas Frequentes de Política do Ciclo de Vida de Suporte do .NET Framework](https://support.microsoft.com/gp/framework_faq/en-us) sobre versões sem suporte.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-148">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="9a9b9-149">Se desejar alcançar o número máximo de projetos e desenvolvedores, use o .NET Framework 4.0 como seu destino de linha de base.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-149">If you want to reach the maximum number of developers and projects, use the .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="9a9b9-150">Para direcionar para o .NET Framework, você precisará começar usando o TFM (Moniker da Estrutura de Destino) correto correspondente à versão do .NET Framework à qual você deseja dar suporte.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-150">To target the .NET Framework, you will need to begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

```
.NET Framework 2.0   --> net20
.NET Framework 3.0   --> net30
.NET Framework 3.5   --> net35
.NET Framework 4.0   --> net40
.NET Framework 4.5   --> net45
.NET Framework 4.5.1 --> net451
.NET Framework 4.5.2 --> net452
.NET Framework 4.6   --> net46
.NET Framework 4.6.1 --> net461
.NET Framework 4.6.2 --> net462
.NET Framework 4.7   --> net47
```

<span data-ttu-id="9a9b9-151">Em seguida, insira esse TFM na seção `TargetFramework` do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-151">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="9a9b9-152">Por exemplo, aqui está como você escreveria uma biblioteca direcionada ao .NET Framework 4.0:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-152">For example, here's how you would write a library which targets the .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="9a9b9-153">E pronto.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-153">And that's it!</span></span> <span data-ttu-id="9a9b9-154">Embora seja compilado somente para o .NET Framework 4, você pode usar a biblioteca em versões mais recentes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-154">Although this compiled only for the .NET Framework 4, you can use the library on newer versions of the .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="9a9b9-155">Como usar Multiplataformas</span><span class="sxs-lookup"><span data-stu-id="9a9b9-155">How to Multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="9a9b9-156">As instruções a seguir pressupõem que você tenha o .NET Framework instalado no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-156">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="9a9b9-157">Consulte a seção [Pré-requisitos](#prerequisites) para saber quais dependências você precisa instalar e de onde baixá-las.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-157">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="9a9b9-158">Talvez seja necessário direcionar para versões mais antigas do .NET Framework quando seu projeto dá suporte a ambos o .NET Framework e o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-158">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="9a9b9-159">Nesse cenário, se você quiser usar construções de linguagem e APIs mais recentes para os destinos, use as diretivas `#if` no seu código.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-159">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="9a9b9-160">Você também pode precisar adicionar diferentes pacotes e dependências para cada plataforma de destino para incluir as diferentes APIs necessárias para cada caso.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-160">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="9a9b9-161">Por exemplo, digamos que você tem uma biblioteca que executa operações de rede por meio de HTTP.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-161">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="9a9b9-162">Para .NET Standard e .NET Framework versões 4.5 ou posterior, você pode usar a classe `HttpClient` do namespace `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-162">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="9a9b9-163">No entanto, versões anteriores do .NET Framework não tem a classe `HttpClient`, portanto, você pode usar a classe `WebClient` do namespace `System.Net` para elas.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-163">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="9a9b9-164">O arquivo de projeto seria semelhante a:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-164">Your project file could look like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.0 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net40'">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.5 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net45'">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="9a9b9-165">Você notará três alterações importantes aqui:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-165">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="9a9b9-166">O nó `TargetFramework` foi substituído pelo `TargetFrameworks` e três TFMs são expressas dentro.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-166">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="9a9b9-167">Há um nó `<ItemGroup>` para o destino `net40 ` extraindo um que o .NET Framework referencia.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-167">There is an `<ItemGroup>` node for the `net40 ` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="9a9b9-168">Há um nó `<ItemGroup>` para o destino `net45` extraindo dois que o .NET Framework referencia.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-168">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="9a9b9-169">O sistema de build reconhece os seguintes símbolos do pré-processador usados nas diretivas `#if`:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-169">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

<span data-ttu-id="9a9b9-170">Aqui está um exemplo fazendo uso de compilação condicional por destino:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-170">Here is an example making use of conditional compilation per-target:</span></span>

```csharp
using System;
using System.Text.RegularExpressions;
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
 // This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif

namespace MultitargetLib
{
    public class Library
    {
#if NET40
        private readonly WebClient _client = new WebClient();
        private readonly object _locker = new object();
#else
        private readonly HttpClient _client = new HttpClient();
#endif

#if NET40
        // .NET Framework 4.0 does not have async/await
        public string GetDotNetCount()
        {
            string url = "http://www.dotnetfoundation.org/";

            var uri = new Uri(url);

            string result = "";

            // Lock here to provide thread-safety.
            lock(_locker)
            {
                result = _client.DownloadString(uri);
            }

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"Dotnet Foundation mentions .NET {dotNetCount} times!";
        }
#else
        // .NET 4.5+ can use async/await!
        public async Task<string> GetDotNetCountAsync()
        {
            string url = "http://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

<span data-ttu-id="9a9b9-171">Se você compilar esse projeto com `dotnet build`, notará três diretórios sob a pasta `bin/`:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-171">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="9a9b9-172">Cada um deles contém arquivos `.dll` para cada destino.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-172">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="9a9b9-173">Como testar bibliotecas .NET Core</span><span class="sxs-lookup"><span data-stu-id="9a9b9-173">How to test libraries on .NET Core</span></span>

<span data-ttu-id="9a9b9-174">É importante ser capaz de testar em várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-174">It's important to be able to test across platforms.</span></span> <span data-ttu-id="9a9b9-175">Você pode usar o [xUnit](http://xunit.github.io/) ou MSTest pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-175">You can use either [xUnit](http://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="9a9b9-176">Ambos são perfeitamente adequados para realizar o teste da unidade de biblioteca no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-176">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="9a9b9-177">A maneira de configurar sua solução com projetos de teste dependerá da [estrutura da sua solução](#structuring-a-solution).</span><span class="sxs-lookup"><span data-stu-id="9a9b9-177">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="9a9b9-178">O exemplo a seguir pressupõe que os diretórios de origem e de teste estão no mesmo diretório de nível superior.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-178">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="9a9b9-179">Ele usa alguns [comandos da CLI do .NET Core](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="9a9b9-179">This uses some [.NET Core CLI commands](../tools/index.md).</span></span> <span data-ttu-id="9a9b9-180">Consulte [dotnet new](../tools/dotnet-new.md) e [dotnet sln](../tools/dotnet-sln.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-180">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="9a9b9-181">Configure sua solução.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-181">Set up your solution.</span></span> <span data-ttu-id="9a9b9-182">Você pode fazer isso usando os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-182">You can do so with the following commands:</span></span>

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="9a9b9-183">Isso criará projetos e os conectará em uma solução.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-183">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="9a9b9-184">O diretório para `SolutionWithSrcAndTest` deve ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-184">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="9a9b9-185">Navegue até o diretório do projeto de teste e adicione uma referência a `MyProject.Test` de `MyProject`.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-185">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="9a9b9-186">Restaure os pacotes e compile projetos:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-186">Restore packages and build projects:</span></span>

   ```bash
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. <span data-ttu-id="9a9b9-187">Verifique se o xUnit é executado por meio da execução do comando `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-187">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="9a9b9-188">Se você optar por usar o MSTest, o executor de console do MSTest deverá ser executado.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-188">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>
    
<span data-ttu-id="9a9b9-189">E pronto.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-189">And that's it!</span></span> <span data-ttu-id="9a9b9-190">Agora você pode testar sua biblioteca em todas as plataformas usando as ferramentas de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-190">You can now test your library across all platforms using command line tools.</span></span> <span data-ttu-id="9a9b9-191">É muito simples testar sua biblioteca agora que está tudo configurado:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-191">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="9a9b9-192">Faça alterações na sua biblioteca.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-192">Make changes to your library.</span></span>
1. <span data-ttu-id="9a9b9-193">Execute os testes de linha de comando no diretório de teste com o comando `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-193">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="9a9b9-194">Seu código será recriado automaticamente quando você invoca o comando `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-194">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="9a9b9-195">Como usar vários projetos</span><span class="sxs-lookup"><span data-stu-id="9a9b9-195">How to use multiple projects</span></span>

<span data-ttu-id="9a9b9-196">Uma necessidade comum das bibliotecas grandes é alocar funcionalidades em diferentes projetos.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-196">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="9a9b9-197">Imagine que você deseja compilar uma biblioteca que poderia ser consumida em expressões idiomáticas de C# e F#.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-197">Imagine you wished to build a library which could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="9a9b9-198">Isso significa que os consumidores da sua biblioteca o farão de maneira natural ao C# ou F#.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-198">That would mean that consumers of your library consume them in ways which are natural to C# or F#.</span></span> <span data-ttu-id="9a9b9-199">Por exemplo, você poderia consumir a biblioteca em C# dessa forma:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-199">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="9a9b9-200">No F#, ela poderia assemelhar-se a:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-200">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="9a9b9-201">Cenários de consumo como esse significam que as APIs que estão sendo acessadas devem ter uma estrutura diferente para C# e F#.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-201">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="9a9b9-202">Uma abordagem comum para realizar isso é fatorar toda a lógica de uma biblioteca em um projeto principal, com projetos C# e F# definindo as camadas de API que chamam esse projeto principal.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-202">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="9a9b9-203">O restante da seção usará os nomes a seguir:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-203">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="9a9b9-204">**AwesomeLibrary.Core** – Um projeto principal que contém toda a lógica para a biblioteca</span><span class="sxs-lookup"><span data-stu-id="9a9b9-204">**AwesomeLibrary.Core** - A core project which contains all logic for the library</span></span>
* <span data-ttu-id="9a9b9-205">**AwesomeLibrary.CSharp** – Um projeto com APIs públicas destinadas ao consumo em C#</span><span class="sxs-lookup"><span data-stu-id="9a9b9-205">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="9a9b9-206">**AwesomeLibrary.FSharp** – Um projeto com APIs públicas destinadas ao consumo em F#</span><span class="sxs-lookup"><span data-stu-id="9a9b9-206">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="9a9b9-207">Você pode executar os comandos a seguir no seu terminal para produzir a mesma estrutura que este guia:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-207">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

```console
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang F#
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

<span data-ttu-id="9a9b9-208">Isso adicionará os três projetos acima e um arquivo de solução que os vincula.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-208">This will add the three projects above and a solution file which links them together.</span></span> <span data-ttu-id="9a9b9-209">Criar o arquivo de solução e vincular projetos permitirá que você restaure e compile projetos de um nível superior.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-209">Creating the solution file and linking projects will allow you to restore and build projects from a top-level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="9a9b9-210">Referência projeto a projeto</span><span class="sxs-lookup"><span data-stu-id="9a9b9-210">Project-to-project referencing</span></span>

<span data-ttu-id="9a9b9-211">A melhor maneira de fazer referência a um projeto é usar a CLI do .NET Core para adicionar uma referência de projeto.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-211">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="9a9b9-212">Dos diretórios dos projetos **AwesomeLibrary.CSharp** e **AwesomeLibrary.FSharp**, você pode executar o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-212">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```console
$ dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="9a9b9-213">Os arquivos de projeto para **AwesomeLibrary.CSharp** e **AwesomeLibrary.FSharp** agora farão referência a **AwesomeLibrary.Core** como um destino `ProjectReference`.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-213">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="9a9b9-214">Você pode verificar isso inspecionando os arquivos de projeto e vendo o seguinte neles:</span><span class="sxs-lookup"><span data-stu-id="9a9b9-214">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="9a9b9-215">Você pode adicionar esta seção a cada arquivo de projeto manualmente se preferir não usar a CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-215">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="9a9b9-216">Estruturar uma solução</span><span class="sxs-lookup"><span data-stu-id="9a9b9-216">Structuring a solution</span></span>

<span data-ttu-id="9a9b9-217">Outro aspecto importante das soluções multiprojetos é estabelecer uma boa estrutura de projeto geral.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-217">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="9a9b9-218">Você pode organizar o código da maneira que desejar, e desde que vincule cada projeto ao arquivo de solução com `dotnet sln add`, você poderá executar `dotnet restore` e `dotnet build` no nível da solução.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-218">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
