---
title: Analisador de API do .NET
description: Saiba como o analisador de API do .NET pode ajudar a detectar problemas de compatibilidade de plataforma e de APIs preteridas.
author: oliag
ms.author: mairaw
ms.date: 04/26/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 584f9f952148ebf72c5d5aaed64a2a078be00ce5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929361"
---
# <a name="net-api-analyzer"></a><span data-ttu-id="88b71-103">Analisador de API do .NET</span><span class="sxs-lookup"><span data-stu-id="88b71-103">.NET API analyzer</span></span>

<span data-ttu-id="88b71-104">O analisador do API .NET é um analisador Roslyn que descobre riscos potenciais de compatibilidade para APIs em C# em diferentes plataformas e detecta chamadas a APIs preteridas.</span><span class="sxs-lookup"><span data-stu-id="88b71-104">The .NET API Analyzer is a Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span> <span data-ttu-id="88b71-105">Pode ser útil para todos os desenvolvedores de C# em qualquer estágio do desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="88b71-105">It can be useful for all C# developers at any stage of development.</span></span>

<span data-ttu-id="88b71-106">O Analisador de API é fornecido como um pacote NuGet [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span><span class="sxs-lookup"><span data-stu-id="88b71-106">API Analyzer comes as a NuGet package [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span></span> <span data-ttu-id="88b71-107">Depois que você faz referência a ele em um projeto, ele automaticamente monitora o código e indica um problema de uso de API.</span><span class="sxs-lookup"><span data-stu-id="88b71-107">After you reference it in a project, it automatically monitors the code and indicates problematic API usage.</span></span> <span data-ttu-id="88b71-108">Você também pode obter sugestões sobre possíveis correções clicando na lâmpada.</span><span class="sxs-lookup"><span data-stu-id="88b71-108">You can also get suggestions on possible fixes by clicking on the light bulb.</span></span> <span data-ttu-id="88b71-109">O menu suspenso inclui uma opção para suprimir os avisos.</span><span class="sxs-lookup"><span data-stu-id="88b71-109">The drop-down menu includes an option to suppress the warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="88b71-110">O analisador do .NET API ainda é uma versão de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="88b71-110">The .NET API analyzer is still a pre-release version.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="88b71-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="88b71-111">Prerequisites</span></span>

- <span data-ttu-id="88b71-112">Visual Studio 2017 e versões posteriores ou Visual Studio para Mac (todas as versões).</span><span class="sxs-lookup"><span data-stu-id="88b71-112">Visual Studio 2017 and later versions, or Visual Studio for Mac (all versions).</span></span>

## <a name="discovering-deprecated-apis"></a><span data-ttu-id="88b71-113">Descobrindo APIs preteridas</span><span class="sxs-lookup"><span data-stu-id="88b71-113">Discovering deprecated APIs</span></span>

### <a name="what-are-deprecated-apis"></a><span data-ttu-id="88b71-114">Quais são as APIs preteridas?</span><span class="sxs-lookup"><span data-stu-id="88b71-114">What are deprecated APIs?</span></span>

<span data-ttu-id="88b71-115">A família .NET é um conjunto de produtos grandes que são atualizados constantemente para atender melhor às necessidades dos clientes.</span><span class="sxs-lookup"><span data-stu-id="88b71-115">The .NET family is a set of large products that are constantly upgraded to better serve customer needs.</span></span> <span data-ttu-id="88b71-116">É natural substituir algumas APIs e substituí-las por novas.</span><span class="sxs-lookup"><span data-stu-id="88b71-116">It's natural to deprecate some APIs and replace them with new ones.</span></span> <span data-ttu-id="88b71-117">Uma API é considerada preterida quando existe uma alternativa melhor.</span><span class="sxs-lookup"><span data-stu-id="88b71-117">An API is considered deprecated when a better alternative exists.</span></span> <span data-ttu-id="88b71-118">Uma maneira de informar que uma API foi preterida e não deve ser usada é marcá-la com o atributo <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="88b71-118">One way to inform that an API is deprecated and shouldn't be used is to mark it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="88b71-119">A desvantagem dessa abordagem é que há apenas uma ID de diagnóstico para todas as APIs preteridas (para C#, [CS0612](../../csharp/misc/cs0612.md)).</span><span class="sxs-lookup"><span data-stu-id="88b71-119">The disadvantage of this approach is that there is only one diagnostic ID for all obsolete APIs (for C#, [CS0612](../../csharp/misc/cs0612.md)).</span></span> <span data-ttu-id="88b71-120">Isso significa que:</span><span class="sxs-lookup"><span data-stu-id="88b71-120">This means that:</span></span>

- <span data-ttu-id="88b71-121">É impossível ter documentos dedicados para cada caso.</span><span class="sxs-lookup"><span data-stu-id="88b71-121">It's impossible to have dedicated documents for each case.</span></span>
- <span data-ttu-id="88b71-122">É impossível suprimir determinada categoria de avisos.</span><span class="sxs-lookup"><span data-stu-id="88b71-122">It's impossible to suppress certain category of warnings.</span></span> <span data-ttu-id="88b71-123">Você pode suprimir todos ou nenhum deles.</span><span class="sxs-lookup"><span data-stu-id="88b71-123">You can suppress either all or none of them.</span></span>
- <span data-ttu-id="88b71-124">Para informar os usuários de uma nova preterição, um assembly referenciado ou um pacote de direcionamento deve ser atualizado.</span><span class="sxs-lookup"><span data-stu-id="88b71-124">To inform users of a new deprecation, a referenced assembly or targeting package has to be updated.</span></span>

<span data-ttu-id="88b71-125">O Analisador de API usa códigos de erro específicos de API que começam com DE (que representa Erro de Preterição), o que permite controlar a exibição de avisos individuais.</span><span class="sxs-lookup"><span data-stu-id="88b71-125">The API Analyzer uses API-specific error codes that begin with DE (which stands for Deprecation Error), which allows control over the display of individual warnings.</span></span> <span data-ttu-id="88b71-126">As APIs preteridas identificadas pelo analisador são definidas no repositório [dotnet/platform-compat](https://github.com/dotnet/platform-compat).</span><span class="sxs-lookup"><span data-stu-id="88b71-126">The deprecated APIs identified by the analyzer are defined in the [dotnet/platform-compat](https://github.com/dotnet/platform-compat) repo.</span></span>

### <a name="using-the-api-analyzer"></a><span data-ttu-id="88b71-127">Como usar o analisador de API</span><span class="sxs-lookup"><span data-stu-id="88b71-127">Using the API Analyzer</span></span>

<span data-ttu-id="88b71-128">Quando uma API preterida, como <xref:System.Net.WebClient>, é usada em um código, o Analisador de API a realça com uma linha irregular verde.</span><span class="sxs-lookup"><span data-stu-id="88b71-128">When a deprecated API, such as <xref:System.Net.WebClient>, is used in a code, API Analyzer highlights it with a green squiggly line.</span></span> <span data-ttu-id="88b71-129">Quando você focaliza a chamada de API, uma lâmpada é exibida com informações sobre a substituição de API, como no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="88b71-129">When you hover over the API call, a light bulb is displayed with information about the API deprecation, as in the following example:</span></span>

!["Captura de tela da API WebClient com linha irregular verde e lâmpada à esquerda"](media/api-analyzer/green-squiggle.jpg)

<span data-ttu-id="88b71-131">A janela **Lista de Erros** contém avisos com uma ID exclusiva por API preterida, conforme mostrado no seguinte exemplo (`DE004`):</span><span class="sxs-lookup"><span data-stu-id="88b71-131">The **Error List** window contains warnings with a unique ID per deprecated API, as shown in the following example (`DE004`):</span></span> 

<span data-ttu-id="88b71-132">!["Captura de tela da janela Lista de Erros mostrando a ID e a descrição do aviso"](media/api-analyzer/warnings-id-and-descriptions.jpg "Janela Lista de Erros, que inclui avisos.")</span><span class="sxs-lookup"><span data-stu-id="88b71-132">!["Screenshot of the Error List window showing warning's ID and description"](media/api-analyzer/warnings-id-and-descriptions.jpg "Error List window that includes warnings.")</span></span>

<span data-ttu-id="88b71-133">Clicando na ID, você vai para uma página da Web com informações detalhadas sobre por que a API foi preterida e sugestões sobre APIs alternativas que podem ser usadas.</span><span class="sxs-lookup"><span data-stu-id="88b71-133">By clicking on the ID, you go to a webpage with detailed information about why the API was deprecated and suggestions regarding alternative APIs that can be used.</span></span>

<span data-ttu-id="88b71-134">Os avisos podem ser suprimidos clicando com o botão direito do mouse no membro realçado e selecionando **Suprimir \<ID de diagnóstico>** .</span><span class="sxs-lookup"><span data-stu-id="88b71-134">Any warnings can be suppressed by right-clicking on the highlighted member and selecting **Suppress \<diagnostic ID>**.</span></span> <span data-ttu-id="88b71-135">Há duas maneiras de suprimir avisos:</span><span class="sxs-lookup"><span data-stu-id="88b71-135">There are two ways to suppress warnings:</span></span> 

- [<span data-ttu-id="88b71-136">localmente (no código-fonte)</span><span class="sxs-lookup"><span data-stu-id="88b71-136">locally (in source)</span></span>](#suppressing-warnings-locally)
- <span data-ttu-id="88b71-137">[globalmente (em um arquivo de supressão)](#suppressing-warnings-globally) ‒ recomendado</span><span class="sxs-lookup"><span data-stu-id="88b71-137">[globally (in a suppression file)](#suppressing-warnings-globally) - recommended</span></span>

### <a name="suppressing-warnings-locally"></a><span data-ttu-id="88b71-138">Como suprimir avisos localmente</span><span class="sxs-lookup"><span data-stu-id="88b71-138">Suppressing warnings locally</span></span>

<span data-ttu-id="88b71-139">Para suprimir avisos localmente, clique no membro para o qual você deseja suprimir avisos e selecione **Ações Rápidas e Refatorações** > **Suprimir *ID de diagnóstico* \<ID de diagnóstico >**  > **na Fonte**.</span><span class="sxs-lookup"><span data-stu-id="88b71-139">To suppress warnings locally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Source**.</span></span> <span data-ttu-id="88b71-140">A diretiva de pré-processador de aviso [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) é adicionada ao código-fonte no escopo definido: !["Captura de tela do código enquadrado com o aviso #pragma desabilitado"](media/api-analyzer/suppress-in-source.jpg)</span><span class="sxs-lookup"><span data-stu-id="88b71-140">The [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) warning preprocessor directive is added to your source code in the scope defined: !["Screenshot of code framed with #pragma warning disable"](media/api-analyzer/suppress-in-source.jpg)</span></span>

### <a name="suppressing-warnings-globally"></a><span data-ttu-id="88b71-141">Como suprimir avisos globalmente</span><span class="sxs-lookup"><span data-stu-id="88b71-141">Suppressing warnings globally</span></span>

<span data-ttu-id="88b71-142">Para suprimir avisos globalmente, clique no membro para o qual você deseja suprimir avisos e selecione **Ações Rápidas e Refatorações** > **Suprimir *ID de diagnóstico*\<ID de diagnóstico >**  > **no Arquivo de Supressão**.</span><span class="sxs-lookup"><span data-stu-id="88b71-142">To suppress warnings globally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Suppression File**.</span></span>

!["Captura de tela da API WebClient com linha irregular verde e lâmpada à esquerda"](media/api-analyzer/suppress-in-sup-file.jpg)

<span data-ttu-id="88b71-144">Um arquivo *GlobalSuppressions.cs* é adicionado ao projeto após a primeira supressão.</span><span class="sxs-lookup"><span data-stu-id="88b71-144">A *GlobalSuppressions.cs* file is added to your project after the first suppression.</span></span> <span data-ttu-id="88b71-145">Novo supressões globais são anexadas a este arquivo.</span><span class="sxs-lookup"><span data-stu-id="88b71-145">New global suppressions are appended to this file.</span></span>

!["Captura de tela da API WebClient com linha irregular verde e lâmpada à esquerda"](media/api-analyzer/suppression-file.jpg)

<span data-ttu-id="88b71-147">A supressão global é a maneira recomendada de garantir a consistência do uso da API em projetos.</span><span class="sxs-lookup"><span data-stu-id="88b71-147">Global suppression is the recommended way to ensure consistency of API usage across projects.</span></span>

## <a name="discovering-cross-platform-issues"></a><span data-ttu-id="88b71-148">Detectando problemas entre plataformas</span><span class="sxs-lookup"><span data-stu-id="88b71-148">Discovering cross-platform issues</span></span>

<span data-ttu-id="88b71-149">De forma semelhante a APIs preteridas, o analisador identifica todas as APIs que não são entre plataformas.</span><span class="sxs-lookup"><span data-stu-id="88b71-149">Similar to deprecated APIs, the analyzer identifies all APIs that are not cross-platform.</span></span> <span data-ttu-id="88b71-150">Por exemplo, <xref:System.Console.WindowWidth?displayProperty=nameWithType> funciona no Windows, mas não no Linux ou no macOS.</span><span class="sxs-lookup"><span data-stu-id="88b71-150">For example, <xref:System.Console.WindowWidth?displayProperty=nameWithType> works on Windows but not on Linux and macOS.</span></span> <span data-ttu-id="88b71-151">A ID de diagnóstico é mostrada na janela **Lista de Erros**.</span><span class="sxs-lookup"><span data-stu-id="88b71-151">The diagnostic ID is shown in the **Error List** window.</span></span> <span data-ttu-id="88b71-152">Você pode suprimir esse aviso clicando e selecionando **Ações Rápidas e Refatorações**.</span><span class="sxs-lookup"><span data-stu-id="88b71-152">You can suppress that warning by right-clicking and selecting **Quick Actions and Refactorings**.</span></span> <span data-ttu-id="88b71-153">Diferentemente de casos de preterição em que você tem duas opções (continuar usando o membro preterido e suprimir avisos ou não o utilizar), aqui, se estiver desenvolvendo o código apenas para algumas plataformas, você poderá suprimir todos os avisos para todas as outras plataformas em que não planejar executar o código.</span><span class="sxs-lookup"><span data-stu-id="88b71-153">Unlike deprecation cases where you have two options (either keep using the deprecated member and suppress warnings or not use it at all), here if you're developing your code only for certain platforms, you can suppress all warnings for all other platforms you don't plan to run your code on.</span></span> <span data-ttu-id="88b71-154">Para fazer isso, basta editar o arquivo de projeto e adicionar a propriedade `PlatformCompatIgnore` que lista todas as plataformas a serem ignoradas.</span><span class="sxs-lookup"><span data-stu-id="88b71-154">To do so, you just need to edit your project file and add the `PlatformCompatIgnore` property that lists all platforms to be ignored.</span></span> <span data-ttu-id="88b71-155">Os valores aceitos são: `Linux`, `macOS` e `Windows`.</span><span class="sxs-lookup"><span data-stu-id="88b71-155">The accepted values are: `Linux`, `macOS`, and `Windows`.</span></span>

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

<span data-ttu-id="88b71-156">Se o código for voltado para várias plataformas e você desejar aproveitar uma API que não tem suporte em algumas delas, poderá proteger essa parte do código com uma instrução `if`:</span><span class="sxs-lookup"><span data-stu-id="88b71-156">If your code targets multiple platforms and you want to take advantage of an API not supported on some of them, you can guard that part of the code with an `if` statement:</span></span>

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

<span data-ttu-id="88b71-157">Você também pode compilar condicionalmente por estrutura/sistema operacional de destino, mas, no momento, precisa fazer isso [manualmente](../frameworks.md#how-to-specify-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="88b71-157">You can also conditionally compile per target framework/operating system, but you currently need to do that [manually](../frameworks.md#how-to-specify-target-frameworks).</span></span>

## <a name="supported-diagnostics"></a><span data-ttu-id="88b71-158">Diagnóstico com suporte</span><span class="sxs-lookup"><span data-stu-id="88b71-158">Supported diagnostics</span></span>

<span data-ttu-id="88b71-159">Atualmente, o analisador trata dos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="88b71-159">Currently, the analyzer handles the following cases:</span></span>

- <span data-ttu-id="88b71-160">Uso de uma API padrão do .NET que gera <xref:System.PlatformNotSupportedException> (PC001).</span><span class="sxs-lookup"><span data-stu-id="88b71-160">Usage of a .NET Standard API that throws <xref:System.PlatformNotSupportedException> (PC001).</span></span>
- <span data-ttu-id="88b71-161">Uso de uma API padrão do .NET que não está disponível no .NET Framework 4.6.1 (PC002).</span><span class="sxs-lookup"><span data-stu-id="88b71-161">Usage of a .NET Standard API that isn't available on the .NET Framework 4.6.1 (PC002).</span></span>
- <span data-ttu-id="88b71-162">Uso de uma API nativa que não existe no UWP (PC003).</span><span class="sxs-lookup"><span data-stu-id="88b71-162">Usage of a native API that doesn’t exist in UWP (PC003).</span></span>
- <span data-ttu-id="88b71-163">Uso das APIs Delegate.BeginInvoke e EndInvoke (PC004).</span><span class="sxs-lookup"><span data-stu-id="88b71-163">Usage of Delegate.BeginInvoke and EndInvoke APIs (PC004).</span></span>
- <span data-ttu-id="88b71-164">Uso de uma API que está marcada como preterida (DEXXXX).</span><span class="sxs-lookup"><span data-stu-id="88b71-164">Usage of an API that is marked as deprecated (DEXXXX).</span></span>

## <a name="ci-machine"></a><span data-ttu-id="88b71-165">Máquina de CI</span><span class="sxs-lookup"><span data-stu-id="88b71-165">CI machine</span></span>

<span data-ttu-id="88b71-166">Todos esses diagnósticos estão disponíveis não só no IDE, mas também na linha de comando, como parte da criação do projeto, o que inclui o servidor de CI.</span><span class="sxs-lookup"><span data-stu-id="88b71-166">All these diagnostics are available not only in the IDE, but also on the command line as part of building your project, which includes the CI server.</span></span>

## <a name="configuration"></a><span data-ttu-id="88b71-167">Configuração</span><span class="sxs-lookup"><span data-stu-id="88b71-167">Configuration</span></span>

<span data-ttu-id="88b71-168">O usuário decide como o diagnóstico deve ser tratado: como avisos, erros, sugestões ou ser desligado.</span><span class="sxs-lookup"><span data-stu-id="88b71-168">The user decides how the diagnostics should be treated: as warnings, errors, suggestions, or to be turned off.</span></span> <span data-ttu-id="88b71-169">Por exemplo, como arquiteto, você pode decidir que problemas de compatibilidade devem ser tratados como erros, chamadas a algumas APIs preteridas geram avisos, enquanto outras só geram sugestões.</span><span class="sxs-lookup"><span data-stu-id="88b71-169">For example, as an architect, you can decide that compatibility issues should be treated as errors, calls to some deprecated APIs generate warnings, while others only generate suggestions.</span></span> <span data-ttu-id="88b71-170">Você pode configurar isso separadamente por ID de diagnóstico e por projeto.</span><span class="sxs-lookup"><span data-stu-id="88b71-170">You can configure this separately by diagnostic ID and by project.</span></span> <span data-ttu-id="88b71-171">Para fazer isso no **Gerenciador de Soluções**, navegue até o nó **Dependências** em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="88b71-171">To do so in **Solution Explorer**, navigate to the **Dependencies** node under your project.</span></span> <span data-ttu-id="88b71-172">Expanda os nós**Dependencies** > **Analyzers** > **Microsoft.DotNet.Analyzers.Compatibility**.</span><span class="sxs-lookup"><span data-stu-id="88b71-172">Expand the nodes **Dependencies** > **Analyzers** > **Microsoft.DotNet.Analyzers.Compatibility**.</span></span> <span data-ttu-id="88b71-173">Clique com o botão direito do mouse na ID de diagnóstico, selecione **Definir Severidade de Conjunto de Regras** e selecione a opção desejada.</span><span class="sxs-lookup"><span data-stu-id="88b71-173">Right click on the diagnostic ID, select **Set Rule Set Severity** and pick the desired option.</span></span>

!["Captura de tela do Gerenciador de Soluções mostrando o diagnóstico e a caixa de diálogo pop-up com Severidade de Conjunto de Regras"](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a><span data-ttu-id="88b71-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88b71-175">See also</span></span>

- <span data-ttu-id="88b71-176">Postagem de blog [Introduzindo o analisador de API](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/).</span><span class="sxs-lookup"><span data-stu-id="88b71-176">[Introducing API Analyzer](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) blog post.</span></span>
- <span data-ttu-id="88b71-177">Vídeo de demonstração no YouTube [Analisador de API](https://youtu.be/eeBEahYXGd0).</span><span class="sxs-lookup"><span data-stu-id="88b71-177">[API Analyzer](https://youtu.be/eeBEahYXGd0) demo video on YouTube.</span></span>
