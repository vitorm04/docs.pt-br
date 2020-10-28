---
title: Analisadores de código para .NET Framework
titleSuffix: ''
description: Saiba como usar os analisadores no pacote .NET Framework analisadores para encontrar e resolver problemas em seu código.
author: billwagner
ms.author: wiwagn
ms.date: 10/23/2020
ms.openlocfilehash: 69dfbc9f9645c7f602ffbce46308b241c119fd96
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687815"
---
# <a name="code-analysis"></a><span data-ttu-id="826d9-103">Análise de código</span><span class="sxs-lookup"><span data-stu-id="826d9-103">Code analysis</span></span>

<span data-ttu-id="826d9-104">Você pode usar analisadores de código para encontrar possíveis problemas em seu .NET Framework código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="826d9-104">You can use code analyzers to find potential issues in your .NET Framework application code.</span></span> <span data-ttu-id="826d9-105">Os analisadores encontram possíveis problemas e sugerem correções para eles.</span><span class="sxs-lookup"><span data-stu-id="826d9-105">The analyzers find potential issues and suggest fixes for them.</span></span>

<span data-ttu-id="826d9-106">Os analisadores de código baseados em Roslyn são executados interativamente no Visual Studio à medida que você escreve seu código ou como parte de uma compilação de CI.</span><span class="sxs-lookup"><span data-stu-id="826d9-106">Roslyn-based code analyzers run interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="826d9-107">Você deve adicionar os analisadores ao seu projeto o mais cedo possível no ciclo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="826d9-107">You should add the analyzers to your project as early as possible in the development cycle.</span></span> <span data-ttu-id="826d9-108">Quanto antes você encontrar potenciais problemas no seu código, mais fácil será corrigi-los.</span><span class="sxs-lookup"><span data-stu-id="826d9-108">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="826d9-109">Os analisadores sinalizam problemas no código existente e avisam sobre novos problemas à medida que você continua o desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="826d9-109">The analyzers flag issues in existing code and warn about new issues as you continue development.</span></span>

## <a name="install-and-configure-analyzers"></a><span data-ttu-id="826d9-110">Instalar e configurar analisadores</span><span class="sxs-lookup"><span data-stu-id="826d9-110">Install and configure analyzers</span></span>

<span data-ttu-id="826d9-111">O Analisador do .NET Framework é fornecido no pacote do NuGet [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/).</span><span class="sxs-lookup"><span data-stu-id="826d9-111">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="826d9-112">Este pacote fornece analisadores específicos para .NET Framework APIs, que incluem analisadores de segurança.</span><span class="sxs-lookup"><span data-stu-id="826d9-112">This package provides analyzers that are specific to .NET Framework APIs, which includes security analyzers.</span></span> <span data-ttu-id="826d9-113">O pacote está incluído no [pacote Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), portanto, se você instalar esse pacote, não será necessário instalar os analisadores de .NET Framework separadamente.</span><span class="sxs-lookup"><span data-stu-id="826d9-113">The package is included with the [Microsoft.CodeAnalysis.FxCopAnalyzers package](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), so if you install that package, there's no need to install the .NET Framework analyzers separately.</span></span>

<span data-ttu-id="826d9-114">Instale o pacote NuGet em todos os projetos em que você deseja que os analisadores sejam executados.</span><span class="sxs-lookup"><span data-stu-id="826d9-114">Install the NuGet package on every project where you want the analyzers to run.</span></span> <span data-ttu-id="826d9-115">Somente um desenvolvedor precisa adicioná-los ao projeto.</span><span class="sxs-lookup"><span data-stu-id="826d9-115">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="826d9-116">O pacote de analisador é uma dependência de projeto e será executado no computador de cada um dos desenvolvedores assim que ele tiver a solução atualizada.</span><span class="sxs-lookup"><span data-stu-id="826d9-116">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="826d9-117">Para instalar o pacote, clique com o botão direito do mouse no projeto e selecione "gerenciar dependências".</span><span class="sxs-lookup"><span data-stu-id="826d9-117">To install the package, right-click on the project, and select "Manage Dependencies".</span></span> <span data-ttu-id="826d9-118">No Gerenciador do NuGet, pesquise por "Microsoft. NetFramework. Analyzers".</span><span class="sxs-lookup"><span data-stu-id="826d9-118">From the NuGet explorer, search for "Microsoft.NetFramework.Analyzers".</span></span> <span data-ttu-id="826d9-119">Instale a versão estável mais recente em todos os projetos na solução.</span><span class="sxs-lookup"><span data-stu-id="826d9-119">Install the latest stable version in all projects in your solution.</span></span>

## <a name="use-the-analyzers"></a><span data-ttu-id="826d9-120">Usar os analisadores</span><span class="sxs-lookup"><span data-stu-id="826d9-120">Use the analyzers</span></span>

<span data-ttu-id="826d9-121">Depois de instalar o pacote do NuGet, compile a solução.</span><span class="sxs-lookup"><span data-stu-id="826d9-121">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="826d9-122">O analisador relatará eventuais problemas que ele localize na base de código.</span><span class="sxs-lookup"><span data-stu-id="826d9-122">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="826d9-123">Os problemas são relatados como avisos na janela Lista de Erros do Visual Studio, conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="826d9-123">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![Problemas relatados por .NET Framework analisadores.](./media/framework-analyzers-2.png)

