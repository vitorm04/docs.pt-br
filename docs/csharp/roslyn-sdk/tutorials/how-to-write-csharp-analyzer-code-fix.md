---
title: 'Tutorial: escrever seu primeiro analisador e correção de código'
description: Este tutorial fornece instruções passo a passo para criar um analisador e correção de código usando o SDK do .NET Compiler (APIs do Roslyn).
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: 7bd0fda9fb717a48c09aafde47f9b7f4f360c357
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837045"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a><span data-ttu-id="8e43b-103">Tutorial: escrever seu primeiro analisador e correção de código</span><span class="sxs-lookup"><span data-stu-id="8e43b-103">Tutorial: Write your first analyzer and code fix</span></span>

<span data-ttu-id="8e43b-104">O SDK da .NET Compiler Platform fornece as ferramentas necessárias para criar avisos personalizados destinados ao C# ou código do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8e43b-104">The .NET Compiler Platform SDK provides the tools you need to create custom warnings that target C# or Visual Basic code.</span></span> <span data-ttu-id="8e43b-105">Seu **analisador** contém código que reconhece as violações da sua regra.</span><span class="sxs-lookup"><span data-stu-id="8e43b-105">Your **analyzer** contains code that recognizes violations of your rule.</span></span> <span data-ttu-id="8e43b-106">Sua **correção de código** contém o código que corrige a violação.</span><span class="sxs-lookup"><span data-stu-id="8e43b-106">Your **code fix** contains the code that fixes the violation.</span></span> <span data-ttu-id="8e43b-107">As regras que você implementar podem ser qualquer coisa, incluindo estrutura do código, estilo de codificação, convenções de nomenclatura e muito mais.</span><span class="sxs-lookup"><span data-stu-id="8e43b-107">The rules you implement can be anything from code structure to coding style to naming conventions and more.</span></span> <span data-ttu-id="8e43b-108">O .NET Compiler Platform fornece a estrutura para executar análise conforme os desenvolvedores escrevem o código, bem como todos os recursos de interface do usuário do Visual Studio para corrigir o código: mostrar rabiscos no editor, popular a Lista de Erros do Visual Studio, criar as sugestões da "lâmpada" e mostrar a visualização avançada das correções sugeridas.</span><span class="sxs-lookup"><span data-stu-id="8e43b-108">The .NET Compiler Platform provides the framework for running analysis as developers are writing code, and all the Visual Studio UI features for fixing code: showing squiggles in the editor, populating the Visual Studio Error List, creating the "light bulb" suggestions and showing the rich preview of the suggested fixes.</span></span>

