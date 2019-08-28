---
title: 'Como: compilar condicionalmente com Trace e Debug'
ms.date: 03/30/2017
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1692b93e09ec972e537e4a375774eeeb865bd58c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043423"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="5229b-102">Como: compilar condicionalmente com Trace e Debug</span><span class="sxs-lookup"><span data-stu-id="5229b-102">How to: Compile Conditionally with Trace and Debug</span></span>
<span data-ttu-id="5229b-103">Enquanto você estiver depurando um aplicativo durante o desenvolvimento, a saída de rastreamento e de depuração é enviada para a janela de Saída no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5229b-103">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="5229b-104">No entanto, para incluir recursos de rastreamento em um aplicativo implantado, compile os aplicativos instrumentados com a diretiva do compilador **TRACE** habilitada.</span><span class="sxs-lookup"><span data-stu-id="5229b-104">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="5229b-105">Isso permite que o código de rastreamento seja compilado na versão de lançamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5229b-105">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="5229b-106">Se você não habilitar a diretiva **TRACE**, todo o código de rastreamento será ignorado durante a compilação e não será incluído no código executável que será implantado.</span><span class="sxs-lookup"><span data-stu-id="5229b-106">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="5229b-107">Os métodos de rastreamento e de depuração têm atributos condicionais associados.</span><span class="sxs-lookup"><span data-stu-id="5229b-107">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="5229b-108">Por exemplo, se o atributo condicional do rastreamento for **true**, todas as instruções de rastreamento serão incluídas em um assembly (um arquivo .exe ou .dll compilado); se o atributo condicional de **Trace** for **false**, as instruções de rastreamento não serão incluídas.</span><span class="sxs-lookup"><span data-stu-id="5229b-108">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="5229b-109">É possível ativar o atributo condicional **Trace** ou **Debug** em um build, ambos ou nenhum.</span><span class="sxs-lookup"><span data-stu-id="5229b-109">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="5229b-110">Portanto, há quatro tipos de compilação: **Depurar**, **rastrear**, ambos ou nenhum.</span><span class="sxs-lookup"><span data-stu-id="5229b-110">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="5229b-111">Alguns builds de versão para implantação de produção podem não conter nenhum dos dois; a maioria dos builds de depuração contém ambos.</span><span class="sxs-lookup"><span data-stu-id="5229b-111">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="5229b-112">É possível especificar as configurações do compilador para o aplicativo de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="5229b-112">You can specify the compiler settings for your application in several ways:</span></span>  
  
- <span data-ttu-id="5229b-113">As páginas de propriedades</span><span class="sxs-lookup"><span data-stu-id="5229b-113">The property pages</span></span>  
  
- <span data-ttu-id="5229b-114">A linha de comando</span><span class="sxs-lookup"><span data-stu-id="5229b-114">The command line</span></span>  
  
- <span data-ttu-id="5229b-115">**#CONST** (para o Visual Basic) e **#define** (para o C#)</span><span class="sxs-lookup"><span data-stu-id="5229b-115">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="5229b-116">Para alterar as configurações de compilação na caixa de diálogo das páginas de propriedades</span><span class="sxs-lookup"><span data-stu-id="5229b-116">To change compile settings from the property pages dialog box</span></span>  
  
1. <span data-ttu-id="5229b-117">Clique com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="5229b-117">Right-click the project node in **Solution Explorer**.</span></span>  
  
2. <span data-ttu-id="5229b-118">Escolha **Propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="5229b-118">Choose **Properties** from the shortcut menu.</span></span>  
  
    - <span data-ttu-id="5229b-119">No Visual Basic, clique na guia **Compilar** no painel esquerdo da página de propriedades e, em seguida, clique no botão **Opções Avançadas de Compilação** para exibir a caixa de diálogo **Configurações Avançadas do Compilador**.</span><span class="sxs-lookup"><span data-stu-id="5229b-119">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="5229b-120">Marque as caixas de seleção para as configurações do compilador que você deseja habilitar.</span><span class="sxs-lookup"><span data-stu-id="5229b-120">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="5229b-121">Desmarque as caixas de seleção das configurações que você deseja desabilitar.</span><span class="sxs-lookup"><span data-stu-id="5229b-121">Clear the check boxes for settings you want to disable.</span></span>  
  
    - <span data-ttu-id="5229b-122">No C#, clique na guia **Compilar** no painel esquerdo da página de propriedades e, em seguida, marque as caixas de seleção para as configurações do compilador que você deseja habilitar.</span><span class="sxs-lookup"><span data-stu-id="5229b-122">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="5229b-123">Desmarque as caixas de seleção das configurações que você deseja desabilitar.</span><span class="sxs-lookup"><span data-stu-id="5229b-123">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="5229b-124">Para compilar um código instrumentado usando a linha de comando</span><span class="sxs-lookup"><span data-stu-id="5229b-124">To compile instrumented code using the command line</span></span>  
  