<span data-ttu-id="826d9-125">Ao escrever código, você vê linhas onduladas sob qualquer problema potencial existente nele.</span><span class="sxs-lookup"><span data-stu-id="826d9-125">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="826d9-126">Passe o mouse sobre qualquer problema para obter mais informações e veja sugestões para qualquer correção possível, conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="826d9-126">Hover over any issue to get more information and see suggestions for any possible fix, as shown in the following image:</span></span>

![Relatório interativo de problemas encontrados por analisadores de código.](./media/framework-analyzers-1.png)

<span data-ttu-id="826d9-128">Para obter mais informações, consulte [análise de código no Visual Studio](/visualstudio/code-quality/roslyn-analyzers-overview).</span><span class="sxs-lookup"><span data-stu-id="826d9-128">For more information, see [Code analysis in Visual Studio](/visualstudio/code-quality/roslyn-analyzers-overview).</span></span>

## <a name="types-of-rules"></a><span data-ttu-id="826d9-129">Tipos de regras</span><span class="sxs-lookup"><span data-stu-id="826d9-129">Types of rules</span></span>

<span data-ttu-id="826d9-130">Os analisadores examinam o código em sua solução e os avisos de superfície com um `CA` prefixo.</span><span class="sxs-lookup"><span data-stu-id="826d9-130">The analyzers examine the code in your solution and surface warnings with a `CA` prefix.</span></span> <span data-ttu-id="826d9-131">Para obter uma lista de todos os avisos possíveis, consulte [regras de qualidade de código](../fundamentals/code-analysis/quality-rules/index.md).</span><span class="sxs-lookup"><span data-stu-id="826d9-131">For a list of all possible warnings, see [Code quality rules](../fundamentals/code-analysis/quality-rules/index.md).</span></span> <span data-ttu-id="826d9-132">Somente alguns desses avisos se aplicam a APIS .NET Framework, incluindo:</span><span class="sxs-lookup"><span data-stu-id="826d9-132">Only some of these warnings apply to .NET Framework APIS, including:</span></span>

- [<span data-ttu-id="826d9-133">CA1058: Tipos não devem estender determinados tipos base</span><span class="sxs-lookup"><span data-stu-id="826d9-133">CA1058: Types should not extend certain base types</span></span>](../fundamentals/code-analysis/quality-rules/ca1058.md)

- [<span data-ttu-id="826d9-134">CA2153: não capturar exceções de estado corrompido</span><span class="sxs-lookup"><span data-stu-id="826d9-134">CA2153: Do not catch corrupted state exceptions</span></span>](../fundamentals/code-analysis/quality-rules/ca2153.md)

- [<span data-ttu-id="826d9-135">CA2229: Implementar construtores de serialização</span><span class="sxs-lookup"><span data-stu-id="826d9-135">CA2229: Implement serialization constructors</span></span>](../fundamentals/code-analysis/quality-rules/ca2229.md)

- [<span data-ttu-id="826d9-136">CA2235: Marcar todos os campos não serializáveis</span><span class="sxs-lookup"><span data-stu-id="826d9-136">CA2235: Mark all non-serializable fields</span></span>](../fundamentals/code-analysis/quality-rules/ca2235.md)

- [<span data-ttu-id="826d9-137">CA2237: marcar tipos ISerializable com serializable</span><span class="sxs-lookup"><span data-stu-id="826d9-137">CA2237: Mark ISerializable types with serializable</span></span>](../fundamentals/code-analysis/quality-rules/ca2237.md)

- [<span data-ttu-id="826d9-138">CA3075: processamento de DTD inseguro em XML</span><span class="sxs-lookup"><span data-stu-id="826d9-138">CA3075: Insecure DTD processing in XML</span></span>](../fundamentals/code-analysis/quality-rules/ca3075.md)

- [<span data-ttu-id="826d9-139">CA5350: não use algoritmos de criptografia fracos</span><span class="sxs-lookup"><span data-stu-id="826d9-139">CA5350: Do not use weak cryptographic algorithms</span></span>](../fundamentals/code-analysis/quality-rules/ca5350.md)

- [<span data-ttu-id="826d9-140">CA5351 não usam algoritmos de criptografia desfeitos</span><span class="sxs-lookup"><span data-stu-id="826d9-140">CA5351 Do not use broken cryptographic algorithms</span></span>](../fundamentals/code-analysis/quality-rules/ca5351.md)

## <a name="see-also"></a><span data-ttu-id="826d9-141">Veja também</span><span class="sxs-lookup"><span data-stu-id="826d9-141">See also</span></span>

- [<span data-ttu-id="826d9-142">Análise de código no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="826d9-142">Code analysis in Visual Studio</span></span>](/visualstudio/code-quality/roslyn-analyzers-overview)
- [<span data-ttu-id="826d9-143">Análise de código no SDK do .NET</span><span class="sxs-lookup"><span data-stu-id="826d9-143">Code analysis in the .NET SDK</span></span>](../fundamentals/code-analysis/overview.md)