<span data-ttu-id="8e43b-109">Neste tutorial, você explorará a criação de um **analisador** e uma **correção de código** que o acompanha, usando as APIs do Roslyn.</span><span class="sxs-lookup"><span data-stu-id="8e43b-109">In this tutorial, you'll explore the creation of an **analyzer** and an accompanying **code fix** using the Roslyn APIs.</span></span> <span data-ttu-id="8e43b-110">Um analisador é uma maneira de executar a análise de código-fonte e relatar um problema para o usuário.</span><span class="sxs-lookup"><span data-stu-id="8e43b-110">An analyzer is a way to perform source code analysis and report a problem to the user.</span></span> <span data-ttu-id="8e43b-111">Opcionalmente, um analisador também pode fornecer uma correção de código que representa uma modificação no código-fonte do usuário.</span><span class="sxs-lookup"><span data-stu-id="8e43b-111">Optionally, an analyzer can also provide a code fix that represents a modification to the user's source code.</span></span> <span data-ttu-id="8e43b-112">Este tutorial cria um analisador que localiza as declarações de variável local que poderiam ser declaradas usando o modificador `const`, mas não o são.</span><span class="sxs-lookup"><span data-stu-id="8e43b-112">This tutorial creates an analyzer that finds local variable declarations that could be declared using the `const` modifier but are not.</span></span> <span data-ttu-id="8e43b-113">A correção de código anexa modifica essas declarações para adicionar o modificador `const`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-113">The accompanying code fix modifies those declarations to add the `const` modifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8e43b-114">{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="8e43b-114">Prerequisites</span></span>

- [<span data-ttu-id="8e43b-115">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="8e43b-115">Visual Studio 2017</span></span>](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
- [<span data-ttu-id="8e43b-116">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="8e43b-116">Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads)

<span data-ttu-id="8e43b-117">Você precisará instalar o **SDK do .net Compiler Platform** por meio do instalador do Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="8e43b-117">You'll need to install the **.NET Compiler Platform SDK** via the Visual Studio Installer:</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<span data-ttu-id="8e43b-118">Há várias etapas para criar e validar o analisador:</span><span class="sxs-lookup"><span data-stu-id="8e43b-118">There are several steps to creating and validating your analyzer:</span></span>

1. <span data-ttu-id="8e43b-119">Crie a solução.</span><span class="sxs-lookup"><span data-stu-id="8e43b-119">Create the solution.</span></span>
1. <span data-ttu-id="8e43b-120">Registre o nome e a descrição do analisador.</span><span class="sxs-lookup"><span data-stu-id="8e43b-120">Register the analyzer name and description.</span></span>
1. <span data-ttu-id="8e43b-121">Relate os avisos e recomendações do analisador.</span><span class="sxs-lookup"><span data-stu-id="8e43b-121">Report analyzer warnings and recommendations.</span></span>
1. <span data-ttu-id="8e43b-122">Implemente a correção de código para aceitar as recomendações.</span><span class="sxs-lookup"><span data-stu-id="8e43b-122">Implement the code fix to accept recommendations.</span></span>
1. <span data-ttu-id="8e43b-123">Melhore a análise por meio de testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="8e43b-123">Improve the analysis through unit tests.</span></span>

## <a name="explore-the-analyzer-template"></a><span data-ttu-id="8e43b-124">Explorar o modelo do analisador</span><span class="sxs-lookup"><span data-stu-id="8e43b-124">Explore the analyzer template</span></span>

<span data-ttu-id="8e43b-125">O analisador relata ao usuário quaisquer declarações de variável local que podem ser convertidas em constantes locais.</span><span class="sxs-lookup"><span data-stu-id="8e43b-125">Your analyzer reports to the user any local variable declarations that can be converted to local constants.</span></span> <span data-ttu-id="8e43b-126">Por exemplo, considere o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="8e43b-126">For example, consider the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="8e43b-127">No código acima, um valor constante é atribuído a `x`, que nunca é modificado.</span><span class="sxs-lookup"><span data-stu-id="8e43b-127">In the code above, `x` is assigned a constant value and is never modified.</span></span> <span data-ttu-id="8e43b-128">Ele pode ser declarado usando o modificador `const`:</span><span class="sxs-lookup"><span data-stu-id="8e43b-128">It can be declared using the `const` modifier:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="8e43b-129">A análise para determinar se uma variável pode ser tornada constante está envolvida, exigindo análise sintática, análise constante da expressão de inicializador e também análise de fluxo de dados, para garantir que nunca ocorram gravações na variável.</span><span class="sxs-lookup"><span data-stu-id="8e43b-129">The analysis to determine whether a variable can be made constant is involved, requiring syntactic analysis, constant analysis of the initializer expression and dataflow analysis to ensure that the variable is never written to.</span></span> <span data-ttu-id="8e43b-130">O .NET Compiler Platform fornece APIs que facilitam essa análise.</span><span class="sxs-lookup"><span data-stu-id="8e43b-130">The .NET Compiler Platform provides APIs that make it easier to perform this analysis.</span></span> <span data-ttu-id="8e43b-131">A primeira etapa é criar um novo em projeto de **Analisador com correção de código** do C#.</span><span class="sxs-lookup"><span data-stu-id="8e43b-131">The first step is to create a new C# **Analyzer with code fix** project.</span></span>

- <span data-ttu-id="8e43b-132">No Visual Studio, escolha **Arquivo > Novo > Projeto...** para exibir a caixa de diálogo Novo Projeto.</span><span class="sxs-lookup"><span data-stu-id="8e43b-132">In Visual Studio, choose **File > New > Project...** to display the New Project dialog.</span></span>
- <span data-ttu-id="8e43b-133">Em **Visual C# > Extensibilidade**, escolha **Analisador com correção de código (.NET Standard)** .</span><span class="sxs-lookup"><span data-stu-id="8e43b-133">Under **Visual C# > Extensibility**, choose **Analyzer with code fix (.NET Standard)**.</span></span>
- <span data-ttu-id="8e43b-134">Nomeie seu projeto como "**MakeConst**" e clique em OK.</span><span class="sxs-lookup"><span data-stu-id="8e43b-134">Name your project "**MakeConst**" and click OK.</span></span>

<span data-ttu-id="8e43b-135">O analisador com modelo de correção de código cria três projetos: um contém o analisador e a correção de código, o segundo é um projeto de teste de unidade e o terceiro é o projeto VSIX.</span><span class="sxs-lookup"><span data-stu-id="8e43b-135">The analyzer with code fix template creates three projects: one contains the analyzer and code fix, the second is a unit test project, and the third is the VSIX project.</span></span> <span data-ttu-id="8e43b-136">O projeto de inicialização padrão é o projeto VSIX.</span><span class="sxs-lookup"><span data-stu-id="8e43b-136">The default startup project is the VSIX project.</span></span> <span data-ttu-id="8e43b-137">Pressione **F5** para iniciar o projeto VSIX.</span><span class="sxs-lookup"><span data-stu-id="8e43b-137">Press **F5** to start the VSIX project.</span></span> <span data-ttu-id="8e43b-138">Isso inicia uma segunda instância do Visual Studio que tenha carregado o seu novo analisador.</span><span class="sxs-lookup"><span data-stu-id="8e43b-138">This starts a second instance of Visual Studio that has loaded your new analyzer.</span></span>

> [!TIP]
> <span data-ttu-id="8e43b-139">Quando você executa seu analisador, você pode iniciar uma segunda cópia do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e43b-139">When you run your analyzer, you start a second copy of Visual Studio.</span></span> <span data-ttu-id="8e43b-140">Essa segunda cópia usa um hive do Registro diferente para armazenar configurações.</span><span class="sxs-lookup"><span data-stu-id="8e43b-140">This second copy uses a different registry hive to store settings.</span></span> <span data-ttu-id="8e43b-141">Isso lhe permite diferenciar as configurações visuais em duas cópias do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e43b-141">That enables you to differentiate the visual settings in the two copies of Visual Studio.</span></span> <span data-ttu-id="8e43b-142">Você pode escolher um tema diferente para a execução experimental do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e43b-142">You can pick a different theme for the experimental run of Visual Studio.</span></span> <span data-ttu-id="8e43b-143">Além disso, não use perfil móvel de suas configurações nem faça logon na conta do Visual Studio usando a execução experimental do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e43b-143">In addition, don't roam your settings or login to your Visual Studio account using the experimental run of Visual Studio.</span></span> <span data-ttu-id="8e43b-144">Isso mantém as diferenças entre as configurações.</span><span class="sxs-lookup"><span data-stu-id="8e43b-144">That keeps the settings different.</span></span>

<span data-ttu-id="8e43b-145">Na segunda instância do Visual Studio que você acabou de iniciar, crie um C# novo projeto de aplicativo de console (.NET Core ou .NET Framework projeto funcionará – os analisadores funcionam no nível de origem). Passe o mouse sobre o token com um sublinhado ondulado e o texto de aviso fornecido por um analisador é exibido.</span><span class="sxs-lookup"><span data-stu-id="8e43b-145">In the second Visual Studio instance that you just started, create a new C# Console Application project (either .NET Core or .NET Framework project will work -- analyzers work at the source level.) Hover over the token with a wavy underline, and the warning text provided by an analyzer appears.</span></span>

<span data-ttu-id="8e43b-146">O modelo cria um analisador que relata um aviso em cada declaração de tipo em que o nome do tipo contém letras minúsculas, conforme mostrado na figura a seguir:</span><span class="sxs-lookup"><span data-stu-id="8e43b-146">The template creates an analyzer that reports a warning on each type declaration where the type name contains lowercase letters, as shown in the following figure:</span></span>

![Analisador de aviso de relatórios](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

<span data-ttu-id="8e43b-148">O modelo também fornece uma correção de código que altera qualquer nome de tipo que contenha caracteres de letras minúsculas, deixando-o com todas as letras maiúsculas.</span><span class="sxs-lookup"><span data-stu-id="8e43b-148">The template also provides a code fix that changes any type name containing lower case characters to all upper case.</span></span> <span data-ttu-id="8e43b-149">Você pode clicar na lâmpada exibida com o aviso para ver as alterações sugeridas.</span><span class="sxs-lookup"><span data-stu-id="8e43b-149">You can click on the light bulb displayed with the warning to see the suggested changes.</span></span> <span data-ttu-id="8e43b-150">Aceitar as alterações sugeridas atualiza o nome do tipo e todas as referências para esse tipo na solução.</span><span class="sxs-lookup"><span data-stu-id="8e43b-150">Accepting the suggested changes updates the type name and all references to that type in the solution.</span></span> <span data-ttu-id="8e43b-151">Agora que você já viu o analisador inicial em ação, feche a segunda instância do Visual Studio e retorne ao projeto do analisador.</span><span class="sxs-lookup"><span data-stu-id="8e43b-151">Now that you've seen the initial analyzer in action, close the second Visual Studio instance and return to your analyzer project.</span></span>

<span data-ttu-id="8e43b-152">Você não precisa iniciar uma segunda cópia do Visual Studio e criar um novo código para testar cada alteração em seu analisador.</span><span class="sxs-lookup"><span data-stu-id="8e43b-152">You don't have to start a second copy of Visual Studio and create new code to test every change in your analyzer.</span></span> <span data-ttu-id="8e43b-153">O modelo também cria um projeto de teste de unidade para você.</span><span class="sxs-lookup"><span data-stu-id="8e43b-153">The template also creates a unit test project for you.</span></span> <span data-ttu-id="8e43b-154">Esse projeto contém dois testes.</span><span class="sxs-lookup"><span data-stu-id="8e43b-154">That project contains two tests.</span></span> <span data-ttu-id="8e43b-155">`TestMethod1` mostra o formato típico de um teste que analisa o código sem disparar um diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="8e43b-155">`TestMethod1` shows the typical format of a test that analyzes code without triggering a diagnostic.</span></span> <span data-ttu-id="8e43b-156">`TestMethod2` mostra o formato de um teste que dispara um diagnóstico e, em seguida, aplica uma correção de código sugerida.</span><span class="sxs-lookup"><span data-stu-id="8e43b-156">`TestMethod2` shows the format of a test that triggers a diagnostic, and then applies a suggested code fix.</span></span> <span data-ttu-id="8e43b-157">Conforme você cria o analisador e a correção de código, você escreve testes para estruturas de código diferentes para verificar seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="8e43b-157">As you build your analyzer and code fix, you'll write tests for different code structures to verify your work.</span></span> <span data-ttu-id="8e43b-158">Testes de unidade para os analisadores são muito mais rápidos do que testá-los de forma interativa com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e43b-158">Unit tests for analyzers are much quicker than testing them interactively with Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="8e43b-159">Testes de unidade de analisador são uma excelente ferramenta quando você sabe quais constructos de código devem e não devem disparar seu analisador.</span><span class="sxs-lookup"><span data-stu-id="8e43b-159">Analyzer unit tests are a great tool when you know what code constructs should and shouldn't trigger your analyzer.</span></span> <span data-ttu-id="8e43b-160">Carregar o analisador em outra cópia do Visual Studio é uma excelente ferramenta para explorar e encontrar constructos nos quais você talvez não tenha pensado ainda.</span><span class="sxs-lookup"><span data-stu-id="8e43b-160">Loading your analyzer in another copy of Visual Studio is a great tool to explore and find constructs you may not have thought about yet.</span></span>

## <a name="create-analyzer-registrations"></a><span data-ttu-id="8e43b-161">Criar registros do analisador</span><span class="sxs-lookup"><span data-stu-id="8e43b-161">Create analyzer registrations</span></span>

<span data-ttu-id="8e43b-162">O modelo cria a classe inicial `DiagnosticAnalyzer`, no arquivo **MakeConstAnalyzer.cs**.</span><span class="sxs-lookup"><span data-stu-id="8e43b-162">The template creates the initial `DiagnosticAnalyzer` class, in the **MakeConstAnalyzer.cs** file.</span></span> <span data-ttu-id="8e43b-163">Esse analisador inicial mostra duas propriedades importantes de cada analisador.</span><span class="sxs-lookup"><span data-stu-id="8e43b-163">This initial analyzer shows two important properties of every analyzer.</span></span>

- <span data-ttu-id="8e43b-164">Cada analisador de diagnóstico deve fornecer um atributo `[DiagnosticAnalyzer]` que descreve a linguagem em que opera.</span><span class="sxs-lookup"><span data-stu-id="8e43b-164">Every diagnostic analyzer must provide a `[DiagnosticAnalyzer]` attribute that describes the language it operates on.</span></span>
- <span data-ttu-id="8e43b-165">Cada analisador de diagnóstico deve derivar da classe <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer>.</span><span class="sxs-lookup"><span data-stu-id="8e43b-165">Every diagnostic analyzer must derive from the <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> class.</span></span>

<span data-ttu-id="8e43b-166">O modelo também mostra os recursos básicos que fazem parte de qualquer analisador:</span><span class="sxs-lookup"><span data-stu-id="8e43b-166">The template also shows the basic features that are part of any analyzer:</span></span>

1. <span data-ttu-id="8e43b-167">Registrar ações.</span><span class="sxs-lookup"><span data-stu-id="8e43b-167">Register actions.</span></span> <span data-ttu-id="8e43b-168">As ações representam alterações de código que devem disparar o analisador para examinar se há violações de código.</span><span class="sxs-lookup"><span data-stu-id="8e43b-168">The actions represent code changes that should trigger your analyzer to examine code for violations.</span></span> <span data-ttu-id="8e43b-169">Quando o Visual Studio detecta as edições de código que correspondem a uma ação registrada, ele chama o método registrado do analisador.</span><span class="sxs-lookup"><span data-stu-id="8e43b-169">When Visual Studio detects code edits that match a registered action, it calls your analyzer's registered method.</span></span>
1. <span data-ttu-id="8e43b-170">Criar diagnósticos.</span><span class="sxs-lookup"><span data-stu-id="8e43b-170">Create diagnostics.</span></span> <span data-ttu-id="8e43b-171">Quando o analisador detecta uma violação, ele cria um objeto de diagnóstico que o Visual Studio usa para notificar o usuário sobre a violação.</span><span class="sxs-lookup"><span data-stu-id="8e43b-171">When your analyzer detects a violation, it creates a diagnostic object that Visual Studio uses to notify the user of the violation.</span></span>

<span data-ttu-id="8e43b-172">Registrar ações na substituição do método <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8e43b-172">You register actions in your override of <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8e43b-173">Neste tutorial, você visitará **nós de sintaxe** em busca de declarações locais e verá quais delas têm valores constantes.</span><span class="sxs-lookup"><span data-stu-id="8e43b-173">In this tutorial, you'll visit **syntax nodes** looking for local declarations, and see which of those have constant values.</span></span> <span data-ttu-id="8e43b-174">Se houver possibilidade de uma declaração ser constante, seu analisador criará e relatará um diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="8e43b-174">If a declaration could be constant, your analyzer will create and report a diagnostic.</span></span>

<span data-ttu-id="8e43b-175">A primeira etapa é atualizar as constantes de registro e o método `Initialize`, de modo que essas constantes indiquem seu analisador "Make Const".</span><span class="sxs-lookup"><span data-stu-id="8e43b-175">The first step is to update the registration constants and `Initialize` method so these constants indicate your "Make Const" analyzer.</span></span> <span data-ttu-id="8e43b-176">A maioria das constantes de cadeia de caracteres é definida no arquivo de recurso de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8e43b-176">Most of the string constants are defined in the string resource file.</span></span> <span data-ttu-id="8e43b-177">Você deve seguir essa prática para uma localização mais fácil.</span><span class="sxs-lookup"><span data-stu-id="8e43b-177">You should follow that practice for easier localization.</span></span> <span data-ttu-id="8e43b-178">Abra o arquivo **Resources.resx** para o projeto do analisador **MakeConst**.</span><span class="sxs-lookup"><span data-stu-id="8e43b-178">Open the **Resources.resx** file for the **MakeConst** analyzer project.</span></span> <span data-ttu-id="8e43b-179">Isso exibe o editor de recursos.</span><span class="sxs-lookup"><span data-stu-id="8e43b-179">This displays the resource editor.</span></span> <span data-ttu-id="8e43b-180">Atualize os recursos de cadeia de caracteres da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8e43b-180">Update the string resources as follows:</span></span>

- <span data-ttu-id="8e43b-181">Altere `AnalyzerTitle` para "A variável pode ser tornada constante".</span><span class="sxs-lookup"><span data-stu-id="8e43b-181">Change `AnalyzerTitle` to "Variable can be made constant".</span></span>
- <span data-ttu-id="8e43b-182">Altere `AnalyzerMessageFormat` para "Pode ser tornada constante".</span><span class="sxs-lookup"><span data-stu-id="8e43b-182">Change `AnalyzerMessageFormat` to "Can be made constant".</span></span>
- <span data-ttu-id="8e43b-183">Altere `AnalyzerDescription` para "Tornar Constante".</span><span class="sxs-lookup"><span data-stu-id="8e43b-183">Change `AnalyzerDescription` to "Make Constant".</span></span>

<span data-ttu-id="8e43b-184">Além disso, lembre-se de alterar a lista suspensa **Modificador de Acesso** para `public`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-184">Also, change the **Access Modifier** drop-down to `public`.</span></span> <span data-ttu-id="8e43b-185">Isso facilita o uso dessas constantes em testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="8e43b-185">That makes it easier to use these constants in unit tests.</span></span> <span data-ttu-id="8e43b-186">Quando você terminar, o editor de recursos deverá aparecer como mostrado na figura a seguir:</span><span class="sxs-lookup"><span data-stu-id="8e43b-186">When you have finished, the resource editor should appear as follow figure shows:</span></span>

![Atualizar recursos de cadeia de caracteres](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

<span data-ttu-id="8e43b-188">As alterações restantes estão no arquivo do analisador.</span><span class="sxs-lookup"><span data-stu-id="8e43b-188">The remaining changes are in the analyzer file.</span></span> <span data-ttu-id="8e43b-189">Abra **MakeConstAnalyzer.cs** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e43b-189">Open **MakeConstAnalyzer.cs** in Visual Studio.</span></span> <span data-ttu-id="8e43b-190">Altere a ação registrada de uma que age em símbolos para uma que age sobre a sintaxe.</span><span class="sxs-lookup"><span data-stu-id="8e43b-190">Change the registered action from one that acts on symbols to one that acts on syntax.</span></span> <span data-ttu-id="8e43b-191">No método `MakeConstAnalyzerAnalyzer.Initialize`, localize a linha que registra a ação em símbolos:</span><span class="sxs-lookup"><span data-stu-id="8e43b-191">In the `MakeConstAnalyzerAnalyzer.Initialize` method, find the line that registers the action on symbols:</span></span>

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

<span data-ttu-id="8e43b-192">Substitua-a com a seguinte linha:</span><span class="sxs-lookup"><span data-stu-id="8e43b-192">Replace it with the following line:</span></span>

[!code-csharp[Register the node action](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

<span data-ttu-id="8e43b-193">Após essa alteração, você poderá excluir o método `AnalyzeSymbol`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-193">After that change, you can delete the `AnalyzeSymbol` method.</span></span> <span data-ttu-id="8e43b-194">Este analisador examina <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, e não instruções <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8e43b-194">This analyzer examines <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, not <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> statements.</span></span> <span data-ttu-id="8e43b-195">Observe que `AnalyzeNode` tem rabiscos vermelhos sob ele.</span><span class="sxs-lookup"><span data-stu-id="8e43b-195">Notice that `AnalyzeNode` has red squiggles under it.</span></span> <span data-ttu-id="8e43b-196">O código apenas que você acaba de adicionar referencia um método `AnalyzeNode` que não foi declarado.</span><span class="sxs-lookup"><span data-stu-id="8e43b-196">The code you just added references an `AnalyzeNode` method that hasn't been declared.</span></span> <span data-ttu-id="8e43b-197">Declare esse método usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="8e43b-197">Declare that method using the following code:</span></span>

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

<span data-ttu-id="8e43b-198">Altere o `Category` para "Usage" em **MakeConstAnalyzer.cs**, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="8e43b-198">Change the `Category` to "Usage" in **MakeConstAnalyzer.cs** as shown in the following code:</span></span>

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a><span data-ttu-id="8e43b-199">Localize as declarações locais que podem ser constantes</span><span class="sxs-lookup"><span data-stu-id="8e43b-199">Find local declarations that could be const</span></span>

<span data-ttu-id="8e43b-200">É hora de escrever a primeira versão do método `AnalyzeNode`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-200">It's time to write the first version of the `AnalyzeNode` method.</span></span> <span data-ttu-id="8e43b-201">Ele deve procurar uma única declaração local que poderia ser `const` mas não é, algo semelhante ao seguinte código:</span><span class="sxs-lookup"><span data-stu-id="8e43b-201">It should look for a single local declaration that could be `const` but is not, like the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="8e43b-202">A primeira etapa é encontrar declarações locais.</span><span class="sxs-lookup"><span data-stu-id="8e43b-202">The first step is to find local declarations.</span></span> <span data-ttu-id="8e43b-203">Adicione o seguinte código a `AnalyzeNode` em **MakeConstAnalyzer.cs**:</span><span class="sxs-lookup"><span data-stu-id="8e43b-203">Add the following code to `AnalyzeNode` in **MakeConstAnalyzer.cs**:</span></span>

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

<span data-ttu-id="8e43b-204">Essa conversão sempre terá êxito porque seu analisador fez o registro para alterações unicamente a declarações locais.</span><span class="sxs-lookup"><span data-stu-id="8e43b-204">This cast always succeeds because your analyzer registered for changes to local declarations, and only local declarations.</span></span> <span data-ttu-id="8e43b-205">Nenhum outro tipo de nó dispara uma chamada para seu método `AnalyzeNode`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-205">No other node type triggers a call to your `AnalyzeNode` method.</span></span> <span data-ttu-id="8e43b-206">Em seguida, verifique a declaração para quaisquer modificadores `const`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-206">Next, check the declaration for any `const` modifiers.</span></span> <span data-ttu-id="8e43b-207">Se você encontrá-los, retorne imediatamente.</span><span class="sxs-lookup"><span data-stu-id="8e43b-207">If you find them, return immediately.</span></span> <span data-ttu-id="8e43b-208">O código a seguir procura por quaisquer modificadores `const` na declaração local:</span><span class="sxs-lookup"><span data-stu-id="8e43b-208">The following code looks for any `const` modifiers on the local declaration:</span></span>

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

<span data-ttu-id="8e43b-209">Por fim, você precisa verificar que a variável pode ser `const`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-209">Finally, you need to check that the variable could be `const`.</span></span> <span data-ttu-id="8e43b-210">Isso significa assegurar que ela nunca seja atribuída após ser inicializada.</span><span class="sxs-lookup"><span data-stu-id="8e43b-210">That means making sure it is never assigned after it is initialized.</span></span>

<span data-ttu-id="8e43b-211">Você executará alguma análise semântica usando o <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span><span class="sxs-lookup"><span data-stu-id="8e43b-211">You'll perform some semantic analysis using the <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span></span> <span data-ttu-id="8e43b-212">Você usa o argumento `context` para determinar se a declaração de variável local pode ser tornada `const`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-212">You use the `context` argument to determine whether the local variable declaration can be made `const`.</span></span> <span data-ttu-id="8e43b-213">Um <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> representa de todas as informações semânticas em um único arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="8e43b-213">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> represents of all semantic information in a single source file.</span></span> <span data-ttu-id="8e43b-214">Você pode aprender mais no artigo que aborda [modelos semânticos](../work-with-semantics.md).</span><span class="sxs-lookup"><span data-stu-id="8e43b-214">You can learn more in the article that covers [semantic models](../work-with-semantics.md).</span></span> <span data-ttu-id="8e43b-215">Você usará o <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> para realizar a análise de fluxo de dados na instrução de declaração local.</span><span class="sxs-lookup"><span data-stu-id="8e43b-215">You'll use the <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> to perform data flow analysis on the local declaration statement.</span></span> <span data-ttu-id="8e43b-216">Em seguida, você usa os resultados dessa análise de fluxo de dados para garantir que a variável local não seja escrita com um novo valor em nenhum outro lugar.</span><span class="sxs-lookup"><span data-stu-id="8e43b-216">Then, you use the results of this data flow analysis to ensure that the local variable isn't written with a new value anywhere else.</span></span> <span data-ttu-id="8e43b-217">Chame o método de extensão <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> para recuperar o <xref:Microsoft.CodeAnalysis.ILocalSymbol> para a variável e verifique se ele não está contido na coleção <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> da análise de fluxo de dados.</span><span class="sxs-lookup"><span data-stu-id="8e43b-217">Call the <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> extension method to retrieve the <xref:Microsoft.CodeAnalysis.ILocalSymbol> for the variable and check that it isn't contained with the <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> collection of the data flow analysis.</span></span> <span data-ttu-id="8e43b-218">Adicione o código a seguir ao final do método `AnalyzeNode`:</span><span class="sxs-lookup"><span data-stu-id="8e43b-218">Add the following code to the end of the `AnalyzeNode` method:</span></span>

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

<span data-ttu-id="8e43b-219">O código recém-adicionado garante que a variável não seja modificada e pode, portanto, ser tornada `const`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-219">The code just added ensures that the variable isn't modified, and can therefore be made `const`.</span></span> <span data-ttu-id="8e43b-220">É hora de gerar o diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="8e43b-220">It's time to raise the diagnostic.</span></span> <span data-ttu-id="8e43b-221">Adicione o código a seguir como a última linha em `AnalyzeNode`:</span><span class="sxs-lookup"><span data-stu-id="8e43b-221">Add the following code as the last line in `AnalyzeNode`:</span></span>

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

<span data-ttu-id="8e43b-222">Você pode verificar seu andamento pressionando **F5** para executar o analisador.</span><span class="sxs-lookup"><span data-stu-id="8e43b-222">You can check your progress by pressing **F5** to run your analyzer.</span></span> <span data-ttu-id="8e43b-223">Você pode carregar o aplicativo de console que você criou anteriormente e, em seguida, adicionar o seguinte código de teste:</span><span class="sxs-lookup"><span data-stu-id="8e43b-223">You can load the console application you created earlier and then add the following test code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="8e43b-224">A lâmpada deve aparecer e o analisador deve relatar um diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="8e43b-224">The light bulb should appear, and your analyzer should report a diagnostic.</span></span> <span data-ttu-id="8e43b-225">No entanto, a lâmpada ainda usa a correção de código gerada por modelo, e diz a você que ela pode ser colocada em letras maiúsculas.</span><span class="sxs-lookup"><span data-stu-id="8e43b-225">However, the light bulb still uses the template generated code fix, and tells you it can be made upper case.</span></span> <span data-ttu-id="8e43b-226">A próxima seção explica como escrever a correção de código.</span><span class="sxs-lookup"><span data-stu-id="8e43b-226">The next section explains how to write the code fix.</span></span>

## <a name="write-the-code-fix"></a><span data-ttu-id="8e43b-227">Escrever a correção de código</span><span class="sxs-lookup"><span data-stu-id="8e43b-227">Write the code fix</span></span>

<span data-ttu-id="8e43b-228">Um analisador pode fornecer uma ou mais correções de código.</span><span class="sxs-lookup"><span data-stu-id="8e43b-228">An analyzer can provide one or more code fixes.</span></span> <span data-ttu-id="8e43b-229">Uma correção de código define uma edição que resolve o problema relatado.</span><span class="sxs-lookup"><span data-stu-id="8e43b-229">A code fix defines an edit that addresses the reported issue.</span></span> <span data-ttu-id="8e43b-230">Para o analisador que você criou, você pode fornecer uma correção de código que insere a palavra-chave const:</span><span class="sxs-lookup"><span data-stu-id="8e43b-230">For the analyzer that you created, you can provide a code fix that inserts the const keyword:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="8e43b-231">O usuário escolhe-a da lâmpada da interface do usuário no editor e do Visual Studio altera o código.</span><span class="sxs-lookup"><span data-stu-id="8e43b-231">The user chooses it from the light bulb UI in the editor and Visual Studio changes the code.</span></span>

<span data-ttu-id="8e43b-232">Abra o arquivo **MakeConstCodeFixProvider.cs** adicionado pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="8e43b-232">Open the **MakeConstCodeFixProvider.cs** file added by the template.</span></span>  <span data-ttu-id="8e43b-233">Essa correção de código já está conectada à ID de Diagnóstico produzida pelo analisador de diagnóstico, mas ela ainda não implementa a transformação de código correta.</span><span class="sxs-lookup"><span data-stu-id="8e43b-233">This code fix is already wired up to the Diagnostic ID produced by your diagnostic analyzer, but it doesn't yet implement the right code transform.</span></span> <span data-ttu-id="8e43b-234">Primeiro você deve remover parte do código de modelo.</span><span class="sxs-lookup"><span data-stu-id="8e43b-234">First you should remove some of the template code.</span></span> <span data-ttu-id="8e43b-235">Altere a cadeia de caracteres do título para "Tornar constante":</span><span class="sxs-lookup"><span data-stu-id="8e43b-235">Change the title string to "Make constant":</span></span>

[!code-csharp[Update the CodeFix title](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

<span data-ttu-id="8e43b-236">Em seguida, exclua o método `MakeUppercaseAsync`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-236">Next, delete the `MakeUppercaseAsync` method.</span></span> <span data-ttu-id="8e43b-237">Ele não se aplica mais.</span><span class="sxs-lookup"><span data-stu-id="8e43b-237">It no longer applies.</span></span>

<span data-ttu-id="8e43b-238">Todos os provedores de correção de código derivam de <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span><span class="sxs-lookup"><span data-stu-id="8e43b-238">All code fix providers derive from <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span></span> <span data-ttu-id="8e43b-239">Todos eles substituem <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> para relatar as correções de código disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8e43b-239">They all override <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> to report available code fixes.</span></span> <span data-ttu-id="8e43b-240">Em `RegisterCodeFixesAsync`, altere o tipo de nó ancestral pelo qual você está pesquisando para um <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> para corresponder ao diagnóstico:</span><span class="sxs-lookup"><span data-stu-id="8e43b-240">In `RegisterCodeFixesAsync`, change the ancestor node type you're searching for to a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> to match the diagnostic:</span></span>

[!code-csharp[Find local declaration node](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

<span data-ttu-id="8e43b-241">Em seguida, altere a última linha para registrar uma correção de código.</span><span class="sxs-lookup"><span data-stu-id="8e43b-241">Next, change the last line to register a code fix.</span></span> <span data-ttu-id="8e43b-242">A correção criará um novo documento resultante da adição do modificador `const` para uma declaração existente:</span><span class="sxs-lookup"><span data-stu-id="8e43b-242">Your fix will create a new document that results from adding the `const` modifier to an existing declaration:</span></span>

[!code-csharp[Register the new code fix](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

<span data-ttu-id="8e43b-243">Você observará rabiscos vermelhos no código que você acabou de adicionar no símbolo `MakeConstAsync`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-243">You'll notice red squiggles in the code you just added on the symbol `MakeConstAsync`.</span></span> <span data-ttu-id="8e43b-244">Adicione uma declaração para `MakeConstAsync` semelhante ao seguinte código:</span><span class="sxs-lookup"><span data-stu-id="8e43b-244">Add a declaration for `MakeConstAsync` like the following code:</span></span>

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

<span data-ttu-id="8e43b-245">Seu novo método `MakeConstAsync` transformará o <xref:Microsoft.CodeAnalysis.Document> que representa o arquivo de origem do usuário em um novo <xref:Microsoft.CodeAnalysis.Document> que agora contém uma declaração `const`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-245">Your new `MakeConstAsync` method will transform the <xref:Microsoft.CodeAnalysis.Document> representing the user's source file into a new <xref:Microsoft.CodeAnalysis.Document> that now contains a `const` declaration.</span></span>

<span data-ttu-id="8e43b-246">Você cria um novo token de palavra-chave `const` a ser inserido no início da instrução de declaração.</span><span class="sxs-lookup"><span data-stu-id="8e43b-246">You create a new `const` keyword token to insert at the front of the declaration statement.</span></span> <span data-ttu-id="8e43b-247">Tenha cuidado para remover qualquer desafio à esquerda do primeiro token de instrução de declaração e anexe-o ao token `const`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-247">Be careful to first remove any leading trivia from the first token of the declaration statement and attach it to the `const` token.</span></span> <span data-ttu-id="8e43b-248">Adicione o seguinte código ao método `MakeConstAsync`:</span><span class="sxs-lookup"><span data-stu-id="8e43b-248">Add the following code to the `MakeConstAsync` method:</span></span>

[!code-csharp[Create a new const keyword token](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

<span data-ttu-id="8e43b-249">Em seguida, adicione o token `const` à declaração usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="8e43b-249">Next, add the `const` token to the declaration using the following code:</span></span>

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

<span data-ttu-id="8e43b-250">Em seguida, formate a nova declaração de acordo com regras de formatação de C#.</span><span class="sxs-lookup"><span data-stu-id="8e43b-250">Next, format the new declaration to match C# formatting rules.</span></span> <span data-ttu-id="8e43b-251">Formatar de suas alterações para corresponderem ao código existente cria uma experiência melhor.</span><span class="sxs-lookup"><span data-stu-id="8e43b-251">Formatting your changes to match existing code creates a better experience.</span></span> <span data-ttu-id="8e43b-252">Adicione a instrução a seguir imediatamente após o código existente:</span><span class="sxs-lookup"><span data-stu-id="8e43b-252">Add the following statement immediately after the existing code:</span></span>

[!code-csharp[Format the new declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

<span data-ttu-id="8e43b-253">Um novo namespace é necessário para esse código.</span><span class="sxs-lookup"><span data-stu-id="8e43b-253">A new namespace is required for this code.</span></span> <span data-ttu-id="8e43b-254">Adicione a instrução `using` a seguir à parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="8e43b-254">Add the following `using` statement to the top of the file:</span></span>

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

<span data-ttu-id="8e43b-255">A etapa final é fazer a edição.</span><span class="sxs-lookup"><span data-stu-id="8e43b-255">The final step is to make your edit.</span></span> <span data-ttu-id="8e43b-256">Há três etapas para esse processo:</span><span class="sxs-lookup"><span data-stu-id="8e43b-256">There are three steps to this process:</span></span>

1. <span data-ttu-id="8e43b-257">Obter um identificador para o documento existente.</span><span class="sxs-lookup"><span data-stu-id="8e43b-257">Get a handle to the existing document.</span></span>
1. <span data-ttu-id="8e43b-258">Criar um novo documento, substituindo a declaração existente pela nova declaração.</span><span class="sxs-lookup"><span data-stu-id="8e43b-258">Create a new document by replacing the existing declaration with the new declaration.</span></span>
1. <span data-ttu-id="8e43b-259">Retornar o novo documento.</span><span class="sxs-lookup"><span data-stu-id="8e43b-259">Return the new document.</span></span>

<span data-ttu-id="8e43b-260">Adicione o código a seguir ao final do método `MakeConstAsync`:</span><span class="sxs-lookup"><span data-stu-id="8e43b-260">Add the following code to the end of the `MakeConstAsync` method:</span></span>

[!code-csharp[replace the declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

<span data-ttu-id="8e43b-261">A correção de código está pronta para ser experimentada.</span><span class="sxs-lookup"><span data-stu-id="8e43b-261">Your code fix is ready to try.</span></span>  <span data-ttu-id="8e43b-262">Pressione F5 para executar o projeto do analisador em uma segunda instância do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e43b-262">Press F5 to run the analyzer project in a second instance of Visual Studio.</span></span> <span data-ttu-id="8e43b-263">Na segunda instância do Visual Studio, crie um novo projeto de Aplicativo de Console em C# e adicione algumas declarações de variável local inicializadas com valores constantes para o método Main.</span><span class="sxs-lookup"><span data-stu-id="8e43b-263">In the second Visual Studio instance, create a new C# Console Application project and add a few local variable declarations initialized with constant values to the Main method.</span></span> <span data-ttu-id="8e43b-264">Você verá que elas são relatadas como avisos, conforme mostrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="8e43b-264">You'll see that they are reported as warnings as below.</span></span>

![Pode fazer avisos constantes](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

<span data-ttu-id="8e43b-266">Você fez muito progresso.</span><span class="sxs-lookup"><span data-stu-id="8e43b-266">You've made a lot of progress.</span></span> <span data-ttu-id="8e43b-267">Há rabiscos sob as declarações que podem ser tornados `const`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-267">There are squiggles under the declarations that can be made `const`.</span></span> <span data-ttu-id="8e43b-268">Mas ainda há trabalho a fazer.</span><span class="sxs-lookup"><span data-stu-id="8e43b-268">But there is still work to do.</span></span> <span data-ttu-id="8e43b-269">Isso funciona bem se você adicionar `const` às declarações começando com `i`, depois `j` e, por fim, `k`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-269">This works fine if you add `const` to the declarations starting with `i`, then `j` and finally `k`.</span></span> <span data-ttu-id="8e43b-270">Mas se você adicionar o modificador `const` em uma ordem diferente, começando com `k`, seu analisador criará erros: `k` não pode ser declarado como `const`, a menos que `i` e `j` já sejam ambos `const`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-270">But, if you add the `const` modifier in a different order, starting with `k`, your analyzer creates errors: `k` can't be declared `const`, unless `i` and `j` are both already `const`.</span></span> <span data-ttu-id="8e43b-271">Você tem que fazer mais análise para assegurar que lida com as diferentes maneiras em que variáveis podem ser declaradas e inicializadas.</span><span class="sxs-lookup"><span data-stu-id="8e43b-271">You've got to do more analysis to ensure you handle the different ways variables can be declared and initialized.</span></span>

## <a name="build-data-driven-tests"></a><span data-ttu-id="8e43b-272">Criar testes controlados por dados</span><span class="sxs-lookup"><span data-stu-id="8e43b-272">Build data driven tests</span></span>

<span data-ttu-id="8e43b-273">Seu analisador e correção de código trabalham em um caso simples de uma única declaração que pode ser tornada const.</span><span class="sxs-lookup"><span data-stu-id="8e43b-273">Your analyzer and code fix work on a simple case of a single declaration that can be made const.</span></span> <span data-ttu-id="8e43b-274">Há várias instruções de declaração possíveis em que essa implementação comete erros.</span><span class="sxs-lookup"><span data-stu-id="8e43b-274">There are numerous possible declaration statements where this implementation makes mistakes.</span></span> <span data-ttu-id="8e43b-275">Você tratará desses casos trabalhando com a biblioteca de teste de unidade gravada pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="8e43b-275">You'll address these cases by working with the unit test library written by the template.</span></span> <span data-ttu-id="8e43b-276">Isso é muito mais rápido do que abrir repetidamente uma segunda cópia do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e43b-276">It's much faster than repeatedly opening a second copy of Visual Studio.</span></span>

<span data-ttu-id="8e43b-277">Abra o arquivo **MakeConstUnitTests.cs** no projeto de teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="8e43b-277">Open the **MakeConstUnitTests.cs** file in the unit test project.</span></span> <span data-ttu-id="8e43b-278">O modelo criou dois testes que seguem os dois padrões comuns para um analisador e o teste de unidade de correção de código.</span><span class="sxs-lookup"><span data-stu-id="8e43b-278">The template created two tests that follow the two common patterns for an analyzer and code fix unit test.</span></span> <span data-ttu-id="8e43b-279">`TestMethod1` mostra o padrão para um teste que garante que o analisador não relata um diagnóstico quando não deve fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="8e43b-279">`TestMethod1` shows the pattern for a test that ensures the analyzer doesn't report a diagnostic when it shouldn't.</span></span> <span data-ttu-id="8e43b-280">`TestMethod2` mostra o padrão para relatar um diagnóstico e executar a correção de código.</span><span class="sxs-lookup"><span data-stu-id="8e43b-280">`TestMethod2` shows the pattern for reporting a diagnostic and running the code fix.</span></span>

<span data-ttu-id="8e43b-281">O código para quase todos os testes para o seu analisador segue um destes dois padrões.</span><span class="sxs-lookup"><span data-stu-id="8e43b-281">The code for almost every test for your analyzer follows one of these two patterns.</span></span> <span data-ttu-id="8e43b-282">Para a primeira etapa, você pode refazer esses testes como testes controlados por dados.</span><span class="sxs-lookup"><span data-stu-id="8e43b-282">For the first step, you can rework these tests as data driven tests.</span></span> <span data-ttu-id="8e43b-283">Em seguida, será fácil criar novos testes adicionando novas constantes de cadeia de caracteres para representar diferentes entradas de teste.</span><span class="sxs-lookup"><span data-stu-id="8e43b-283">Then, it will be easy to create new tests by adding new string constants to represent different test inputs.</span></span>

<span data-ttu-id="8e43b-284">Para obter eficiência, a primeira etapa é refatorar os dois testes em testes controlados por dados.</span><span class="sxs-lookup"><span data-stu-id="8e43b-284">For efficiency, the first step is to refactor the two tests into data driven tests.</span></span> <span data-ttu-id="8e43b-285">Em seguida, você só precisa definir algumas constantes de cadeia de caracteres para cada novo teste.</span><span class="sxs-lookup"><span data-stu-id="8e43b-285">Then, you only need to define a couple string constants for each new test.</span></span> <span data-ttu-id="8e43b-286">Durante a refatoração, renomeie os dois métodos com nomes melhores.</span><span class="sxs-lookup"><span data-stu-id="8e43b-286">While your refactoring, rename both methods to better names.</span></span> <span data-ttu-id="8e43b-287">Substitua `TestMethod1` com este teste, que garante que nenhum diagnóstico seja gerado:</span><span class="sxs-lookup"><span data-stu-id="8e43b-287">Replace `TestMethod1` with this test that ensures no diagnostic is raised:</span></span>

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

<span data-ttu-id="8e43b-288">Você pode criar uma nova linha de dados para este teste, definindo qualquer fragmento de código que não faça com que o diagnóstico dispare um aviso.</span><span class="sxs-lookup"><span data-stu-id="8e43b-288">You can create a new data row for this test by defining any code fragment that should not cause your diagnostic to trigger a warning.</span></span> <span data-ttu-id="8e43b-289">Essa sobrecarga de `VerifyCSharpDiagnostic` passa quando não há nenhum diagnóstico disparado para o fragmento de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="8e43b-289">This overload of `VerifyCSharpDiagnostic` passes when there are no diagnostics triggered for the source code fragment.</span></span>

<span data-ttu-id="8e43b-290">Em seguida, substitua `TestMethod2` com esse teste que garante que um diagnóstico é gerado e uma correção de código aplicada ao fragmento de código-fonte:</span><span class="sxs-lookup"><span data-stu-id="8e43b-290">Next, replace `TestMethod2` with this test that ensures a diagnostic is raised and a code fix applied for the source code fragment:</span></span>

```csharp
[DataTestMethod]
[DataRow(LocalIntCouldBeConstant, LocalIntCouldBeConstantFixed, 10, 13)]
public void WhenDiagnosticIsRaisedFixUpdatesCode(
    string test,
    string fixTest,
    int line,
    int column)
{
    var expected = new DiagnosticResult
    {
        Id = MakeConstAnalyzer.DiagnosticId,
        Message = new LocalizableResourceString(nameof(MakeConst.Resources.AnalyzerMessageFormat), MakeConst.Resources.ResourceManager, typeof(MakeConst.Resources)).ToString(),
        Severity = DiagnosticSeverity.Warning,
        Locations =
            new[] {
                    new DiagnosticResultLocation("Test0.cs", line, column)
                }
    };

    VerifyCSharpDiagnostic(test, expected);

    VerifyCSharpFix(test, fixTest);
}
```

<span data-ttu-id="8e43b-291">O código anterior também fez algumas alterações no código que cria o resultado de diagnóstico esperado.</span><span class="sxs-lookup"><span data-stu-id="8e43b-291">The preceding code also made a couple changes to the code that builds the expected diagnostic result.</span></span> <span data-ttu-id="8e43b-292">Ele usa as constantes públicas registradas no analisador `MakeConst`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-292">It uses the public constants registered in the `MakeConst` analyzer.</span></span> <span data-ttu-id="8e43b-293">Além disso, ele usa duas constantes de cadeia de caracteres para a fonte de entrada e fonte fixa.</span><span class="sxs-lookup"><span data-stu-id="8e43b-293">In addition, it uses two string constants for the input and fixed source.</span></span> <span data-ttu-id="8e43b-294">Adicione as seguintes constantes de cadeia de caracteres à classe `UnitTest`:</span><span class="sxs-lookup"><span data-stu-id="8e43b-294">Add the following string constants to the `UnitTest` class:</span></span>

[!code-csharp[string constants for fix test](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

<span data-ttu-id="8e43b-295">Execute esses dois testes para certificar-se de sua aprovação.</span><span class="sxs-lookup"><span data-stu-id="8e43b-295">Run these two tests to make sure they pass.</span></span> <span data-ttu-id="8e43b-296">No Visual Studio, abra o **Gerenciador de Testes** selecionando **Teste** > **Windows** > **Gerenciador de Testes**.</span><span class="sxs-lookup"><span data-stu-id="8e43b-296">In Visual Studio, open the **Test Explorer** by selecting **Test** > **Windows** > **Test Explorer**.</span></span>  <span data-ttu-id="8e43b-297">Em seguida, pressione o link **Executar Tudo**.</span><span class="sxs-lookup"><span data-stu-id="8e43b-297">The press the **Run All** link.</span></span>

## <a name="create-tests-for-valid-declarations"></a><span data-ttu-id="8e43b-298">Criar testes para declarações válidas</span><span class="sxs-lookup"><span data-stu-id="8e43b-298">Create tests for valid declarations</span></span>

<span data-ttu-id="8e43b-299">Como regra geral, os analisadores devem sair assim que possível, fazendo o mínimo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8e43b-299">As a general rule, analyzers should exit as quickly as possible, doing minimal work.</span></span> <span data-ttu-id="8e43b-300">O Visual Studio chama analisadores registrados conforme o usuário edita o código.</span><span class="sxs-lookup"><span data-stu-id="8e43b-300">Visual Studio calls registered analyzers as the user edits code.</span></span> <span data-ttu-id="8e43b-301">A capacidade de resposta é um requisito fundamental.</span><span class="sxs-lookup"><span data-stu-id="8e43b-301">Responsiveness is a key requirement.</span></span> <span data-ttu-id="8e43b-302">Há vários casos de teste para o código que não deverão gerar o diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="8e43b-302">There are several test cases for code that should not raise your diagnostic.</span></span> <span data-ttu-id="8e43b-303">O analisador já gerencia um desses testes, o caso em que uma variável é atribuída após ser inicializada.</span><span class="sxs-lookup"><span data-stu-id="8e43b-303">Your analyzer already handles one of those tests, the case where a variable is assigned after being initialized.</span></span> <span data-ttu-id="8e43b-304">Adicione a constante de cadeia de caracteres a seguir para seus testes para representar esse caso:</span><span class="sxs-lookup"><span data-stu-id="8e43b-304">Add the following string constant to your tests to represent that case:</span></span>

[!code-csharp[variable assigned](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

<span data-ttu-id="8e43b-305">Em seguida, adicione uma linha de dados para este teste, conforme mostrado no snippet de código a seguir:</span><span class="sxs-lookup"><span data-stu-id="8e43b-305">Then, add a data row for this test as shown in the snippet below:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="8e43b-306">Esse teste é aprovado também.</span><span class="sxs-lookup"><span data-stu-id="8e43b-306">This test passes as well.</span></span> <span data-ttu-id="8e43b-307">Em seguida, adicione as constantes para as condições que você ainda não manipulou ainda:</span><span class="sxs-lookup"><span data-stu-id="8e43b-307">Next, add constants for conditions you haven't handled yet:</span></span>

- <span data-ttu-id="8e43b-308">Declarações que já são `const`, porque elas já são const:</span><span class="sxs-lookup"><span data-stu-id="8e43b-308">Declarations that are already `const`, because they are already const:</span></span>

   [!code-csharp[already const declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- <span data-ttu-id="8e43b-309">Declarações que não têm nenhum inicializador, porque não há nenhum valor a ser usado:</span><span class="sxs-lookup"><span data-stu-id="8e43b-309">Declarations that have no initializer, because there is no value to use:</span></span>

   [!code-csharp[declarations that have no initializer](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- <span data-ttu-id="8e43b-310">Declarações em que o inicializador não é uma constante, porque elas não podem ser constantes de tempo de compilação:</span><span class="sxs-lookup"><span data-stu-id="8e43b-310">Declarations where the initializer is not a constant, because they can't be compile-time constants:</span></span>

   [!code-csharp[declarations where the initializer isn't const](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

<span data-ttu-id="8e43b-311">Isso pode ser ainda mais complicado, porque o C# permite várias declarações como uma instrução.</span><span class="sxs-lookup"><span data-stu-id="8e43b-311">It can be even more complicated because C# allows multiple declarations as one statement.</span></span> <span data-ttu-id="8e43b-312">Considere a seguinte constante de cadeia de caracteres de caso de teste:</span><span class="sxs-lookup"><span data-stu-id="8e43b-312">Consider the following test case string constant:</span></span>

[!code-csharp[multiple initializers](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

<span data-ttu-id="8e43b-313">A variável `i` pode ser tornada constante, mas o mesmo não se aplica à variável `j`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-313">The variable `i` can be made constant, but the variable `j` cannot.</span></span> <span data-ttu-id="8e43b-314">Portanto, essa instrução não pode ser tornada uma declaração const.</span><span class="sxs-lookup"><span data-stu-id="8e43b-314">Therefore, this statement cannot be made a const declaration.</span></span> <span data-ttu-id="8e43b-315">Adicione as declarações `DataRow` para todos esses testes:</span><span class="sxs-lookup"><span data-stu-id="8e43b-315">Add the `DataRow` declarations for all these tests:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
    DataRow(VariableAssigned),
    DataRow(AlreadyConst),
    DataRow(NoInitializer),
    DataRow(InitializerNotConstant),
    DataRow(MultipleInitializers)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="8e43b-316">Execute os testes novamente e você verá esses novos casos de teste falharem.</span><span class="sxs-lookup"><span data-stu-id="8e43b-316">Run your tests again, and you'll see these new test cases fail.</span></span>

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a><span data-ttu-id="8e43b-317">Atualize seu analisador para ignorar as declarações corretas</span><span class="sxs-lookup"><span data-stu-id="8e43b-317">Update your analyzer to ignore correct declarations</span></span>

<span data-ttu-id="8e43b-318">Você precisa de algumas melhorias no método `AnalyzeNode` do analisador para filtrar o código que corresponde a essas condições.</span><span class="sxs-lookup"><span data-stu-id="8e43b-318">You need some enhancements to your analyzer's `AnalyzeNode` method to filter out code that matches these conditions.</span></span> <span data-ttu-id="8e43b-319">Elas são todas condições relacionadas, portanto, alterações semelhantes corrigirão todas essas condições.</span><span class="sxs-lookup"><span data-stu-id="8e43b-319">They are all related conditions, so similar changes will fix all these conditions.</span></span> <span data-ttu-id="8e43b-320">Faça as alterações a seguir em `AnalyzeNode`:</span><span class="sxs-lookup"><span data-stu-id="8e43b-320">Make the following changes to `AnalyzeNode`:</span></span>

- <span data-ttu-id="8e43b-321">A análise semântica examinou uma única declaração de variável.</span><span class="sxs-lookup"><span data-stu-id="8e43b-321">Your semantic analysis examined a single variable declaration.</span></span> <span data-ttu-id="8e43b-322">Esse código deve estar em um loop de `foreach` que examina todas as variáveis declaradas na mesma instrução.</span><span class="sxs-lookup"><span data-stu-id="8e43b-322">This code needs to be in a `foreach` loop that examines all the variables declared in the same statement.</span></span>
- <span data-ttu-id="8e43b-323">Cada variável declarada precisa ter um inicializador.</span><span class="sxs-lookup"><span data-stu-id="8e43b-323">Each declared variable needs to have an initializer.</span></span>
- <span data-ttu-id="8e43b-324">O inicializador de cada variável declarada precisa ser uma constante de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="8e43b-324">Each declared variable's initializer must be a compile-time constant.</span></span>

<span data-ttu-id="8e43b-325">No seu método `AnalyzeNode`, substitua a análise semântica original:</span><span class="sxs-lookup"><span data-stu-id="8e43b-325">In your `AnalyzeNode` method, replace the original semantic analysis:</span></span>

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

<span data-ttu-id="8e43b-326">com o snippet de código a seguir:</span><span class="sxs-lookup"><span data-stu-id="8e43b-326">with the following code snippet:</span></span>

```csharp
// Ensure that all variables in the local declaration have initializers that
// are assigned with constant values.
foreach (var variable in localDeclaration.Declaration.Variables)
{
    var initializer = variable.Initializer;
    if (initializer == null)
    {
        return;
    }

    var constantValue = context.SemanticModel.GetConstantValue(initializer.Value);
    if (!constantValue.HasValue)
    {
        return;
    }
}

// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

foreach (var variable in localDeclaration.Declaration.Variables)
{
    // Retrieve the local symbol for each variable in the local declaration
    // and ensure that it is not written outside of the data flow analysis region.
    var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
    if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
    {
        return;
    }
}
```

<span data-ttu-id="8e43b-327">O primeiro loop de `foreach` examina cada declaração de variável usando a análise sintática.</span><span class="sxs-lookup"><span data-stu-id="8e43b-327">The first `foreach` loop examines each variable declaration using syntactic analysis.</span></span> <span data-ttu-id="8e43b-328">A primeira verificação garante que a variável tenha um inicializador.</span><span class="sxs-lookup"><span data-stu-id="8e43b-328">The first check guarantees that the variable has an initializer.</span></span> <span data-ttu-id="8e43b-329">A segunda verificação garante que o inicializador seja uma constante.</span><span class="sxs-lookup"><span data-stu-id="8e43b-329">The second check guarantees that the initializer is a constant.</span></span> <span data-ttu-id="8e43b-330">O segundo loop tem a análise semântica original.</span><span class="sxs-lookup"><span data-stu-id="8e43b-330">The second loop has the original semantic analysis.</span></span> <span data-ttu-id="8e43b-331">As verificações semânticas estão em um loop separado porque ele tem um impacto maior no desempenho.</span><span class="sxs-lookup"><span data-stu-id="8e43b-331">The semantic checks are in a separate loop because it has a greater impact on performance.</span></span> <span data-ttu-id="8e43b-332">Execute os testes novamente e você deverá ver todos eles serem aprovados.</span><span class="sxs-lookup"><span data-stu-id="8e43b-332">Run your tests again, and you should see them all pass.</span></span>

## <a name="add-the-final-polish"></a><span data-ttu-id="8e43b-333">Adicionar o final polonês</span><span class="sxs-lookup"><span data-stu-id="8e43b-333">Add the final polish</span></span>

<span data-ttu-id="8e43b-334">Você está quase terminando.</span><span class="sxs-lookup"><span data-stu-id="8e43b-334">You're almost done.</span></span> <span data-ttu-id="8e43b-335">Há mais algumas condições com as quais o seu analisador deve lidar.</span><span class="sxs-lookup"><span data-stu-id="8e43b-335">There are a few more conditions for your analyzer to handle.</span></span> <span data-ttu-id="8e43b-336">Enquanto o usuário está escrevendo código, o Visual Studio chama os analisadores.</span><span class="sxs-lookup"><span data-stu-id="8e43b-336">Visual Studio calls analyzers while the user is writing code.</span></span> <span data-ttu-id="8e43b-337">Muitas vezes o analisador será chamado para código que não é compilado.</span><span class="sxs-lookup"><span data-stu-id="8e43b-337">It's often the case that your analyzer will be called for code that doesn't compile.</span></span> <span data-ttu-id="8e43b-338">O método `AnalyzeNode` do analisador de diagnóstico não verifica para ver se o valor da constante é conversível para o tipo de variável.</span><span class="sxs-lookup"><span data-stu-id="8e43b-338">The diagnostic analyzer's `AnalyzeNode` method does not check to see if the constant value is convertible to the variable type.</span></span> <span data-ttu-id="8e43b-339">Assim, a implementação atual converterá facilmente uma declaração incorreta, tal como int i = "abc", em uma constante local.</span><span class="sxs-lookup"><span data-stu-id="8e43b-339">So, the current implementation will happily convert an incorrect declaration such as int i = "abc"' to a local constant.</span></span> <span data-ttu-id="8e43b-340">Adicione uma constante de cadeia de caracteres de origem para essa condição:</span><span class="sxs-lookup"><span data-stu-id="8e43b-340">Add a source string constant for that condition:</span></span>

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

<span data-ttu-id="8e43b-341">Além disso, os tipos de referência não são tratados corretamente.</span><span class="sxs-lookup"><span data-stu-id="8e43b-341">In addition, reference types are not handled properly.</span></span> <span data-ttu-id="8e43b-342">O único valor de constante permitido para um tipo de referência é `null`, exceto no caso de <xref:System.String?displayProperty=nameWithType>, que permite literais de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8e43b-342">The only constant value allowed for a reference type is `null`, except in this case of <xref:System.String?displayProperty=nameWithType>, which allows string literals.</span></span> <span data-ttu-id="8e43b-343">Em outras palavras, `const string s = "abc"` é legal, mas `const object s = "abc"` não é.</span><span class="sxs-lookup"><span data-stu-id="8e43b-343">In other words, `const string s = "abc"` is legal, but `const object s = "abc"` is not.</span></span> <span data-ttu-id="8e43b-344">Este snippet de código verifica essa condição:</span><span class="sxs-lookup"><span data-stu-id="8e43b-344">This code snippet verifies that condition:</span></span>

[!code-csharp[Reference types don't raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

<span data-ttu-id="8e43b-345">Para ser criterioso, você precisará adicionar outro teste para verificar se pode criar uma declaração de constante para uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8e43b-345">To be thorough, you need to add another test to make sure that you can create a constant declaration for a string.</span></span> <span data-ttu-id="8e43b-346">O snippet de código a seguir define o código que gera o diagnóstico e o código após a aplicação da correção:</span><span class="sxs-lookup"><span data-stu-id="8e43b-346">The following snippet defines both the code that raises the diagnostic, and the code after the fix has been applied:</span></span>

[!code-csharp[string reference types raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

<span data-ttu-id="8e43b-347">Por fim, se uma variável é declarada com a palavra-chave `var`, a correção de código faz a coisa errada e gera uma declaração `const var`, que não é compatível com a linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="8e43b-347">Finally, if a variable is declared with the `var` keyword, the code fix does the wrong thing and generates a `const var` declaration, which is not supported by the C# language.</span></span> <span data-ttu-id="8e43b-348">Para corrigir esse bug, a correção de código deve substituir a palavra-chave `var` pelo nome do tipo inferido:</span><span class="sxs-lookup"><span data-stu-id="8e43b-348">To fix this bug, the code fix must replace the `var` keyword with the inferred type's name:</span></span>

[!code-csharp[var references need to use the inferred types](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

<span data-ttu-id="8e43b-349">Essas alterações atualizam as declarações de linha de dados para ambos os testes.</span><span class="sxs-lookup"><span data-stu-id="8e43b-349">These changes update the data row declarations for both tests.</span></span> <span data-ttu-id="8e43b-350">O código a seguir mostra esses testes com todos os atributos de linha de dados:</span><span class="sxs-lookup"><span data-stu-id="8e43b-350">The following code shows these tests with all data row attributes:</span></span>

[!code-csharp[The finished tests](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

<span data-ttu-id="8e43b-351">Felizmente, todos os erros acima podem ser resolvidos usando as mesmas técnicas que você acabou de aprender.</span><span class="sxs-lookup"><span data-stu-id="8e43b-351">Fortunately, all of the above bugs can be addressed using the same techniques that you just learned.</span></span>

<span data-ttu-id="8e43b-352">Para corrigir o primeiro bug, primeiro abra **DiagnosticAnalyzer.cs** e localize o loop foreach em que cada um dos inicializadores de declaração local é verificado para garantir que valores constantes sejam atribuídos a eles.</span><span class="sxs-lookup"><span data-stu-id="8e43b-352">To fix the first bug, first open **DiagnosticAnalyzer.cs** and locate the foreach loop where each of the local declaration's initializers are checked to ensure that they're assigned with constant values.</span></span> <span data-ttu-id="8e43b-353">Imediatamente _antes_ do primeiro loop foreach, chame `context.SemanticModel.GetTypeInfo()` para recuperar informações detalhadas sobre o tipo declarado da declaração local:</span><span class="sxs-lookup"><span data-stu-id="8e43b-353">Immediately _before_ the first foreach loop, call `context.SemanticModel.GetTypeInfo()` to retrieve detailed information about the declared type of the local declaration:</span></span>

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

<span data-ttu-id="8e43b-354">Em seguida, dentro do loop `foreach`, verifique cada inicializador para garantir que ele pode ser convertido no tipo de variável.</span><span class="sxs-lookup"><span data-stu-id="8e43b-354">Then, inside your `foreach` loop, check each initializer to make sure it's convertible to the variable type.</span></span> <span data-ttu-id="8e43b-355">Adicione a seguinte verificação depois de garantir que o inicializador é uma constante:</span><span class="sxs-lookup"><span data-stu-id="8e43b-355">Add the following check after ensuring that the initializer is a constant:</span></span>

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

<span data-ttu-id="8e43b-356">A próxima alteração é realizada com base na última.</span><span class="sxs-lookup"><span data-stu-id="8e43b-356">The next change builds upon the last one.</span></span> <span data-ttu-id="8e43b-357">Antes da chave de fechamento do primeiro loop foreach, adicione o código a seguir para verificar o tipo da declaração de local quando a constante é uma cadeia de caracteres ou valor nulo.</span><span class="sxs-lookup"><span data-stu-id="8e43b-357">Before the closing curly brace of the first foreach loop, add the following code to check the type of the local declaration when the constant is a string or null.</span></span>

```csharp
// Special cases:
//  * If the constant value is a string, the type of the local declaration
//    must be System.String.
//  * If the constant value is null, the type of the local declaration must
//    be a reference type.
if (constantValue.Value is string)
{
    if (variableType.SpecialType != SpecialType.System_String)
    {
        return;
    }
}
else if (variableType.IsReferenceType && constantValue.Value != null)
{
    return;
}
```

<span data-ttu-id="8e43b-358">Você precisa escrever um pouco mais de código no seu provedor de correção de código para substituir a palavra-chave var' com o nome do tipo correto.</span><span class="sxs-lookup"><span data-stu-id="8e43b-358">You must write a bit more code in your code fix provider to replace the var' keyword with the correct type name.</span></span> <span data-ttu-id="8e43b-359">Retorne ao **CodeFixProvider.cs**.</span><span class="sxs-lookup"><span data-stu-id="8e43b-359">Return to **CodeFixProvider.cs**.</span></span> <span data-ttu-id="8e43b-360">O código que você adicionará realizará as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="8e43b-360">The code you'll add does the following steps:</span></span>

- <span data-ttu-id="8e43b-361">Verifique se a declaração é uma declaração `var` e se afirmativo:</span><span class="sxs-lookup"><span data-stu-id="8e43b-361">Check if the declaration is a `var` declaration, and if it is:</span></span>
- <span data-ttu-id="8e43b-362">Crie um novo tipo para o tipo inferido.</span><span class="sxs-lookup"><span data-stu-id="8e43b-362">Create a new type for the inferred type.</span></span>
- <span data-ttu-id="8e43b-363">Certifique-se de que a declaração de tipo não é um alias.</span><span class="sxs-lookup"><span data-stu-id="8e43b-363">Make sure the type declaration is not an alias.</span></span> <span data-ttu-id="8e43b-364">Em caso afirmativo, é legal declarar `const var`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-364">If so, it is legal to declare `const var`.</span></span>
- <span data-ttu-id="8e43b-365">Certifique-se de que `var` não é um nome de tipo neste programa.</span><span class="sxs-lookup"><span data-stu-id="8e43b-365">Make sure that `var` isn't a type name in this program.</span></span> <span data-ttu-id="8e43b-366">(Em caso afirmativo, `const var` é legal).</span><span class="sxs-lookup"><span data-stu-id="8e43b-366">(If so, `const var` is legal).</span></span>
- <span data-ttu-id="8e43b-367">Simplificar o nome completo do tipo</span><span class="sxs-lookup"><span data-stu-id="8e43b-367">Simplify the full type name</span></span>

<span data-ttu-id="8e43b-368">Isso soa como muito código.</span><span class="sxs-lookup"><span data-stu-id="8e43b-368">That sounds like a lot of code.</span></span> <span data-ttu-id="8e43b-369">Mas não é.</span><span class="sxs-lookup"><span data-stu-id="8e43b-369">It's not.</span></span> <span data-ttu-id="8e43b-370">Substitua a linha que declara e inicializa `newLocal` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8e43b-370">Replace the line that declares and initializes `newLocal` with the following code.</span></span> <span data-ttu-id="8e43b-371">Ele é colocado imediatamente após a inicialização de `newModifiers`:</span><span class="sxs-lookup"><span data-stu-id="8e43b-371">It goes immediately after the initialization of `newModifiers`:</span></span>

[!code-csharp[Replace Var designations](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

<span data-ttu-id="8e43b-372">Você precisará adicionar uma instrução `using` para usar o tipo <xref:Microsoft.CodeAnalysis.Simplification.Simplifier>:</span><span class="sxs-lookup"><span data-stu-id="8e43b-372">You'll need to add one `using` statement to use the <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> type:</span></span>

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

<span data-ttu-id="8e43b-373">Execute seus testes, que devem todos ser aprovados.</span><span class="sxs-lookup"><span data-stu-id="8e43b-373">Run your tests, and they should all pass.</span></span> <span data-ttu-id="8e43b-374">Dê parabéns a si mesmo, executando seu analisador concluído.</span><span class="sxs-lookup"><span data-stu-id="8e43b-374">Congratulate yourself by running your finished analyzer.</span></span> <span data-ttu-id="8e43b-375">Pressione Ctrl + F5 para executar o projeto do analisador em uma segunda instância do Visual Studio com a extensão de versão prévia do Roslyn carregada.</span><span class="sxs-lookup"><span data-stu-id="8e43b-375">Press Ctrl+F5 to run the analyzer project in a second instance of Visual Studio with the Roslyn Preview extension loaded.</span></span>

- <span data-ttu-id="8e43b-376">Na segunda instância do Visual Studio, crie um novo projeto de Aplicativo de Console de C# e adicione `int x = "abc";` ao método Main.</span><span class="sxs-lookup"><span data-stu-id="8e43b-376">In the second Visual Studio instance, create a new C# Console Application project and add `int x = "abc";` to the Main method.</span></span> <span data-ttu-id="8e43b-377">Graças à primeira correção de bug, nenhum aviso deve ser relatado para esta declaração de variável local (embora haja um erro do compilador, conforme esperado).</span><span class="sxs-lookup"><span data-stu-id="8e43b-377">Thanks to the first bug fix, no warning should be reported for this local variable declaration (though there's a compiler error as expected).</span></span>
- <span data-ttu-id="8e43b-378">Em seguida, adicione `object s = "abc";` ao método Main.</span><span class="sxs-lookup"><span data-stu-id="8e43b-378">Next, add `object s = "abc";` to the Main method.</span></span> <span data-ttu-id="8e43b-379">Devido à segunda correção de bug, nenhum aviso deve ser relatado.</span><span class="sxs-lookup"><span data-stu-id="8e43b-379">Because of the second bug fix, no warning should be reported.</span></span>
- <span data-ttu-id="8e43b-380">Por fim, adicione outra variável local que usa a palavra-chave `var`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-380">Finally, add another local variable that uses the `var` keyword.</span></span> <span data-ttu-id="8e43b-381">Você verá que um aviso é relatado e uma sugestão é exibida abaixo e a esquerda.</span><span class="sxs-lookup"><span data-stu-id="8e43b-381">You'll see that a warning is reported and a suggestion appears beneath to the left.</span></span>
- <span data-ttu-id="8e43b-382">Mova o cursor do editor sobre o sublinhado ondulado e pressione Ctrl +.</span><span class="sxs-lookup"><span data-stu-id="8e43b-382">Move the editor caret over the squiggly underline and press Ctrl+.</span></span> <span data-ttu-id="8e43b-383">para exibir a correção de código sugerida.</span><span class="sxs-lookup"><span data-stu-id="8e43b-383">to display the suggested code fix.</span></span> <span data-ttu-id="8e43b-384">Ao selecionar a correção de código, observe que a palavra-chave var' agora é manipulada corretamente.</span><span class="sxs-lookup"><span data-stu-id="8e43b-384">Upon selecting your code fix, note that the var' keyword is now handled correctly.</span></span>

<span data-ttu-id="8e43b-385">Por fim, adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="8e43b-385">Finally, add the following code:</span></span>

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

<span data-ttu-id="8e43b-386">Após essas alterações, você obtém linhas onduladas vermelhas apenas nas duas primeiras variáveis.</span><span class="sxs-lookup"><span data-stu-id="8e43b-386">After these changes, you get red squiggles only on the first two variables.</span></span> <span data-ttu-id="8e43b-387">Adicione `const` para ambos `i` e `j`, e você receberá um novo aviso em `k` porque ele agora pode ser `const`.</span><span class="sxs-lookup"><span data-stu-id="8e43b-387">Add `const` to both `i` and `j`, and you get a new warning on `k` because it can now be `const`.</span></span>

<span data-ttu-id="8e43b-388">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="8e43b-388">Congratulations!</span></span> <span data-ttu-id="8e43b-389">Você criou sua primeira extensão do .NET Compiler Platform que executa análise de código com o sistema em funcionamento para detectar um problema e fornece uma correção rápida para corrigi-lo.</span><span class="sxs-lookup"><span data-stu-id="8e43b-389">You've created your first .NET Compiler Platform extension that performs on-the-fly code analysis to detect an issue and provides a quick fix to correct it.</span></span> <span data-ttu-id="8e43b-390">Ao longo do caminho, você aprendeu muitas das APIs de código que fazem parte do SDK do .NET Compiler Platform (APIs do Roslyn).</span><span class="sxs-lookup"><span data-stu-id="8e43b-390">Along the way, you've learned many of the code APIs that are part of the .NET Compiler Platform SDK (Roslyn APIs).</span></span> <span data-ttu-id="8e43b-391">Você pode verificar seu trabalho comparando-o à [amostra concluída](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) em nosso repositório GitHub de exemplos.</span><span class="sxs-lookup"><span data-stu-id="8e43b-391">You can check your work against the [completed sample](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) in our samples GitHub repository.</span></span> <span data-ttu-id="8e43b-392">Ou você pode baixar o [arquivo zip do projeto concluído](https://github.com/dotnet/samples/blob/master/csharp/roslyn-sdk/Tutorials/MakeConst.zip)</span><span class="sxs-lookup"><span data-stu-id="8e43b-392">Or you can download [zip file of the completed project](https://github.com/dotnet/samples/blob/master/csharp/roslyn-sdk/Tutorials/MakeConst.zip)</span></span>

## <a name="other-resources"></a><span data-ttu-id="8e43b-393">Outros recursos</span><span class="sxs-lookup"><span data-stu-id="8e43b-393">Other resources</span></span>

- [<span data-ttu-id="8e43b-394">Introdução à análise de sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e43b-394">Get started with syntax analysis</span></span>](../get-started/syntax-analysis.md)
- [<span data-ttu-id="8e43b-395">Introdução à análise semântica</span><span class="sxs-lookup"><span data-stu-id="8e43b-395">Get started with semantic analysis</span></span>](../get-started/semantic-analysis.md)
