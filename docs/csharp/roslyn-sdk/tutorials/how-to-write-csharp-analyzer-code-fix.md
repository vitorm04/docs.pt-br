---
title: 'Tutorial: escrever seu primeiro analisador e correção de código'
description: Este tutorial fornece instruções passo a passo para criar um analisador e correção de código usando o SDK do .NET Compiler (APIs do Roslyn).
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: e79907f364939462b7d0d5814c4752be23bcfdf3
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381587"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a><span data-ttu-id="e6228-103">Tutorial: escrever seu primeiro analisador e correção de código</span><span class="sxs-lookup"><span data-stu-id="e6228-103">Tutorial: Write your first analyzer and code fix</span></span>

<span data-ttu-id="e6228-104">O SDK da .NET Compiler Platform fornece as ferramentas necessárias para criar avisos personalizados destinados ao C# ou código do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e6228-104">The .NET Compiler Platform SDK provides the tools you need to create custom warnings that target C# or Visual Basic code.</span></span> <span data-ttu-id="e6228-105">Seu **analisador** contém código que reconhece as violações da sua regra.</span><span class="sxs-lookup"><span data-stu-id="e6228-105">Your **analyzer** contains code that recognizes violations of your rule.</span></span> <span data-ttu-id="e6228-106">Sua **correção de código** contém o código que corrige a violação.</span><span class="sxs-lookup"><span data-stu-id="e6228-106">Your **code fix** contains the code that fixes the violation.</span></span> <span data-ttu-id="e6228-107">As regras que você implementar podem ser qualquer coisa, incluindo estrutura do código, estilo de codificação, convenções de nomenclatura e muito mais.</span><span class="sxs-lookup"><span data-stu-id="e6228-107">The rules you implement can be anything from code structure to coding style to naming conventions and more.</span></span> <span data-ttu-id="e6228-108">O .NET Compiler Platform fornece a estrutura para executar análise conforme os desenvolvedores escrevem o código, bem como todos os recursos de interface do usuário do Visual Studio para corrigir o código: mostrar rabiscos no editor, popular a Lista de Erros do Visual Studio, criar as sugestões da "lâmpada" e mostrar a visualização avançada das correções sugeridas.</span><span class="sxs-lookup"><span data-stu-id="e6228-108">The .NET Compiler Platform provides the framework for running analysis as developers are writing code, and all the Visual Studio UI features for fixing code: showing squiggles in the editor, populating the Visual Studio Error List, creating the "light bulb" suggestions and showing the rich preview of the suggested fixes.</span></span>

<span data-ttu-id="e6228-109">Neste tutorial, você explorará a criação de um **analisador** e uma **correção de código** que o acompanha, usando as APIs do Roslyn.</span><span class="sxs-lookup"><span data-stu-id="e6228-109">In this tutorial, you'll explore the creation of an **analyzer** and an accompanying **code fix** using the Roslyn APIs.</span></span> <span data-ttu-id="e6228-110">Um analisador é uma maneira de executar a análise de código-fonte e relatar um problema para o usuário.</span><span class="sxs-lookup"><span data-stu-id="e6228-110">An analyzer is a way to perform source code analysis and report a problem to the user.</span></span> <span data-ttu-id="e6228-111">Opcionalmente, um analisador também pode fornecer uma correção de código que representa uma modificação no código-fonte do usuário.</span><span class="sxs-lookup"><span data-stu-id="e6228-111">Optionally, an analyzer can also provide a code fix that represents a modification to the user's source code.</span></span> <span data-ttu-id="e6228-112">Este tutorial cria um analisador que localiza as declarações de variável local que poderiam ser declaradas usando o modificador `const`, mas não o são.</span><span class="sxs-lookup"><span data-stu-id="e6228-112">This tutorial creates an analyzer that finds local variable declarations that could be declared using the `const` modifier but are not.</span></span> <span data-ttu-id="e6228-113">A correção de código anexa modifica essas declarações para adicionar o modificador `const`.</span><span class="sxs-lookup"><span data-stu-id="e6228-113">The accompanying code fix modifies those declarations to add the `const` modifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e6228-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e6228-114">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="e6228-115">O modelo atual do **analisador do Visual Studio com o código Fix (.net Standard)** tem um bug conhecido e deve ser corrigido no Visual Studio 2019 versão 16,7.</span><span class="sxs-lookup"><span data-stu-id="e6228-115">The current Visual Studio **Analyzer with code fix (.NET Standard)** template has a known bug in it and should be fixed in Visual Studio 2019 version 16.7.</span></span> <span data-ttu-id="e6228-116">Os projetos no modelo não serão compilados, a menos que sejam feitas as seguintes alterações:</span><span class="sxs-lookup"><span data-stu-id="e6228-116">The projects in the template will not compile unless the following changes are made:</span></span>
>
> 1. <span data-ttu-id="e6228-117">Selecione **ferramentas**  >  **Opções**  >  pacote**Gerenciador de pacotes NuGet**  >  **fontes**</span><span class="sxs-lookup"><span data-stu-id="e6228-117">Select **Tools** > **Options** > **NuGet Package Manager** > **Package Sources**</span></span>
>    - <span data-ttu-id="e6228-118">Selecione o botão de adição para adicionar uma nova fonte:</span><span class="sxs-lookup"><span data-stu-id="e6228-118">Select the plus button, to add a new source:</span></span>
>    - <span data-ttu-id="e6228-119">Defina a **origem** como `https://dotnet.myget.org/F/roslyn-analyzers/api/v3/index.json` e selecione **Atualizar**</span><span class="sxs-lookup"><span data-stu-id="e6228-119">Set the **Source** to `https://dotnet.myget.org/F/roslyn-analyzers/api/v3/index.json` and select **Update**</span></span>
> 1. <span data-ttu-id="e6228-120">No **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **MakeConst. vsix** e selecione **Editar arquivo de projeto**</span><span class="sxs-lookup"><span data-stu-id="e6228-120">From the **Solution Explorer**, right-click on the **MakeConst.Vsix** project, and select **Edit Project File**</span></span>
>    - <span data-ttu-id="e6228-121">Atualize o `<AssemblyName>` nó para adicionar o `.Visx` sufixo:</span><span class="sxs-lookup"><span data-stu-id="e6228-121">Update the `<AssemblyName>` node to add the `.Visx` suffix:</span></span>
>      - `<AssemblyName>MakeConst.Vsix</AssemblyName>`
>    - <span data-ttu-id="e6228-122">Atualize o `<ProjectReference>` nó na linha 41 para alterar o `TargetFramework` valor:</span><span class="sxs-lookup"><span data-stu-id="e6228-122">Update the `<ProjectReference>` node on line 41 to alter the `TargetFramework` value:</span></span>
>      - `<ProjectReference Update="@(ProjectReference)" AdditionalProperties="TargetFramework=netstandard2.0" />`
> 1. <span data-ttu-id="e6228-123">Atualize o arquivo *MakeConstUnitTests.cs* , no projeto *MakeConst. Test* :</span><span class="sxs-lookup"><span data-stu-id="e6228-123">Update the *MakeConstUnitTests.cs* file, in the *MakeConst.Test* project:</span></span>
>    - <span data-ttu-id="e6228-124">Altere a linha 9 para o seguinte, observe a alteração do namespace:</span><span class="sxs-lookup"><span data-stu-id="e6228-124">Change line 9 to the following, notice namespace alteration:</span></span>
>      - `using Verify = Microsoft.CodeAnalysis.CSharp.Testing.MSTest.CodeFixVerifier<`
>    - <span data-ttu-id="e6228-125">Altere a linha 24 para o seguinte método:</span><span class="sxs-lookup"><span data-stu-id="e6228-125">Change line 24 to the following method:</span></span>
>      - `await Verify.VerifyAnalyzerAsync(test);`
>    - <span data-ttu-id="e6228-126">Altere a linha 62 para o seguinte método:</span><span class="sxs-lookup"><span data-stu-id="e6228-126">Change line 62 to the following method:</span></span>
>      - `await Verify.VerifyCodeFixAsync(test, expected, fixtest);`