1. <span data-ttu-id="5229b-125">Defina uma opção de compilador condicional na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="5229b-125">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="5229b-126">O compilador incluirá o código de rastreamento ou de depuração no executável.</span><span class="sxs-lookup"><span data-stu-id="5229b-126">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="5229b-127">Por exemplo, a seguinte instrução do compilador inserida na linha de comando incluirá o código de rastreamento em um executável compilado:</span><span class="sxs-lookup"><span data-stu-id="5229b-127">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="5229b-128">Para Visual Basic: **Vbc-r:System.dll-d:TRACE = True-d:debug = false MyApplication. vb**</span><span class="sxs-lookup"><span data-stu-id="5229b-128">For Visual Basic: **vbc -r:System.dll -d:TRACE=TRUE -d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="5229b-129">Para C#: **CSC-r:System.dll-d:Trace-d:debug = false MyApplication.cs**</span><span class="sxs-lookup"><span data-stu-id="5229b-129">For C#: **csc -r:System.dll -d:TRACE -d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="5229b-130">Para compilar mais de um arquivo de aplicativo, deixe um espaço em branco entre os nomes de arquivo, por exemplo, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** ou **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="5229b-130">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="5229b-131">O significado das diretivas de compilação condicional usadas nos exemplos acima é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5229b-131">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="5229b-132">Diretiva</span><span class="sxs-lookup"><span data-stu-id="5229b-132">Directive</span></span>|<span data-ttu-id="5229b-133">Significado</span><span class="sxs-lookup"><span data-stu-id="5229b-133">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="5229b-134">compilador do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5229b-134">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="5229b-135">Compilador C#</span><span class="sxs-lookup"><span data-stu-id="5229b-135">C# compiler</span></span>|  
    |`-r:`|<span data-ttu-id="5229b-136">Referencia um assembly externo (EXE ou DLL)</span><span class="sxs-lookup"><span data-stu-id="5229b-136">References an external assembly (EXE or DLL)</span></span>|  
    |`-d:`|<span data-ttu-id="5229b-137">Define um símbolo de compilação condicional</span><span class="sxs-lookup"><span data-stu-id="5229b-137">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="5229b-138">É necessário escrever TRACE ou DEBUG com letras maiúsculas.</span><span class="sxs-lookup"><span data-stu-id="5229b-138">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="5229b-139">Para obter mais informações sobre os comandos de compilação condicional, insira `vbc /?` (para o Visual Basic) ou `csc /?` (para o C#) no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="5229b-139">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="5229b-140">Para obter mais informações, consulte [Compilando por meio da linha de comando](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) ou [Invocando o compilador de linha de comando](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5229b-140">For more information, see [Building from the Command Line](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="5229b-141">Para executar a compilação condicional usando #CONST ou #define</span><span class="sxs-lookup"><span data-stu-id="5229b-141">To perform conditional compilation using #CONST or #define</span></span>  
  
1. <span data-ttu-id="5229b-142">Digite a instrução apropriada para a linguagem de programação na parte superior do arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="5229b-142">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="5229b-143">Idioma</span><span class="sxs-lookup"><span data-stu-id="5229b-143">Language</span></span>|<span data-ttu-id="5229b-144">Instrução</span><span class="sxs-lookup"><span data-stu-id="5229b-144">Statement</span></span>|<span data-ttu-id="5229b-145">Resultado</span><span class="sxs-lookup"><span data-stu-id="5229b-145">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="5229b-146">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="5229b-146">**Visual Basic**</span></span>|<span data-ttu-id="5229b-147">**#CONST TRACE = true**</span><span class="sxs-lookup"><span data-stu-id="5229b-147">**#CONST TRACE = true**</span></span>|<span data-ttu-id="5229b-148">Habilita o rastreamento</span><span class="sxs-lookup"><span data-stu-id="5229b-148">Enables tracing</span></span>|  
    ||<span data-ttu-id="5229b-149">**#CONST TRACE = false**</span><span class="sxs-lookup"><span data-stu-id="5229b-149">**#CONST TRACE = false**</span></span>|<span data-ttu-id="5229b-150">Desabilita o rastreamento</span><span class="sxs-lookup"><span data-stu-id="5229b-150">Disables tracing</span></span>|  
    ||<span data-ttu-id="5229b-151">**#CONST DEBUG = true**</span><span class="sxs-lookup"><span data-stu-id="5229b-151">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="5229b-152">Habilita a depuração</span><span class="sxs-lookup"><span data-stu-id="5229b-152">Enables debugging</span></span>|  
    ||<span data-ttu-id="5229b-153">**#CONST DEBUG = false**</span><span class="sxs-lookup"><span data-stu-id="5229b-153">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="5229b-154">Desabilita a depuração</span><span class="sxs-lookup"><span data-stu-id="5229b-154">Disables debugging</span></span>|  
    |<span data-ttu-id="5229b-155">**C#**</span><span class="sxs-lookup"><span data-stu-id="5229b-155">**C#**</span></span>|<span data-ttu-id="5229b-156">**#define TRACE**</span><span class="sxs-lookup"><span data-stu-id="5229b-156">**#define TRACE**</span></span>|<span data-ttu-id="5229b-157">Habilita o rastreamento</span><span class="sxs-lookup"><span data-stu-id="5229b-157">Enables tracing</span></span>|  
    ||<span data-ttu-id="5229b-158">**#undef TRACE**</span><span class="sxs-lookup"><span data-stu-id="5229b-158">**#undef TRACE**</span></span>|<span data-ttu-id="5229b-159">Desabilita o rastreamento</span><span class="sxs-lookup"><span data-stu-id="5229b-159">Disables tracing</span></span>|  
    ||<span data-ttu-id="5229b-160">**#define DEBUG**</span><span class="sxs-lookup"><span data-stu-id="5229b-160">**#define DEBUG**</span></span>|<span data-ttu-id="5229b-161">Habilita a depuração</span><span class="sxs-lookup"><span data-stu-id="5229b-161">Enables debugging</span></span>|  
    ||<span data-ttu-id="5229b-162">**#undef DEBUG**</span><span class="sxs-lookup"><span data-stu-id="5229b-162">**#undef DEBUG**</span></span>|<span data-ttu-id="5229b-163">Desabilita a depuração</span><span class="sxs-lookup"><span data-stu-id="5229b-163">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="5229b-164">Para desabilitar o rastreamento ou a depuração</span><span class="sxs-lookup"><span data-stu-id="5229b-164">To disable tracing or debugging</span></span>  
  
<span data-ttu-id="5229b-165">Exclua a diretiva do compilador do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="5229b-165">Delete the compiler directive from your source code.</span></span>  
  
<span data-ttu-id="5229b-166">\- ou -</span><span class="sxs-lookup"><span data-stu-id="5229b-166">\- or -</span></span>  
  
<span data-ttu-id="5229b-167">Comente a diretiva do compilador.</span><span class="sxs-lookup"><span data-stu-id="5229b-167">Comment out the compiler directive.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5229b-168">Quando você estiver pronto para compilar, escolha **Compilar** no menu **Compilar** ou use o método de linha de comando, mas sem digitar o **d:** para definir símbolos de compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="5229b-168">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5229b-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5229b-169">See also</span></span>

- [<span data-ttu-id="5229b-170">Rastreando e instrumentando aplicativos</span><span class="sxs-lookup"><span data-stu-id="5229b-170">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="5229b-171">Como: Criar, inicializar e configurar opções de rastreamento</span><span class="sxs-lookup"><span data-stu-id="5229b-171">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="5229b-172">Opções de rastreamento</span><span class="sxs-lookup"><span data-stu-id="5229b-172">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="5229b-173">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="5229b-173">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [<span data-ttu-id="5229b-174">Como: Adicionar instruções de rastreamento ao código do aplicativo</span><span class="sxs-lookup"><span data-stu-id="5229b-174">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="5229b-175">Como: Definir variáveis de ambiente para a linha de comando do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5229b-175">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [<span data-ttu-id="5229b-176">Como: invocar o compilador de linha de comando</span><span class="sxs-lookup"><span data-stu-id="5229b-176">How to: Invoke the Command-Line Compiler</span></span>](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
