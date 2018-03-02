---
title: 'Os analisadores do Roslyn: .NET'
description: "Saiba mais sobre os analisadores do Roslyn que localizam problemas e sugerem correções."
keywords: .NET, .NET Core
author: billwagner
ms.author: billwagner
ms.date: 01/24/2018
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.openlocfilehash: 8c6524716ba403bc426df8dc33e64b8b2934d3d7
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2018
---
# <a name="the-roslyn-based-analyzers"></a><span data-ttu-id="fdae2-104">Os analisadores do Roslyn</span><span class="sxs-lookup"><span data-stu-id="fdae2-104">The Roslyn based Analyzers</span></span>

<span data-ttu-id="fdae2-105">Os analisadores do Roslyn usam o .NET Compiler SDK (APIs do Roslyn) para analisar o código-fonte do seu projeto para localizar problemas e sugerir correções.</span><span class="sxs-lookup"><span data-stu-id="fdae2-105">Roslyn-based analyzers use the .NET Compiler SDK (Roslyn APIs) to analyze your project's source code to find issues and suggest corrections.</span></span> <span data-ttu-id="fdae2-106">Analisadores diferentes procuram diferentes classes de problemas, variando de práticas que podem causar erros a problemas de segurança à compatibilidade da API.</span><span class="sxs-lookup"><span data-stu-id="fdae2-106">Different analyzers look for different classes of issues, ranging from practices that are likely to cause bugs to security concerns to API compatibility.</span></span>

<span data-ttu-id="fdae2-107">Os analisadores do Roslyn trabalham tanto interativamente quanto durante as compilações.</span><span class="sxs-lookup"><span data-stu-id="fdae2-107">Roslyn-based analyzers work both interactively and during builds.</span></span> <span data-ttu-id="fdae2-108">O analisador fornece uma orientações diferentes no Visual Studio ou em compilações da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="fdae2-108">The analyzer provides different guidance when in Visual Studio or in command-line builds.</span></span>

<span data-ttu-id="fdae2-109">Embora você edite códigos no Visual Studio, os analisadores são executados enquanto você faz alterações, capturando possíveis problemas assim que você cria um código que aciona problemas.</span><span class="sxs-lookup"><span data-stu-id="fdae2-109">While you edit code in Visual Studio, the analyzers run as you make changes, catching possible issues as soon as you create code that trigger concerns.</span></span> <span data-ttu-id="fdae2-110">Os problemas são destacados com linhas onduladas abaixo deles.</span><span class="sxs-lookup"><span data-stu-id="fdae2-110">Any issues are highlighted with squiggles under any issue.</span></span> <span data-ttu-id="fdae2-111">O Visual Studio exibe uma lâmpada. Quando você clica nela, o analisador sugere soluções possíveis para o problema.</span><span class="sxs-lookup"><span data-stu-id="fdae2-111">Visual Studio displays a light bulb, and when you click on it the analyzer will suggest possible fixes for that issue.</span></span> <span data-ttu-id="fdae2-112">Quando você compila o projeto, no Visual Studio ou na linha de comando, o código-fonte é analisado, e o analisador fornece uma lista completa de possíveis problemas.</span><span class="sxs-lookup"><span data-stu-id="fdae2-112">When you build the project, either in Visual Studio or from the command line, all the source code is analyzed and the analyzer provides a full list of potential issues.</span></span> <span data-ttu-id="fdae2-113">A imagem a seguir mostra um exemplo.</span><span class="sxs-lookup"><span data-stu-id="fdae2-113">The following figure shows one example.</span></span>

![problemas relatados pelo analisador de estrutura](./media/framework-analyzers-2.png)

<span data-ttu-id="fdae2-115">Os analisadores do Roslyn relatam problemas potenciais como erros, avisos ou informações com base na gravidade do problema.</span><span class="sxs-lookup"><span data-stu-id="fdae2-115">Roslyn-based analyzers report potential issues as errors, warnings, or information based on the severity of the issue.</span></span>

<span data-ttu-id="fdae2-116">É possível instalar os analisadores do Roslyn como pacotes NuGet no projeto.</span><span class="sxs-lookup"><span data-stu-id="fdae2-116">You install Roslyn-based analyzers as NuGet packages in your project.</span></span> <span data-ttu-id="fdae2-117">Os analisadores configurados e qualquer configuração para cada analisador são restaurados e executados no computador de qualquer desenvolvedor para o projeto.</span><span class="sxs-lookup"><span data-stu-id="fdae2-117">The configured analyzers and any settings for each analyzer are restored and run on any developer's machine for that project.</span></span>

> [!NOTE]
> <span data-ttu-id="fdae2-118">A experiência do usuário com os analisadores do Roslyn é diferente da experiência com as bibliotecas de análise de código, como as versões mais antigas do FxCop e as ferramentas de análise de segurança.</span><span class="sxs-lookup"><span data-stu-id="fdae2-118">The user experience for Roslyn-based analyzers is different than that of the Code Analysis libraries like the older versions of FxCop and the security analysis tools.</span></span>  <span data-ttu-id="fdae2-119">Você não precisa executar explicitamente os analisadores do Roslyn.</span><span class="sxs-lookup"><span data-stu-id="fdae2-119">You don't need to explicitly run the Roslyn-based analyzers.</span></span> <span data-ttu-id="fdae2-120">Não é necessário usar os itens de menu "Executar análise de código" no menu "Analisar" do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fdae2-120">There's no need to use the "Run Code Analysis" menu items on the "Analyze" menu in Visual Studio.</span></span> <span data-ttu-id="fdae2-121">Os analisadores do Roslyn executam de forma assíncrona enquanto você trabalha.</span><span class="sxs-lookup"><span data-stu-id="fdae2-121">Roslyn-based analyzers run asychronously as you work.</span></span> 

## <a name="more-information-on-specific-analyzers"></a><span data-ttu-id="fdae2-122">Mais informações sobre analisadores específicos</span><span class="sxs-lookup"><span data-stu-id="fdae2-122">More information on specific analyzers</span></span>

<span data-ttu-id="fdae2-123">Os analisadores a seguir são abordados nesta seção:</span><span class="sxs-lookup"><span data-stu-id="fdae2-123">The following analyzers are covered in this section:</span></span>

<span data-ttu-id="fdae2-124">[Analisador de API](api-analyzer.md): este analisador verifica se há em seu código possíveis riscos de compatibilidade ou usos de APIs obsoletas.</span><span class="sxs-lookup"><span data-stu-id="fdae2-124">[API Analyzer](api-analyzer.md): This analyzer examines your code for potential compatibility risks or uses of deprecated APIs.</span></span>    
<span data-ttu-id="fdae2-125">[Analisador de estrutura](framework-analyzer.md): este analisador examina seu código para garantir que ele segue as diretrizes dos aplicativos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fdae2-125">[Framework Analyzer](framework-analyzer.md): This analyzer examines your code to ensure it follows the guidelines for .NET Framework applications.</span></span> <span data-ttu-id="fdae2-126">Essas regras incluem várias recomendações com base em segurança.</span><span class="sxs-lookup"><span data-stu-id="fdae2-126">These rules include several security-based recommendations.</span></span>