- [<span data-ttu-id="e6228-127">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="e6228-127">Visual Studio 2017</span></span>](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
- [<span data-ttu-id="e6228-128">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="e6228-128">Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads)

<span data-ttu-id="e6228-129">Você precisará instalar o **SDK do .net Compiler Platform** por meio do instalador do Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="e6228-129">You'll need to install the **.NET Compiler Platform SDK** via the Visual Studio Installer:</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<span data-ttu-id="e6228-130">Há várias etapas para criar e validar o analisador:</span><span class="sxs-lookup"><span data-stu-id="e6228-130">There are several steps to creating and validating your analyzer:</span></span>

1. <span data-ttu-id="e6228-131">Crie a solução.</span><span class="sxs-lookup"><span data-stu-id="e6228-131">Create the solution.</span></span>
1. <span data-ttu-id="e6228-132">Registre o nome e a descrição do analisador.</span><span class="sxs-lookup"><span data-stu-id="e6228-132">Register the analyzer name and description.</span></span>
1. <span data-ttu-id="e6228-133">Relate os avisos e recomendações do analisador.</span><span class="sxs-lookup"><span data-stu-id="e6228-133">Report analyzer warnings and recommendations.</span></span>
1. <span data-ttu-id="e6228-134">Implemente a correção de código para aceitar as recomendações.</span><span class="sxs-lookup"><span data-stu-id="e6228-134">Implement the code fix to accept recommendations.</span></span>
1. <span data-ttu-id="e6228-135">Melhore a análise por meio de testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="e6228-135">Improve the analysis through unit tests.</span></span>

## <a name="explore-the-analyzer-template"></a><span data-ttu-id="e6228-136">Explorar o modelo do analisador</span><span class="sxs-lookup"><span data-stu-id="e6228-136">Explore the analyzer template</span></span>

<span data-ttu-id="e6228-137">O analisador relata ao usuário quaisquer declarações de variável local que podem ser convertidas em constantes locais.</span><span class="sxs-lookup"><span data-stu-id="e6228-137">Your analyzer reports to the user any local variable declarations that can be converted to local constants.</span></span> <span data-ttu-id="e6228-138">Por exemplo, considere o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="e6228-138">For example, consider the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="e6228-139">No código acima, um valor constante é atribuído a `x`, que nunca é modificado.</span><span class="sxs-lookup"><span data-stu-id="e6228-139">In the code above, `x` is assigned a constant value and is never modified.</span></span> <span data-ttu-id="e6228-140">Ele pode ser declarado usando o modificador `const`:</span><span class="sxs-lookup"><span data-stu-id="e6228-140">It can be declared using the `const` modifier:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="e6228-141">A análise para determinar se uma variável pode ser tornada constante está envolvida, exigindo análise sintática, análise constante da expressão de inicializador e também análise de fluxo de dados, para garantir que nunca ocorram gravações na variável.</span><span class="sxs-lookup"><span data-stu-id="e6228-141">The analysis to determine whether a variable can be made constant is involved, requiring syntactic analysis, constant analysis of the initializer expression and dataflow analysis to ensure that the variable is never written to.</span></span> <span data-ttu-id="e6228-142">O .NET Compiler Platform fornece APIs que facilitam essa análise.</span><span class="sxs-lookup"><span data-stu-id="e6228-142">The .NET Compiler Platform provides APIs that make it easier to perform this analysis.</span></span> <span data-ttu-id="e6228-143">A primeira etapa é criar um novo em projeto de **Analisador com correção de código** do C#.</span><span class="sxs-lookup"><span data-stu-id="e6228-143">The first step is to create a new C# **Analyzer with code fix** project.</span></span>

- <span data-ttu-id="e6228-144">No Visual Studio, escolha **Arquivo > Novo > Projeto...** para exibir a caixa de diálogo Novo Projeto.</span><span class="sxs-lookup"><span data-stu-id="e6228-144">In Visual Studio, choose **File > New > Project...** to display the New Project dialog.</span></span>
- <span data-ttu-id="e6228-145">Em **Visual C# > Extensibilidade**, escolha **Analisador com correção de código (.NET Standard)**.</span><span class="sxs-lookup"><span data-stu-id="e6228-145">Under **Visual C# > Extensibility**, choose **Analyzer with code fix (.NET Standard)**.</span></span>
- <span data-ttu-id="e6228-146">Nomeie seu projeto como "**MakeConst**" e clique em OK.</span><span class="sxs-lookup"><span data-stu-id="e6228-146">Name your project "**MakeConst**" and click OK.</span></span>

<span data-ttu-id="e6228-147">O analisador com modelo de correção de código cria três projetos: um contém o analisador e a correção de código, o segundo é um projeto de teste de unidade e o terceiro é o projeto VSIX.</span><span class="sxs-lookup"><span data-stu-id="e6228-147">The analyzer with code fix template creates three projects: one contains the analyzer and code fix, the second is a unit test project, and the third is the VSIX project.</span></span> <span data-ttu-id="e6228-148">O projeto de inicialização padrão é o projeto VSIX.</span><span class="sxs-lookup"><span data-stu-id="e6228-148">The default startup project is the VSIX project.</span></span> <span data-ttu-id="e6228-149">Pressione <kbd>F5</kbd> para iniciar o projeto VSIX.</span><span class="sxs-lookup"><span data-stu-id="e6228-149">Press <kbd>F5</kbd> to start the VSIX project.</span></span> <span data-ttu-id="e6228-150">Isso inicia uma segunda instância do Visual Studio que tenha carregado o seu novo analisador.</span><span class="sxs-lookup"><span data-stu-id="e6228-150">This starts a second instance of Visual Studio that has loaded your new analyzer.</span></span>

> [!TIP]
> <span data-ttu-id="e6228-151">Quando você executa seu analisador, você pode iniciar uma segunda cópia do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e6228-151">When you run your analyzer, you start a second copy of Visual Studio.</span></span> <span data-ttu-id="e6228-152">Essa segunda cópia usa um hive do Registro diferente para armazenar configurações.</span><span class="sxs-lookup"><span data-stu-id="e6228-152">This second copy uses a different registry hive to store settings.</span></span> <span data-ttu-id="e6228-153">Isso lhe permite diferenciar as configurações visuais em duas cópias do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e6228-153">That enables you to differentiate the visual settings in the two copies of Visual Studio.</span></span> <span data-ttu-id="e6228-154">Você pode escolher um tema diferente para a execução experimental do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e6228-154">You can pick a different theme for the experimental run of Visual Studio.</span></span> <span data-ttu-id="e6228-155">Além disso, não use perfil móvel de suas configurações nem faça logon na conta do Visual Studio usando a execução experimental do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e6228-155">In addition, don't roam your settings or login to your Visual Studio account using the experimental run of Visual Studio.</span></span> <span data-ttu-id="e6228-156">Isso mantém as diferenças entre as configurações.</span><span class="sxs-lookup"><span data-stu-id="e6228-156">That keeps the settings different.</span></span>

<span data-ttu-id="e6228-157">Na segunda instância do Visual Studio que você acabou de iniciar, crie um novo projeto de aplicativo de console em C# (o .NET Core ou .NET Framework projeto funcionará, os analisadores funcionam no nível de origem). Passe o mouse sobre o token com um sublinhado ondulado e o texto de aviso fornecido por um analisador é exibido.</span><span class="sxs-lookup"><span data-stu-id="e6228-157">In the second Visual Studio instance that you just started, create a new C# Console Application project (either .NET Core or .NET Framework project will work -- analyzers work at the source level.) Hover over the token with a wavy underline, and the warning text provided by an analyzer appears.</span></span>

<span data-ttu-id="e6228-158">O modelo cria um analisador que relata um aviso em cada declaração de tipo em que o nome do tipo contém letras minúsculas, conforme mostrado na figura a seguir:</span><span class="sxs-lookup"><span data-stu-id="e6228-158">The template creates an analyzer that reports a warning on each type declaration where the type name contains lowercase letters, as shown in the following figure:</span></span>

![Analisador de aviso de relatórios](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

<span data-ttu-id="e6228-160">O modelo também fornece uma correção de código que altera qualquer nome de tipo que contenha caracteres de letras minúsculas, deixando-o com todas as letras maiúsculas.</span><span class="sxs-lookup"><span data-stu-id="e6228-160">The template also provides a code fix that changes any type name containing lower case characters to all upper case.</span></span> <span data-ttu-id="e6228-161">Você pode clicar na lâmpada exibida com o aviso para ver as alterações sugeridas.</span><span class="sxs-lookup"><span data-stu-id="e6228-161">You can click on the light bulb displayed with the warning to see the suggested changes.</span></span> <span data-ttu-id="e6228-162">Aceitar as alterações sugeridas atualiza o nome do tipo e todas as referências para esse tipo na solução.</span><span class="sxs-lookup"><span data-stu-id="e6228-162">Accepting the suggested changes updates the type name and all references to that type in the solution.</span></span> <span data-ttu-id="e6228-163">Agora que você já viu o analisador inicial em ação, feche a segunda instância do Visual Studio e retorne ao projeto do analisador.</span><span class="sxs-lookup"><span data-stu-id="e6228-163">Now that you've seen the initial analyzer in action, close the second Visual Studio instance and return to your analyzer project.</span></span>

<span data-ttu-id="e6228-164">Você não precisa iniciar uma segunda cópia do Visual Studio e criar um novo código para testar cada alteração em seu analisador.</span><span class="sxs-lookup"><span data-stu-id="e6228-164">You don't have to start a second copy of Visual Studio and create new code to test every change in your analyzer.</span></span> <span data-ttu-id="e6228-165">O modelo também cria um projeto de teste de unidade para você.</span><span class="sxs-lookup"><span data-stu-id="e6228-165">The template also creates a unit test project for you.</span></span> <span data-ttu-id="e6228-166">Esse projeto contém dois testes.</span><span class="sxs-lookup"><span data-stu-id="e6228-166">That project contains two tests.</span></span> <span data-ttu-id="e6228-167">`TestMethod1` mostra o formato típico de um teste que analisa o código sem disparar um diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="e6228-167">`TestMethod1` shows the typical format of a test that analyzes code without triggering a diagnostic.</span></span> <span data-ttu-id="e6228-168">`TestMethod2` mostra o formato de um teste que dispara um diagnóstico e, em seguida, aplica uma correção de código sugerida.</span><span class="sxs-lookup"><span data-stu-id="e6228-168">`TestMethod2` shows the format of a test that triggers a diagnostic, and then applies a suggested code fix.</span></span> <span data-ttu-id="e6228-169">Conforme você cria o analisador e a correção de código, você escreve testes para estruturas de código diferentes para verificar seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="e6228-169">As you build your analyzer and code fix, you'll write tests for different code structures to verify your work.</span></span> <span data-ttu-id="e6228-170">Testes de unidade para os analisadores são muito mais rápidos do que testá-los de forma interativa com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e6228-170">Unit tests for analyzers are much quicker than testing them interactively with Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="e6228-171">Testes de unidade de analisador são uma excelente ferramenta quando você sabe quais constructos de código devem e não devem disparar seu analisador.</span><span class="sxs-lookup"><span data-stu-id="e6228-171">Analyzer unit tests are a great tool when you know what code constructs should and shouldn't trigger your analyzer.</span></span> <span data-ttu-id="e6228-172">Carregar o analisador em outra cópia do Visual Studio é uma excelente ferramenta para explorar e encontrar constructos nos quais você talvez não tenha pensado ainda.</span><span class="sxs-lookup"><span data-stu-id="e6228-172">Loading your analyzer in another copy of Visual Studio is a great tool to explore and find constructs you may not have thought about yet.</span></span>

## <a name="create-analyzer-registrations"></a><span data-ttu-id="e6228-173">Criar registros do analisador</span><span class="sxs-lookup"><span data-stu-id="e6228-173">Create analyzer registrations</span></span>

<span data-ttu-id="e6228-174">O modelo cria a classe inicial `DiagnosticAnalyzer`, no arquivo **MakeConstAnalyzer.cs**.</span><span class="sxs-lookup"><span data-stu-id="e6228-174">The template creates the initial `DiagnosticAnalyzer` class, in the **MakeConstAnalyzer.cs** file.</span></span> <span data-ttu-id="e6228-175">Esse analisador inicial mostra duas propriedades importantes de cada analisador.</span><span class="sxs-lookup"><span data-stu-id="e6228-175">This initial analyzer shows two important properties of every analyzer.</span></span>

- <span data-ttu-id="e6228-176">Cada analisador de diagnóstico deve fornecer um atributo `[DiagnosticAnalyzer]` que descreve a linguagem em que opera.</span><span class="sxs-lookup"><span data-stu-id="e6228-176">Every diagnostic analyzer must provide a `[DiagnosticAnalyzer]` attribute that describes the language it operates on.</span></span>
- <span data-ttu-id="e6228-177">Cada analisador de diagnóstico deve derivar da classe <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer>.</span><span class="sxs-lookup"><span data-stu-id="e6228-177">Every diagnostic analyzer must derive from the <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> class.</span></span>

<span data-ttu-id="e6228-178">O modelo também mostra os recursos básicos que fazem parte de qualquer analisador:</span><span class="sxs-lookup"><span data-stu-id="e6228-178">The template also shows the basic features that are part of any analyzer:</span></span>

1. <span data-ttu-id="e6228-179">Registrar ações.</span><span class="sxs-lookup"><span data-stu-id="e6228-179">Register actions.</span></span> <span data-ttu-id="e6228-180">As ações representam alterações de código que devem disparar o analisador para examinar se há violações de código.</span><span class="sxs-lookup"><span data-stu-id="e6228-180">The actions represent code changes that should trigger your analyzer to examine code for violations.</span></span> <span data-ttu-id="e6228-181">Quando o Visual Studio detecta as edições de código que correspondem a uma ação registrada, ele chama o método registrado do analisador.</span><span class="sxs-lookup"><span data-stu-id="e6228-181">When Visual Studio detects code edits that match a registered action, it calls your analyzer's registered method.</span></span>
1. <span data-ttu-id="e6228-182">Criar diagnósticos.</span><span class="sxs-lookup"><span data-stu-id="e6228-182">Create diagnostics.</span></span> <span data-ttu-id="e6228-183">Quando o analisador detecta uma violação, ele cria um objeto de diagnóstico que o Visual Studio usa para notificar o usuário sobre a violação.</span><span class="sxs-lookup"><span data-stu-id="e6228-183">When your analyzer detects a violation, it creates a diagnostic object that Visual Studio uses to notify the user of the violation.</span></span>

<span data-ttu-id="e6228-184">Registrar ações na substituição do método <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6228-184">You register actions in your override of <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e6228-185">Neste tutorial, você visitará **nós de sintaxe** em busca de declarações locais e verá quais delas têm valores constantes.</span><span class="sxs-lookup"><span data-stu-id="e6228-185">In this tutorial, you'll visit **syntax nodes** looking for local declarations, and see which of those have constant values.</span></span> <span data-ttu-id="e6228-186">Se houver possibilidade de uma declaração ser constante, seu analisador criará e relatará um diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="e6228-186">If a declaration could be constant, your analyzer will create and report a diagnostic.</span></span>

<span data-ttu-id="e6228-187">A primeira etapa é atualizar as constantes de registro e o método `Initialize`, de modo que essas constantes indiquem seu analisador "Make Const".</span><span class="sxs-lookup"><span data-stu-id="e6228-187">The first step is to update the registration constants and `Initialize` method so these constants indicate your "Make Const" analyzer.</span></span> <span data-ttu-id="e6228-188">A maioria das constantes de cadeia de caracteres é definida no arquivo de recurso de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e6228-188">Most of the string constants are defined in the string resource file.</span></span> <span data-ttu-id="e6228-189">Você deve seguir essa prática para uma localização mais fácil.</span><span class="sxs-lookup"><span data-stu-id="e6228-189">You should follow that practice for easier localization.</span></span> <span data-ttu-id="e6228-190">Abra o arquivo **Resources.resx** para o projeto do analisador **MakeConst**.</span><span class="sxs-lookup"><span data-stu-id="e6228-190">Open the **Resources.resx** file for the **MakeConst** analyzer project.</span></span> <span data-ttu-id="e6228-191">Isso exibe o editor de recursos.</span><span class="sxs-lookup"><span data-stu-id="e6228-191">This displays the resource editor.</span></span> <span data-ttu-id="e6228-192">Atualize os recursos de cadeia de caracteres da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e6228-192">Update the string resources as follows:</span></span>

- <span data-ttu-id="e6228-193">Altere `AnalyzerTitle` para "A variável pode ser tornada constante".</span><span class="sxs-lookup"><span data-stu-id="e6228-193">Change `AnalyzerTitle` to "Variable can be made constant".</span></span>
- <span data-ttu-id="e6228-194">Altere `AnalyzerMessageFormat` para "Pode ser tornada constante".</span><span class="sxs-lookup"><span data-stu-id="e6228-194">Change `AnalyzerMessageFormat` to "Can be made constant".</span></span>
- <span data-ttu-id="e6228-195">Altere `AnalyzerDescription` para "Tornar Constante".</span><span class="sxs-lookup"><span data-stu-id="e6228-195">Change `AnalyzerDescription` to "Make Constant".</span></span>

<span data-ttu-id="e6228-196">Além disso, lembre-se de alterar a lista suspensa **Modificador de Acesso** para `public`.</span><span class="sxs-lookup"><span data-stu-id="e6228-196">Also, change the **Access Modifier** drop-down to `public`.</span></span> <span data-ttu-id="e6228-197">Isso facilita o uso dessas constantes em testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="e6228-197">That makes it easier to use these constants in unit tests.</span></span> <span data-ttu-id="e6228-198">Quando você terminar, o editor de recursos deverá aparecer como mostrado na figura a seguir:</span><span class="sxs-lookup"><span data-stu-id="e6228-198">When you have finished, the resource editor should appear as follow figure shows:</span></span>

![Atualizar recursos de cadeia de caracteres](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

<span data-ttu-id="e6228-200">As alterações restantes estão no arquivo do analisador.</span><span class="sxs-lookup"><span data-stu-id="e6228-200">The remaining changes are in the analyzer file.</span></span> <span data-ttu-id="e6228-201">Abra **MakeConstAnalyzer.cs** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e6228-201">Open **MakeConstAnalyzer.cs** in Visual Studio.</span></span> <span data-ttu-id="e6228-202">Altere a ação registrada de uma que age em símbolos para uma que age sobre a sintaxe.</span><span class="sxs-lookup"><span data-stu-id="e6228-202">Change the registered action from one that acts on symbols to one that acts on syntax.</span></span> <span data-ttu-id="e6228-203">No método `MakeConstAnalyzerAnalyzer.Initialize`, localize a linha que registra a ação em símbolos:</span><span class="sxs-lookup"><span data-stu-id="e6228-203">In the `MakeConstAnalyzerAnalyzer.Initialize` method, find the line that registers the action on symbols:</span></span>

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

<span data-ttu-id="e6228-204">Substitua-a com a seguinte linha:</span><span class="sxs-lookup"><span data-stu-id="e6228-204">Replace it with the following line:</span></span>

[!code-csharp[Register the node action](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

<span data-ttu-id="e6228-205">Após essa alteração, você poderá excluir o método `AnalyzeSymbol`.</span><span class="sxs-lookup"><span data-stu-id="e6228-205">After that change, you can delete the `AnalyzeSymbol` method.</span></span> <span data-ttu-id="e6228-206">Este analisador examina <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, e não instruções <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6228-206">This analyzer examines <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, not <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> statements.</span></span> <span data-ttu-id="e6228-207">Observe que `AnalyzeNode` tem rabiscos vermelhos sob ele.</span><span class="sxs-lookup"><span data-stu-id="e6228-207">Notice that `AnalyzeNode` has red squiggles under it.</span></span> <span data-ttu-id="e6228-208">O código apenas que você acaba de adicionar referencia um método `AnalyzeNode` que não foi declarado.</span><span class="sxs-lookup"><span data-stu-id="e6228-208">The code you just added references an `AnalyzeNode` method that hasn't been declared.</span></span> <span data-ttu-id="e6228-209">Declare esse método usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="e6228-209">Declare that method using the following code:</span></span>

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

<span data-ttu-id="e6228-210">Altere o `Category` para "Usage" em **MakeConstAnalyzer.cs**, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="e6228-210">Change the `Category` to "Usage" in **MakeConstAnalyzer.cs** as shown in the following code:</span></span>

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a><span data-ttu-id="e6228-211">Localize as declarações locais que podem ser constantes</span><span class="sxs-lookup"><span data-stu-id="e6228-211">Find local declarations that could be const</span></span>

<span data-ttu-id="e6228-212">É hora de escrever a primeira versão do método `AnalyzeNode`.</span><span class="sxs-lookup"><span data-stu-id="e6228-212">It's time to write the first version of the `AnalyzeNode` method.</span></span> <span data-ttu-id="e6228-213">Ele deve procurar uma única declaração local que poderia ser `const` mas não é, algo semelhante ao seguinte código:</span><span class="sxs-lookup"><span data-stu-id="e6228-213">It should look for a single local declaration that could be `const` but is not, like the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="e6228-214">A primeira etapa é encontrar declarações locais.</span><span class="sxs-lookup"><span data-stu-id="e6228-214">The first step is to find local declarations.</span></span> <span data-ttu-id="e6228-215">Adicione o seguinte código a `AnalyzeNode` em **MakeConstAnalyzer.cs**:</span><span class="sxs-lookup"><span data-stu-id="e6228-215">Add the following code to `AnalyzeNode` in **MakeConstAnalyzer.cs**:</span></span>

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

<span data-ttu-id="e6228-216">Essa conversão sempre terá êxito porque seu analisador fez o registro para alterações unicamente a declarações locais.</span><span class="sxs-lookup"><span data-stu-id="e6228-216">This cast always succeeds because your analyzer registered for changes to local declarations, and only local declarations.</span></span> <span data-ttu-id="e6228-217">Nenhum outro tipo de nó dispara uma chamada para seu método `AnalyzeNode`.</span><span class="sxs-lookup"><span data-stu-id="e6228-217">No other node type triggers a call to your `AnalyzeNode` method.</span></span> <span data-ttu-id="e6228-218">Em seguida, verifique a declaração para quaisquer modificadores `const`.</span><span class="sxs-lookup"><span data-stu-id="e6228-218">Next, check the declaration for any `const` modifiers.</span></span> <span data-ttu-id="e6228-219">Se você encontrá-los, retorne imediatamente.</span><span class="sxs-lookup"><span data-stu-id="e6228-219">If you find them, return immediately.</span></span> <span data-ttu-id="e6228-220">O código a seguir procura por quaisquer modificadores `const` na declaração local:</span><span class="sxs-lookup"><span data-stu-id="e6228-220">The following code looks for any `const` modifiers on the local declaration:</span></span>

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

<span data-ttu-id="e6228-221">Por fim, você precisa verificar que a variável pode ser `const`.</span><span class="sxs-lookup"><span data-stu-id="e6228-221">Finally, you need to check that the variable could be `const`.</span></span> <span data-ttu-id="e6228-222">Isso significa assegurar que ela nunca seja atribuída após ser inicializada.</span><span class="sxs-lookup"><span data-stu-id="e6228-222">That means making sure it is never assigned after it is initialized.</span></span>

<span data-ttu-id="e6228-223">Você executará alguma análise semântica usando o <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span><span class="sxs-lookup"><span data-stu-id="e6228-223">You'll perform some semantic analysis using the <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span></span> <span data-ttu-id="e6228-224">Você usa o argumento `context` para determinar se a declaração de variável local pode ser tornada `const`.</span><span class="sxs-lookup"><span data-stu-id="e6228-224">You use the `context` argument to determine whether the local variable declaration can be made `const`.</span></span> <span data-ttu-id="e6228-225">Um <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> representa todas as informações semânticas em um único arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="e6228-225">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> represents all of semantic information in a single source file.</span></span> <span data-ttu-id="e6228-226">Você pode aprender mais no artigo que aborda [modelos semânticos](../work-with-semantics.md).</span><span class="sxs-lookup"><span data-stu-id="e6228-226">You can learn more in the article that covers [semantic models](../work-with-semantics.md).</span></span> <span data-ttu-id="e6228-227">Você usará o <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> para realizar a análise de fluxo de dados na instrução de declaração local.</span><span class="sxs-lookup"><span data-stu-id="e6228-227">You'll use the <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> to perform data flow analysis on the local declaration statement.</span></span> <span data-ttu-id="e6228-228">Em seguida, você usa os resultados dessa análise de fluxo de dados para garantir que a variável local não seja escrita com um novo valor em nenhum outro lugar.</span><span class="sxs-lookup"><span data-stu-id="e6228-228">Then, you use the results of this data flow analysis to ensure that the local variable isn't written with a new value anywhere else.</span></span> <span data-ttu-id="e6228-229">Chame o método de extensão <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> para recuperar o <xref:Microsoft.CodeAnalysis.ILocalSymbol> para a variável e verifique se ele não está contido na coleção <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> da análise de fluxo de dados.</span><span class="sxs-lookup"><span data-stu-id="e6228-229">Call the <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> extension method to retrieve the <xref:Microsoft.CodeAnalysis.ILocalSymbol> for the variable and check that it isn't contained with the <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> collection of the data flow analysis.</span></span> <span data-ttu-id="e6228-230">Adicione o seguinte código ao final do método `AnalyzeNode`:</span><span class="sxs-lookup"><span data-stu-id="e6228-230">Add the following code to the end of the `AnalyzeNode` method:</span></span>

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

<span data-ttu-id="e6228-231">O código recém-adicionado garante que a variável não seja modificada e pode, portanto, ser tornada `const`.</span><span class="sxs-lookup"><span data-stu-id="e6228-231">The code just added ensures that the variable isn't modified, and can therefore be made `const`.</span></span> <span data-ttu-id="e6228-232">É hora de gerar o diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="e6228-232">It's time to raise the diagnostic.</span></span> <span data-ttu-id="e6228-233">Adicione o código a seguir como a última linha em `AnalyzeNode`:</span><span class="sxs-lookup"><span data-stu-id="e6228-233">Add the following code as the last line in `AnalyzeNode`:</span></span>

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

<span data-ttu-id="e6228-234">Você pode verificar seu andamento pressionando <kbd>F5</kbd> para executar o analisador.</span><span class="sxs-lookup"><span data-stu-id="e6228-234">You can check your progress by pressing <kbd>F5</kbd> to run your analyzer.</span></span> <span data-ttu-id="e6228-235">Você pode carregar o aplicativo de console que você criou anteriormente e, em seguida, adicionar o seguinte código de teste:</span><span class="sxs-lookup"><span data-stu-id="e6228-235">You can load the console application you created earlier and then add the following test code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="e6228-236">A lâmpada deve aparecer e o analisador deve relatar um diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="e6228-236">The light bulb should appear, and your analyzer should report a diagnostic.</span></span> <span data-ttu-id="e6228-237">No entanto, a lâmpada ainda usa a correção de código gerada por modelo, e diz a você que ela pode ser colocada em letras maiúsculas.</span><span class="sxs-lookup"><span data-stu-id="e6228-237">However, the light bulb still uses the template generated code fix, and tells you it can be made upper case.</span></span> <span data-ttu-id="e6228-238">A próxima seção explica como escrever a correção de código.</span><span class="sxs-lookup"><span data-stu-id="e6228-238">The next section explains how to write the code fix.</span></span>

## <a name="write-the-code-fix"></a><span data-ttu-id="e6228-239">Escrever a correção de código</span><span class="sxs-lookup"><span data-stu-id="e6228-239">Write the code fix</span></span>

<span data-ttu-id="e6228-240">Um analisador pode fornecer uma ou mais correções de código.</span><span class="sxs-lookup"><span data-stu-id="e6228-240">An analyzer can provide one or more code fixes.</span></span> <span data-ttu-id="e6228-241">Uma correção de código define uma edição que resolve o problema relatado.</span><span class="sxs-lookup"><span data-stu-id="e6228-241">A code fix defines an edit that addresses the reported issue.</span></span> <span data-ttu-id="e6228-242">Para o analisador que você criou, você pode fornecer uma correção de código que insere a palavra-chave const:</span><span class="sxs-lookup"><span data-stu-id="e6228-242">For the analyzer that you created, you can provide a code fix that inserts the const keyword:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="e6228-243">O usuário escolhe-a da lâmpada da interface do usuário no editor e do Visual Studio altera o código.</span><span class="sxs-lookup"><span data-stu-id="e6228-243">The user chooses it from the light bulb UI in the editor and Visual Studio changes the code.</span></span>

<span data-ttu-id="e6228-244">Abra o arquivo **MakeConstCodeFixProvider.cs** adicionado pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="e6228-244">Open the **MakeConstCodeFixProvider.cs** file added by the template.</span></span>  <span data-ttu-id="e6228-245">Essa correção de código já está conectada à ID de Diagnóstico produzida pelo analisador de diagnóstico, mas ela ainda não implementa a transformação de código correta.</span><span class="sxs-lookup"><span data-stu-id="e6228-245">This code fix is already wired up to the Diagnostic ID produced by your diagnostic analyzer, but it doesn't yet implement the right code transform.</span></span> <span data-ttu-id="e6228-246">Primeiro você deve remover parte do código de modelo.</span><span class="sxs-lookup"><span data-stu-id="e6228-246">First you should remove some of the template code.</span></span> <span data-ttu-id="e6228-247">Altere a cadeia de caracteres do título para "Tornar constante":</span><span class="sxs-lookup"><span data-stu-id="e6228-247">Change the title string to "Make constant":</span></span>

[!code-csharp[Update the CodeFix title](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

<span data-ttu-id="e6228-248">Em seguida, exclua o método `MakeUppercaseAsync`.</span><span class="sxs-lookup"><span data-stu-id="e6228-248">Next, delete the `MakeUppercaseAsync` method.</span></span> <span data-ttu-id="e6228-249">Ele não se aplica mais.</span><span class="sxs-lookup"><span data-stu-id="e6228-249">It no longer applies.</span></span>

<span data-ttu-id="e6228-250">Todos os provedores de correção de código derivam de <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span><span class="sxs-lookup"><span data-stu-id="e6228-250">All code fix providers derive from <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span></span> <span data-ttu-id="e6228-251">Todos eles substituem <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> para relatar as correções de código disponíveis.</span><span class="sxs-lookup"><span data-stu-id="e6228-251">They all override <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> to report available code fixes.</span></span> <span data-ttu-id="e6228-252">Em `RegisterCodeFixesAsync`, altere o tipo de nó ancestral pelo qual você está pesquisando para um <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> para corresponder ao diagnóstico:</span><span class="sxs-lookup"><span data-stu-id="e6228-252">In `RegisterCodeFixesAsync`, change the ancestor node type you're searching for to a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> to match the diagnostic:</span></span>

[!code-csharp[Find local declaration node](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

<span data-ttu-id="e6228-253">Em seguida, altere a última linha para registrar uma correção de código.</span><span class="sxs-lookup"><span data-stu-id="e6228-253">Next, change the last line to register a code fix.</span></span> <span data-ttu-id="e6228-254">A correção criará um novo documento resultante da adição do modificador `const` para uma declaração existente:</span><span class="sxs-lookup"><span data-stu-id="e6228-254">Your fix will create a new document that results from adding the `const` modifier to an existing declaration:</span></span>

[!code-csharp[Register the new code fix](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

<span data-ttu-id="e6228-255">Você observará rabiscos vermelhos no código que você acabou de adicionar no símbolo `MakeConstAsync`.</span><span class="sxs-lookup"><span data-stu-id="e6228-255">You'll notice red squiggles in the code you just added on the symbol `MakeConstAsync`.</span></span> <span data-ttu-id="e6228-256">Adicione uma declaração para `MakeConstAsync` semelhante ao seguinte código:</span><span class="sxs-lookup"><span data-stu-id="e6228-256">Add a declaration for `MakeConstAsync` like the following code:</span></span>

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

<span data-ttu-id="e6228-257">Seu novo método `MakeConstAsync` transformará o <xref:Microsoft.CodeAnalysis.Document> que representa o arquivo de origem do usuário em um novo <xref:Microsoft.CodeAnalysis.Document> que agora contém uma declaração `const`.</span><span class="sxs-lookup"><span data-stu-id="e6228-257">Your new `MakeConstAsync` method will transform the <xref:Microsoft.CodeAnalysis.Document> representing the user's source file into a new <xref:Microsoft.CodeAnalysis.Document> that now contains a `const` declaration.</span></span>

<span data-ttu-id="e6228-258">Você cria um novo token de palavra-chave `const` a ser inserido no início da instrução de declaração.</span><span class="sxs-lookup"><span data-stu-id="e6228-258">You create a new `const` keyword token to insert at the front of the declaration statement.</span></span> <span data-ttu-id="e6228-259">Tenha cuidado para remover qualquer desafio à esquerda do primeiro token de instrução de declaração e anexe-o ao token `const`.</span><span class="sxs-lookup"><span data-stu-id="e6228-259">Be careful to first remove any leading trivia from the first token of the declaration statement and attach it to the `const` token.</span></span> <span data-ttu-id="e6228-260">Adicione o seguinte código ao método `MakeConstAsync`:</span><span class="sxs-lookup"><span data-stu-id="e6228-260">Add the following code to the `MakeConstAsync` method:</span></span>

[!code-csharp[Create a new const keyword token](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

<span data-ttu-id="e6228-261">Em seguida, adicione o token `const` à declaração usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="e6228-261">Next, add the `const` token to the declaration using the following code:</span></span>

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

<span data-ttu-id="e6228-262">Em seguida, formate a nova declaração de acordo com regras de formatação de C#.</span><span class="sxs-lookup"><span data-stu-id="e6228-262">Next, format the new declaration to match C# formatting rules.</span></span> <span data-ttu-id="e6228-263">Formatar de suas alterações para corresponderem ao código existente cria uma experiência melhor.</span><span class="sxs-lookup"><span data-stu-id="e6228-263">Formatting your changes to match existing code creates a better experience.</span></span> <span data-ttu-id="e6228-264">Adicione a instrução a seguir imediatamente após o código existente:</span><span class="sxs-lookup"><span data-stu-id="e6228-264">Add the following statement immediately after the existing code:</span></span>

[!code-csharp[Format the new declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

<span data-ttu-id="e6228-265">Um novo namespace é necessário para esse código.</span><span class="sxs-lookup"><span data-stu-id="e6228-265">A new namespace is required for this code.</span></span> <span data-ttu-id="e6228-266">Adicione a seguinte `using` diretiva à parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="e6228-266">Add the following `using` directive to the top of the file:</span></span>

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

<span data-ttu-id="e6228-267">A etapa final é fazer a edição.</span><span class="sxs-lookup"><span data-stu-id="e6228-267">The final step is to make your edit.</span></span> <span data-ttu-id="e6228-268">Há três etapas para esse processo:</span><span class="sxs-lookup"><span data-stu-id="e6228-268">There are three steps to this process:</span></span>

1. <span data-ttu-id="e6228-269">Obter um identificador para o documento existente.</span><span class="sxs-lookup"><span data-stu-id="e6228-269">Get a handle to the existing document.</span></span>
1. <span data-ttu-id="e6228-270">Criar um novo documento, substituindo a declaração existente pela nova declaração.</span><span class="sxs-lookup"><span data-stu-id="e6228-270">Create a new document by replacing the existing declaration with the new declaration.</span></span>
1. <span data-ttu-id="e6228-271">Retornar o novo documento.</span><span class="sxs-lookup"><span data-stu-id="e6228-271">Return the new document.</span></span>

<span data-ttu-id="e6228-272">Adicione o seguinte código ao final do método `MakeConstAsync`:</span><span class="sxs-lookup"><span data-stu-id="e6228-272">Add the following code to the end of the `MakeConstAsync` method:</span></span>

[!code-csharp[replace the declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

<span data-ttu-id="e6228-273">A correção de código está pronta para ser experimentada.</span><span class="sxs-lookup"><span data-stu-id="e6228-273">Your code fix is ready to try.</span></span>  <span data-ttu-id="e6228-274">Pressione <kbd>F5</kbd> para executar o projeto do analisador em uma segunda instância do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e6228-274">Press <kbd>F5</kbd> to run the analyzer project in a second instance of Visual Studio.</span></span> <span data-ttu-id="e6228-275">Na segunda instância do Visual Studio, crie um novo projeto de Aplicativo de Console em C# e adicione algumas declarações de variável local inicializadas com valores constantes para o método Main.</span><span class="sxs-lookup"><span data-stu-id="e6228-275">In the second Visual Studio instance, create a new C# Console Application project and add a few local variable declarations initialized with constant values to the Main method.</span></span> <span data-ttu-id="e6228-276">Você verá que elas são relatadas como avisos, conforme mostrado a seguir.</span><span class="sxs-lookup"><span data-stu-id="e6228-276">You'll see that they are reported as warnings as below.</span></span>

![Pode fazer avisos constantes](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

<span data-ttu-id="e6228-278">Você fez muito progresso.</span><span class="sxs-lookup"><span data-stu-id="e6228-278">You've made a lot of progress.</span></span> <span data-ttu-id="e6228-279">Há rabiscos sob as declarações que podem ser tornados `const`.</span><span class="sxs-lookup"><span data-stu-id="e6228-279">There are squiggles under the declarations that can be made `const`.</span></span> <span data-ttu-id="e6228-280">Mas ainda há trabalho a fazer.</span><span class="sxs-lookup"><span data-stu-id="e6228-280">But there is still work to do.</span></span> <span data-ttu-id="e6228-281">Isso funciona bem se você adicionar `const` às declarações começando com `i`, depois `j` e, por fim, `k`.</span><span class="sxs-lookup"><span data-stu-id="e6228-281">This works fine if you add `const` to the declarations starting with `i`, then `j` and finally `k`.</span></span> <span data-ttu-id="e6228-282">Mas se você adicionar o modificador `const` em uma ordem diferente, começando com `k`, seu analisador criará erros: `k` não pode ser declarado como `const`, a menos que `i` e `j` já sejam ambos `const`.</span><span class="sxs-lookup"><span data-stu-id="e6228-282">But, if you add the `const` modifier in a different order, starting with `k`, your analyzer creates errors: `k` can't be declared `const`, unless `i` and `j` are both already `const`.</span></span> <span data-ttu-id="e6228-283">Você tem que fazer mais análise para assegurar que lida com as diferentes maneiras em que variáveis podem ser declaradas e inicializadas.</span><span class="sxs-lookup"><span data-stu-id="e6228-283">You've got to do more analysis to ensure you handle the different ways variables can be declared and initialized.</span></span>

## <a name="build-data-driven-tests"></a><span data-ttu-id="e6228-284">Criar testes controlados por dados</span><span class="sxs-lookup"><span data-stu-id="e6228-284">Build data driven tests</span></span>

<span data-ttu-id="e6228-285">Seu analisador e correção de código trabalham em um caso simples de uma única declaração que pode ser tornada const.</span><span class="sxs-lookup"><span data-stu-id="e6228-285">Your analyzer and code fix work on a simple case of a single declaration that can be made const.</span></span> <span data-ttu-id="e6228-286">Há várias instruções de declaração possíveis em que essa implementação comete erros.</span><span class="sxs-lookup"><span data-stu-id="e6228-286">There are numerous possible declaration statements where this implementation makes mistakes.</span></span> <span data-ttu-id="e6228-287">Você tratará desses casos trabalhando com a biblioteca de teste de unidade gravada pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="e6228-287">You'll address these cases by working with the unit test library written by the template.</span></span> <span data-ttu-id="e6228-288">Isso é muito mais rápido do que abrir repetidamente uma segunda cópia do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e6228-288">It's much faster than repeatedly opening a second copy of Visual Studio.</span></span>

<span data-ttu-id="e6228-289">Abra o arquivo **MakeConstUnitTests.cs** no projeto de teste de unidade.</span><span class="sxs-lookup"><span data-stu-id="e6228-289">Open the **MakeConstUnitTests.cs** file in the unit test project.</span></span> <span data-ttu-id="e6228-290">O modelo criou dois testes que seguem os dois padrões comuns para um analisador e o teste de unidade de correção de código.</span><span class="sxs-lookup"><span data-stu-id="e6228-290">The template created two tests that follow the two common patterns for an analyzer and code fix unit test.</span></span> <span data-ttu-id="e6228-291">`TestMethod1` mostra o padrão para um teste que garante que o analisador não relata um diagnóstico quando não deve fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="e6228-291">`TestMethod1` shows the pattern for a test that ensures the analyzer doesn't report a diagnostic when it shouldn't.</span></span> <span data-ttu-id="e6228-292">`TestMethod2` mostra o padrão para relatar um diagnóstico e executar a correção de código.</span><span class="sxs-lookup"><span data-stu-id="e6228-292">`TestMethod2` shows the pattern for reporting a diagnostic and running the code fix.</span></span>

<span data-ttu-id="e6228-293">O código para quase todos os testes para o seu analisador segue um destes dois padrões.</span><span class="sxs-lookup"><span data-stu-id="e6228-293">The code for almost every test for your analyzer follows one of these two patterns.</span></span> <span data-ttu-id="e6228-294">Para a primeira etapa, você pode refazer esses testes como testes controlados por dados.</span><span class="sxs-lookup"><span data-stu-id="e6228-294">For the first step, you can rework these tests as data driven tests.</span></span> <span data-ttu-id="e6228-295">Em seguida, será fácil criar novos testes adicionando novas constantes de cadeia de caracteres para representar diferentes entradas de teste.</span><span class="sxs-lookup"><span data-stu-id="e6228-295">Then, it will be easy to create new tests by adding new string constants to represent different test inputs.</span></span>

<span data-ttu-id="e6228-296">Para obter eficiência, a primeira etapa é refatorar os dois testes em testes controlados por dados.</span><span class="sxs-lookup"><span data-stu-id="e6228-296">For efficiency, the first step is to refactor the two tests into data driven tests.</span></span> <span data-ttu-id="e6228-297">Em seguida, você só precisa definir algumas constantes de cadeia de caracteres para cada novo teste.</span><span class="sxs-lookup"><span data-stu-id="e6228-297">Then, you only need to define a couple string constants for each new test.</span></span> <span data-ttu-id="e6228-298">Enquanto você estiver Refatorando, renomeie os dois métodos para melhores nomes.</span><span class="sxs-lookup"><span data-stu-id="e6228-298">While you are refactoring, rename both methods to better names.</span></span> <span data-ttu-id="e6228-299">Substitua `TestMethod1` com este teste, que garante que nenhum diagnóstico seja gerado:</span><span class="sxs-lookup"><span data-stu-id="e6228-299">Replace `TestMethod1` with this test that ensures no diagnostic is raised:</span></span>

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

<span data-ttu-id="e6228-300">Você pode criar uma nova linha de dados para este teste, definindo qualquer fragmento de código que não faça com que o diagnóstico dispare um aviso.</span><span class="sxs-lookup"><span data-stu-id="e6228-300">You can create a new data row for this test by defining any code fragment that should not cause your diagnostic to trigger a warning.</span></span> <span data-ttu-id="e6228-301">Essa sobrecarga de `VerifyCSharpDiagnostic` passa quando não há nenhum diagnóstico disparado para o fragmento de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="e6228-301">This overload of `VerifyCSharpDiagnostic` passes when there are no diagnostics triggered for the source code fragment.</span></span>

<span data-ttu-id="e6228-302">Em seguida, substitua `TestMethod2` com esse teste que garante que um diagnóstico é gerado e uma correção de código aplicada ao fragmento de código-fonte:</span><span class="sxs-lookup"><span data-stu-id="e6228-302">Next, replace `TestMethod2` with this test that ensures a diagnostic is raised and a code fix applied for the source code fragment:</span></span>

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

<span data-ttu-id="e6228-303">O código anterior também fez algumas alterações no código que cria o resultado de diagnóstico esperado.</span><span class="sxs-lookup"><span data-stu-id="e6228-303">The preceding code also made a couple changes to the code that builds the expected diagnostic result.</span></span> <span data-ttu-id="e6228-304">Ele usa as constantes públicas registradas no analisador `MakeConst`.</span><span class="sxs-lookup"><span data-stu-id="e6228-304">It uses the public constants registered in the `MakeConst` analyzer.</span></span> <span data-ttu-id="e6228-305">Além disso, ele usa duas constantes de cadeia de caracteres para a fonte de entrada e fonte fixa.</span><span class="sxs-lookup"><span data-stu-id="e6228-305">In addition, it uses two string constants for the input and fixed source.</span></span> <span data-ttu-id="e6228-306">Adicione as seguintes constantes de cadeia de caracteres à classe `UnitTest`:</span><span class="sxs-lookup"><span data-stu-id="e6228-306">Add the following string constants to the `UnitTest` class:</span></span>

[!code-csharp[string constants for fix test](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

<span data-ttu-id="e6228-307">Execute esses dois testes para certificar-se de sua aprovação.</span><span class="sxs-lookup"><span data-stu-id="e6228-307">Run these two tests to make sure they pass.</span></span> <span data-ttu-id="e6228-308">No Visual Studio, abra o **Gerenciador de Testes** selecionando **Teste** > **Windows** > **Gerenciador de Testes**.</span><span class="sxs-lookup"><span data-stu-id="e6228-308">In Visual Studio, open the **Test Explorer** by selecting **Test** > **Windows** > **Test Explorer**.</span></span> <span data-ttu-id="e6228-309">Em seguida, selecione o link **executar tudo** .</span><span class="sxs-lookup"><span data-stu-id="e6228-309">Then select the **Run All** link.</span></span>

## <a name="create-tests-for-valid-declarations"></a><span data-ttu-id="e6228-310">Criar testes para declarações válidas</span><span class="sxs-lookup"><span data-stu-id="e6228-310">Create tests for valid declarations</span></span>

<span data-ttu-id="e6228-311">Como regra geral, os analisadores devem sair assim que possível, fazendo o mínimo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e6228-311">As a general rule, analyzers should exit as quickly as possible, doing minimal work.</span></span> <span data-ttu-id="e6228-312">O Visual Studio chama analisadores registrados conforme o usuário edita o código.</span><span class="sxs-lookup"><span data-stu-id="e6228-312">Visual Studio calls registered analyzers as the user edits code.</span></span> <span data-ttu-id="e6228-313">A capacidade de resposta é um requisito fundamental.</span><span class="sxs-lookup"><span data-stu-id="e6228-313">Responsiveness is a key requirement.</span></span> <span data-ttu-id="e6228-314">Há vários casos de teste para o código que não deverão gerar o diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="e6228-314">There are several test cases for code that should not raise your diagnostic.</span></span> <span data-ttu-id="e6228-315">O analisador já gerencia um desses testes, o caso em que uma variável é atribuída após ser inicializada.</span><span class="sxs-lookup"><span data-stu-id="e6228-315">Your analyzer already handles one of those tests, the case where a variable is assigned after being initialized.</span></span> <span data-ttu-id="e6228-316">Adicione a constante de cadeia de caracteres a seguir para seus testes para representar esse caso:</span><span class="sxs-lookup"><span data-stu-id="e6228-316">Add the following string constant to your tests to represent that case:</span></span>

[!code-csharp[variable assigned](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

<span data-ttu-id="e6228-317">Em seguida, adicione uma linha de dados para este teste, conforme mostrado no snippet de código a seguir:</span><span class="sxs-lookup"><span data-stu-id="e6228-317">Then, add a data row for this test as shown in the snippet below:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="e6228-318">Esse teste é aprovado também.</span><span class="sxs-lookup"><span data-stu-id="e6228-318">This test passes as well.</span></span> <span data-ttu-id="e6228-319">Em seguida, adicione as constantes para as condições que você ainda não manipulou ainda:</span><span class="sxs-lookup"><span data-stu-id="e6228-319">Next, add constants for conditions you haven't handled yet:</span></span>

- <span data-ttu-id="e6228-320">Declarações que já são `const`, porque elas já são const:</span><span class="sxs-lookup"><span data-stu-id="e6228-320">Declarations that are already `const`, because they are already const:</span></span>

   [!code-csharp[already const declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- <span data-ttu-id="e6228-321">Declarações que não têm nenhum inicializador, porque não há nenhum valor a ser usado:</span><span class="sxs-lookup"><span data-stu-id="e6228-321">Declarations that have no initializer, because there is no value to use:</span></span>

   [!code-csharp[declarations that have no initializer](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- <span data-ttu-id="e6228-322">Declarações em que o inicializador não é uma constante, porque elas não podem ser constantes de tempo de compilação:</span><span class="sxs-lookup"><span data-stu-id="e6228-322">Declarations where the initializer is not a constant, because they can't be compile-time constants:</span></span>

   [!code-csharp[declarations where the initializer isn't const](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

<span data-ttu-id="e6228-323">Isso pode ser ainda mais complicado, porque o C# permite várias declarações como uma instrução.</span><span class="sxs-lookup"><span data-stu-id="e6228-323">It can be even more complicated because C# allows multiple declarations as one statement.</span></span> <span data-ttu-id="e6228-324">Considere a seguinte constante de cadeia de caracteres de caso de teste:</span><span class="sxs-lookup"><span data-stu-id="e6228-324">Consider the following test case string constant:</span></span>

[!code-csharp[multiple initializers](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

<span data-ttu-id="e6228-325">A variável `i` pode ser tornada constante, mas o mesmo não se aplica à variável `j`.</span><span class="sxs-lookup"><span data-stu-id="e6228-325">The variable `i` can be made constant, but the variable `j` cannot.</span></span> <span data-ttu-id="e6228-326">Portanto, essa instrução não pode ser tornada uma declaração const.</span><span class="sxs-lookup"><span data-stu-id="e6228-326">Therefore, this statement cannot be made a const declaration.</span></span> <span data-ttu-id="e6228-327">Adicione as declarações `DataRow` para todos esses testes:</span><span class="sxs-lookup"><span data-stu-id="e6228-327">Add the `DataRow` declarations for all these tests:</span></span>

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

<span data-ttu-id="e6228-328">Execute os testes novamente e você verá esses novos casos de teste falharem.</span><span class="sxs-lookup"><span data-stu-id="e6228-328">Run your tests again, and you'll see these new test cases fail.</span></span>

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a><span data-ttu-id="e6228-329">Atualize seu analisador para ignorar as declarações corretas</span><span class="sxs-lookup"><span data-stu-id="e6228-329">Update your analyzer to ignore correct declarations</span></span>

<span data-ttu-id="e6228-330">Você precisa de algumas melhorias no método `AnalyzeNode` do analisador para filtrar o código que corresponde a essas condições.</span><span class="sxs-lookup"><span data-stu-id="e6228-330">You need some enhancements to your analyzer's `AnalyzeNode` method to filter out code that matches these conditions.</span></span> <span data-ttu-id="e6228-331">Elas são todas condições relacionadas, portanto, alterações semelhantes corrigirão todas essas condições.</span><span class="sxs-lookup"><span data-stu-id="e6228-331">They are all related conditions, so similar changes will fix all these conditions.</span></span> <span data-ttu-id="e6228-332">Faça as alterações a seguir em `AnalyzeNode`:</span><span class="sxs-lookup"><span data-stu-id="e6228-332">Make the following changes to `AnalyzeNode`:</span></span>

- <span data-ttu-id="e6228-333">A análise semântica examinou uma única declaração de variável.</span><span class="sxs-lookup"><span data-stu-id="e6228-333">Your semantic analysis examined a single variable declaration.</span></span> <span data-ttu-id="e6228-334">Esse código deve estar em um loop de `foreach` que examina todas as variáveis declaradas na mesma instrução.</span><span class="sxs-lookup"><span data-stu-id="e6228-334">This code needs to be in a `foreach` loop that examines all the variables declared in the same statement.</span></span>
- <span data-ttu-id="e6228-335">Cada variável declarada precisa ter um inicializador.</span><span class="sxs-lookup"><span data-stu-id="e6228-335">Each declared variable needs to have an initializer.</span></span>
- <span data-ttu-id="e6228-336">O inicializador de cada variável declarada precisa ser uma constante de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="e6228-336">Each declared variable's initializer must be a compile-time constant.</span></span>

<span data-ttu-id="e6228-337">No seu método `AnalyzeNode`, substitua a análise semântica original:</span><span class="sxs-lookup"><span data-stu-id="e6228-337">In your `AnalyzeNode` method, replace the original semantic analysis:</span></span>

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

<span data-ttu-id="e6228-338">com o snippet de código a seguir:</span><span class="sxs-lookup"><span data-stu-id="e6228-338">with the following code snippet:</span></span>

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

<span data-ttu-id="e6228-339">O primeiro loop de `foreach` examina cada declaração de variável usando a análise sintática.</span><span class="sxs-lookup"><span data-stu-id="e6228-339">The first `foreach` loop examines each variable declaration using syntactic analysis.</span></span> <span data-ttu-id="e6228-340">A primeira verificação garante que a variável tenha um inicializador.</span><span class="sxs-lookup"><span data-stu-id="e6228-340">The first check guarantees that the variable has an initializer.</span></span> <span data-ttu-id="e6228-341">A segunda verificação garante que o inicializador seja uma constante.</span><span class="sxs-lookup"><span data-stu-id="e6228-341">The second check guarantees that the initializer is a constant.</span></span> <span data-ttu-id="e6228-342">O segundo loop tem a análise semântica original.</span><span class="sxs-lookup"><span data-stu-id="e6228-342">The second loop has the original semantic analysis.</span></span> <span data-ttu-id="e6228-343">As verificações semânticas estão em um loop separado porque ele tem um impacto maior no desempenho.</span><span class="sxs-lookup"><span data-stu-id="e6228-343">The semantic checks are in a separate loop because it has a greater impact on performance.</span></span> <span data-ttu-id="e6228-344">Execute os testes novamente e você deverá ver todos eles serem aprovados.</span><span class="sxs-lookup"><span data-stu-id="e6228-344">Run your tests again, and you should see them all pass.</span></span>

## <a name="add-the-final-polish"></a><span data-ttu-id="e6228-345">Adicionar o final polonês</span><span class="sxs-lookup"><span data-stu-id="e6228-345">Add the final polish</span></span>

<span data-ttu-id="e6228-346">Você está quase lá.</span><span class="sxs-lookup"><span data-stu-id="e6228-346">You're almost done.</span></span> <span data-ttu-id="e6228-347">Há mais algumas condições com as quais o seu analisador deve lidar.</span><span class="sxs-lookup"><span data-stu-id="e6228-347">There are a few more conditions for your analyzer to handle.</span></span> <span data-ttu-id="e6228-348">Enquanto o usuário está escrevendo código, o Visual Studio chama os analisadores.</span><span class="sxs-lookup"><span data-stu-id="e6228-348">Visual Studio calls analyzers while the user is writing code.</span></span> <span data-ttu-id="e6228-349">Muitas vezes o analisador será chamado para código que não é compilado.</span><span class="sxs-lookup"><span data-stu-id="e6228-349">It's often the case that your analyzer will be called for code that doesn't compile.</span></span> <span data-ttu-id="e6228-350">O método `AnalyzeNode` do analisador de diagnóstico não verifica para ver se o valor da constante é conversível para o tipo de variável.</span><span class="sxs-lookup"><span data-stu-id="e6228-350">The diagnostic analyzer's `AnalyzeNode` method does not check to see if the constant value is convertible to the variable type.</span></span> <span data-ttu-id="e6228-351">Assim, a implementação atual converterá facilmente uma declaração incorreta, tal como int i = "abc", em uma constante local.</span><span class="sxs-lookup"><span data-stu-id="e6228-351">So, the current implementation will happily convert an incorrect declaration such as int i = "abc"' to a local constant.</span></span> <span data-ttu-id="e6228-352">Adicione uma constante de cadeia de caracteres de origem para essa condição:</span><span class="sxs-lookup"><span data-stu-id="e6228-352">Add a source string constant for that condition:</span></span>

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

<span data-ttu-id="e6228-353">Além disso, os tipos de referência não são tratados corretamente.</span><span class="sxs-lookup"><span data-stu-id="e6228-353">In addition, reference types are not handled properly.</span></span> <span data-ttu-id="e6228-354">O único valor de constante permitido para um tipo de referência é `null`, exceto no caso de <xref:System.String?displayProperty=nameWithType>, que permite literais de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e6228-354">The only constant value allowed for a reference type is `null`, except in this case of <xref:System.String?displayProperty=nameWithType>, which allows string literals.</span></span> <span data-ttu-id="e6228-355">Em outras palavras, `const string s = "abc"` é legal, mas `const object s = "abc"` não é.</span><span class="sxs-lookup"><span data-stu-id="e6228-355">In other words, `const string s = "abc"` is legal, but `const object s = "abc"` is not.</span></span> <span data-ttu-id="e6228-356">Este snippet de código verifica essa condição:</span><span class="sxs-lookup"><span data-stu-id="e6228-356">This code snippet verifies that condition:</span></span>

[!code-csharp[Reference types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

<span data-ttu-id="e6228-357">Para ser criterioso, você precisará adicionar outro teste para verificar se pode criar uma declaração de constante para uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e6228-357">To be thorough, you need to add another test to make sure that you can create a constant declaration for a string.</span></span> <span data-ttu-id="e6228-358">O snippet de código a seguir define o código que gera o diagnóstico e o código após a aplicação da correção:</span><span class="sxs-lookup"><span data-stu-id="e6228-358">The following snippet defines both the code that raises the diagnostic, and the code after the fix has been applied:</span></span>

[!code-csharp[string reference types raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

<span data-ttu-id="e6228-359">Por fim, se uma variável é declarada com a palavra-chave `var`, a correção de código faz a coisa errada e gera uma declaração `const var`, que não é compatível com a linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="e6228-359">Finally, if a variable is declared with the `var` keyword, the code fix does the wrong thing and generates a `const var` declaration, which is not supported by the C# language.</span></span> <span data-ttu-id="e6228-360">Para corrigir esse bug, a correção de código deve substituir a palavra-chave `var` pelo nome do tipo inferido:</span><span class="sxs-lookup"><span data-stu-id="e6228-360">To fix this bug, the code fix must replace the `var` keyword with the inferred type's name:</span></span>

[!code-csharp[var references need to use the inferred types](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

<span data-ttu-id="e6228-361">Essas alterações atualizam as declarações de linha de dados para ambos os testes.</span><span class="sxs-lookup"><span data-stu-id="e6228-361">These changes update the data row declarations for both tests.</span></span> <span data-ttu-id="e6228-362">O código a seguir mostra esses testes com todos os atributos de linha de dados:</span><span class="sxs-lookup"><span data-stu-id="e6228-362">The following code shows these tests with all data row attributes:</span></span>

[!code-csharp[The finished tests](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

<span data-ttu-id="e6228-363">Felizmente, todos os erros acima podem ser resolvidos usando as mesmas técnicas que você acabou de aprender.</span><span class="sxs-lookup"><span data-stu-id="e6228-363">Fortunately, all of the above bugs can be addressed using the same techniques that you just learned.</span></span>

<span data-ttu-id="e6228-364">Para corrigir o primeiro bug, primeiro abra **DiagnosticAnalyzer.cs** e localize o loop foreach em que cada um dos inicializadores de declaração local é verificado para garantir que valores constantes sejam atribuídos a eles.</span><span class="sxs-lookup"><span data-stu-id="e6228-364">To fix the first bug, first open **DiagnosticAnalyzer.cs** and locate the foreach loop where each of the local declaration's initializers are checked to ensure that they're assigned with constant values.</span></span> <span data-ttu-id="e6228-365">Imediatamente _antes_ do primeiro loop foreach, chame `context.SemanticModel.GetTypeInfo()` para recuperar informações detalhadas sobre o tipo declarado da declaração local:</span><span class="sxs-lookup"><span data-stu-id="e6228-365">Immediately _before_ the first foreach loop, call `context.SemanticModel.GetTypeInfo()` to retrieve detailed information about the declared type of the local declaration:</span></span>

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

<span data-ttu-id="e6228-366">Em seguida, dentro do loop `foreach`, verifique cada inicializador para garantir que ele pode ser convertido no tipo de variável.</span><span class="sxs-lookup"><span data-stu-id="e6228-366">Then, inside your `foreach` loop, check each initializer to make sure it's convertible to the variable type.</span></span> <span data-ttu-id="e6228-367">Adicione a seguinte verificação depois de garantir que o inicializador é uma constante:</span><span class="sxs-lookup"><span data-stu-id="e6228-367">Add the following check after ensuring that the initializer is a constant:</span></span>

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

<span data-ttu-id="e6228-368">A próxima alteração é realizada com base na última.</span><span class="sxs-lookup"><span data-stu-id="e6228-368">The next change builds upon the last one.</span></span> <span data-ttu-id="e6228-369">Antes da chave de fechamento do primeiro loop foreach, adicione o código a seguir para verificar o tipo da declaração de local quando a constante é uma cadeia de caracteres ou valor nulo.</span><span class="sxs-lookup"><span data-stu-id="e6228-369">Before the closing curly brace of the first foreach loop, add the following code to check the type of the local declaration when the constant is a string or null.</span></span>

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

<span data-ttu-id="e6228-370">Você deve escrever um pouco mais de código no provedor de correção de código para substituir a `var` palavra-chave pelo nome de tipo correto.</span><span class="sxs-lookup"><span data-stu-id="e6228-370">You must write a bit more code in your code fix provider to replace the `var` keyword with the correct type name.</span></span> <span data-ttu-id="e6228-371">Retorne ao **CodeFixProvider.cs**.</span><span class="sxs-lookup"><span data-stu-id="e6228-371">Return to **CodeFixProvider.cs**.</span></span> <span data-ttu-id="e6228-372">O código que você adicionará realizará as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="e6228-372">The code you'll add does the following steps:</span></span>

- <span data-ttu-id="e6228-373">Verifique se a declaração é uma declaração `var` e se afirmativo:</span><span class="sxs-lookup"><span data-stu-id="e6228-373">Check if the declaration is a `var` declaration, and if it is:</span></span>
- <span data-ttu-id="e6228-374">Crie um novo tipo para o tipo inferido.</span><span class="sxs-lookup"><span data-stu-id="e6228-374">Create a new type for the inferred type.</span></span>
- <span data-ttu-id="e6228-375">Certifique-se de que a declaração de tipo não é um alias.</span><span class="sxs-lookup"><span data-stu-id="e6228-375">Make sure the type declaration is not an alias.</span></span> <span data-ttu-id="e6228-376">Em caso afirmativo, é legal declarar `const var`.</span><span class="sxs-lookup"><span data-stu-id="e6228-376">If so, it is legal to declare `const var`.</span></span>
- <span data-ttu-id="e6228-377">Certifique-se de que `var` não é um nome de tipo neste programa.</span><span class="sxs-lookup"><span data-stu-id="e6228-377">Make sure that `var` isn't a type name in this program.</span></span> <span data-ttu-id="e6228-378">(Em caso afirmativo, `const var` é legal).</span><span class="sxs-lookup"><span data-stu-id="e6228-378">(If so, `const var` is legal).</span></span>
- <span data-ttu-id="e6228-379">Simplificar o nome completo do tipo</span><span class="sxs-lookup"><span data-stu-id="e6228-379">Simplify the full type name</span></span>

<span data-ttu-id="e6228-380">Isso soa como muito código.</span><span class="sxs-lookup"><span data-stu-id="e6228-380">That sounds like a lot of code.</span></span> <span data-ttu-id="e6228-381">Mas não é.</span><span class="sxs-lookup"><span data-stu-id="e6228-381">It's not.</span></span> <span data-ttu-id="e6228-382">Substitua a linha que declara e inicializa `newLocal` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e6228-382">Replace the line that declares and initializes `newLocal` with the following code.</span></span> <span data-ttu-id="e6228-383">Ele é colocado imediatamente após a inicialização de `newModifiers`:</span><span class="sxs-lookup"><span data-stu-id="e6228-383">It goes immediately after the initialization of `newModifiers`:</span></span>

[!code-csharp[Replace Var designations](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

<span data-ttu-id="e6228-384">Você precisará adicionar uma `using` diretiva para usar o <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> tipo:</span><span class="sxs-lookup"><span data-stu-id="e6228-384">You'll need to add one `using` directive to use the <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> type:</span></span>

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

<span data-ttu-id="e6228-385">Execute seus testes, que devem todos ser aprovados.</span><span class="sxs-lookup"><span data-stu-id="e6228-385">Run your tests, and they should all pass.</span></span> <span data-ttu-id="e6228-386">Dê parabéns a si mesmo, executando seu analisador concluído.</span><span class="sxs-lookup"><span data-stu-id="e6228-386">Congratulate yourself by running your finished analyzer.</span></span> <span data-ttu-id="e6228-387">Pressione <kbd>Ctrl</kbd> + <kbd>F5</kbd> para executar o projeto do analisador em uma segunda instância do Visual Studio com a extensão de visualização do Roslyn carregada.</span><span class="sxs-lookup"><span data-stu-id="e6228-387">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the analyzer project in a second instance of Visual Studio with the Roslyn Preview extension loaded.</span></span>

- <span data-ttu-id="e6228-388">Na segunda instância do Visual Studio, crie um novo projeto de Aplicativo de Console de C# e adicione `int x = "abc";` ao método Main.</span><span class="sxs-lookup"><span data-stu-id="e6228-388">In the second Visual Studio instance, create a new C# Console Application project and add `int x = "abc";` to the Main method.</span></span> <span data-ttu-id="e6228-389">Graças à primeira correção de bug, nenhum aviso deve ser relatado para esta declaração de variável local (embora haja um erro do compilador, conforme esperado).</span><span class="sxs-lookup"><span data-stu-id="e6228-389">Thanks to the first bug fix, no warning should be reported for this local variable declaration (though there's a compiler error as expected).</span></span>
- <span data-ttu-id="e6228-390">Em seguida, adicione `object s = "abc";` ao método Main.</span><span class="sxs-lookup"><span data-stu-id="e6228-390">Next, add `object s = "abc";` to the Main method.</span></span> <span data-ttu-id="e6228-391">Devido à segunda correção de bug, nenhum aviso deve ser relatado.</span><span class="sxs-lookup"><span data-stu-id="e6228-391">Because of the second bug fix, no warning should be reported.</span></span>
- <span data-ttu-id="e6228-392">Por fim, adicione outra variável local que usa a palavra-chave `var`.</span><span class="sxs-lookup"><span data-stu-id="e6228-392">Finally, add another local variable that uses the `var` keyword.</span></span> <span data-ttu-id="e6228-393">Você verá que um aviso é relatado e uma sugestão é exibida abaixo e a esquerda.</span><span class="sxs-lookup"><span data-stu-id="e6228-393">You'll see that a warning is reported and a suggestion appears beneath to the left.</span></span>
- <span data-ttu-id="e6228-394">Mova o cursor do editor sobre o sublinhado ondulado e pressione <kbd>Ctrl</kbd> + <kbd>.</kbd>.</span><span class="sxs-lookup"><span data-stu-id="e6228-394">Move the editor caret over the squiggly underline and press <kbd>Ctrl</kbd>+<kbd>.</kbd>.</span></span> <span data-ttu-id="e6228-395">para exibir a correção de código sugerida.</span><span class="sxs-lookup"><span data-stu-id="e6228-395">to display the suggested code fix.</span></span> <span data-ttu-id="e6228-396">Ao selecionar a correção de código, observe que a `var` palavra-chave agora é manipulada corretamente.</span><span class="sxs-lookup"><span data-stu-id="e6228-396">Upon selecting your code fix, note that the `var` keyword is now handled correctly.</span></span>

<span data-ttu-id="e6228-397">Por fim, adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="e6228-397">Finally, add the following code:</span></span>

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

<span data-ttu-id="e6228-398">Após essas alterações, você obtém linhas onduladas vermelhas apenas nas duas primeiras variáveis.</span><span class="sxs-lookup"><span data-stu-id="e6228-398">After these changes, you get red squiggles only on the first two variables.</span></span> <span data-ttu-id="e6228-399">Adicione `const` para ambos `i` e `j`, e você receberá um novo aviso em `k` porque ele agora pode ser `const`.</span><span class="sxs-lookup"><span data-stu-id="e6228-399">Add `const` to both `i` and `j`, and you get a new warning on `k` because it can now be `const`.</span></span>

<span data-ttu-id="e6228-400">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="e6228-400">Congratulations!</span></span> <span data-ttu-id="e6228-401">Você criou sua primeira extensão do .NET Compiler Platform que executa análise de código com o sistema em funcionamento para detectar um problema e fornece uma correção rápida para corrigi-lo.</span><span class="sxs-lookup"><span data-stu-id="e6228-401">You've created your first .NET Compiler Platform extension that performs on-the-fly code analysis to detect an issue and provides a quick fix to correct it.</span></span> <span data-ttu-id="e6228-402">Ao longo do caminho, você aprendeu muitas das APIs de código que fazem parte do SDK do .NET Compiler Platform (APIs do Roslyn).</span><span class="sxs-lookup"><span data-stu-id="e6228-402">Along the way, you've learned many of the code APIs that are part of the .NET Compiler Platform SDK (Roslyn APIs).</span></span> <span data-ttu-id="e6228-403">Você pode verificar seu trabalho comparando-o à [amostra concluída](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) em nosso repositório GitHub de exemplos.</span><span class="sxs-lookup"><span data-stu-id="e6228-403">You can check your work against the [completed sample](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) in our samples GitHub repository.</span></span>

## <a name="other-resources"></a><span data-ttu-id="e6228-404">Outros recursos</span><span class="sxs-lookup"><span data-stu-id="e6228-404">Other resources</span></span>

- [<span data-ttu-id="e6228-405">Introdução à análise de sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6228-405">Get started with syntax analysis</span></span>](../get-started/syntax-analysis.md)
- [<span data-ttu-id="e6228-406">Introdução à análise semântica</span><span class="sxs-lookup"><span data-stu-id="e6228-406">Get started with semantic analysis</span></span>](../get-started/semantic-analysis.md)
