---
title: Como compilar condicionalmente com Trace e Debug
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
caps.latest.revision: 11
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ee67d687b52bd911597fb99e6f1316e8a9cf5fe0
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="0db61-102">Como compilar condicionalmente com Trace e Debug</span><span class="sxs-lookup"><span data-stu-id="0db61-102">How to: Compile Conditionally with Trace and Debug</span></span>
<span data-ttu-id="0db61-103">Enquanto você estiver depurando um aplicativo durante o desenvolvimento, a saída de rastreamento e de depuração é enviada para a janela de Saída no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0db61-103">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="0db61-104">No entanto, para incluir recursos de rastreamento em um aplicativo implantado, compile os aplicativos instrumentados com a diretiva do compilador **TRACE** habilitada.</span><span class="sxs-lookup"><span data-stu-id="0db61-104">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="0db61-105">Isso permite que o código de rastreamento seja compilado na versão de lançamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0db61-105">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="0db61-106">Se você não habilitar a diretiva **TRACE**, todo o código de rastreamento será ignorado durante a compilação e não será incluído no código executável que será implantado.</span><span class="sxs-lookup"><span data-stu-id="0db61-106">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="0db61-107">Os métodos de rastreamento e de depuração têm atributos condicionais associados.</span><span class="sxs-lookup"><span data-stu-id="0db61-107">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="0db61-108">Por exemplo, se o atributo condicional do rastreamento for **true**, todas as instruções de rastreamento serão incluídas em um assembly (um arquivo .exe ou .dll compilado); se o atributo condicional de **Trace** for **false**, as instruções de rastreamento não serão incluídas.</span><span class="sxs-lookup"><span data-stu-id="0db61-108">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="0db61-109">É possível ativar o atributo condicional **Trace** ou **Debug** em um build, ambos ou nenhum.</span><span class="sxs-lookup"><span data-stu-id="0db61-109">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="0db61-110">Portanto, há quatro tipos de build: **Debug**, **Trace**, ambos ou nenhum.</span><span class="sxs-lookup"><span data-stu-id="0db61-110">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="0db61-111">Alguns builds de versão para implantação de produção podem não conter nenhum dos dois; a maioria dos builds de depuração contém ambos.</span><span class="sxs-lookup"><span data-stu-id="0db61-111">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="0db61-112">É possível especificar as configurações do compilador para o aplicativo de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="0db61-112">You can specify the compiler settings for your application in several ways:</span></span>  
  
-   <span data-ttu-id="0db61-113">As páginas de propriedades</span><span class="sxs-lookup"><span data-stu-id="0db61-113">The property pages</span></span>  
  
-   <span data-ttu-id="0db61-114">A linha de comando</span><span class="sxs-lookup"><span data-stu-id="0db61-114">The command line</span></span>  
  
-   <span data-ttu-id="0db61-115">**#CONST** (para o Visual Basic) e **#define** (para o C#)</span><span class="sxs-lookup"><span data-stu-id="0db61-115">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="0db61-116">Para alterar as configurações de compilação na caixa de diálogo das páginas de propriedades</span><span class="sxs-lookup"><span data-stu-id="0db61-116">To change compile settings from the property pages dialog box</span></span>  
  
1.  <span data-ttu-id="0db61-117">Clique com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="0db61-117">Right-click the project node in **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="0db61-118">Escolha **Propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="0db61-118">Choose **Properties** from the shortcut menu.</span></span>  
  
    -   <span data-ttu-id="0db61-119">No Visual Basic, clique na guia **Compilar** no painel esquerdo da página de propriedades e, em seguida, clique no botão **Opções Avançadas de Compilação** para exibir a caixa de diálogo **Configurações Avançadas do Compilador**.</span><span class="sxs-lookup"><span data-stu-id="0db61-119">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="0db61-120">Marque as caixas de seleção para as configurações do compilador que você deseja habilitar.</span><span class="sxs-lookup"><span data-stu-id="0db61-120">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="0db61-121">Desmarque as caixas de seleção das configurações que você deseja desabilitar.</span><span class="sxs-lookup"><span data-stu-id="0db61-121">Clear the check boxes for settings you want to disable.</span></span>  
  
    -   <span data-ttu-id="0db61-122">No C#, clique na guia **Compilar** no painel esquerdo da página de propriedades e, em seguida, marque as caixas de seleção para as configurações do compilador que você deseja habilitar.</span><span class="sxs-lookup"><span data-stu-id="0db61-122">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="0db61-123">Desmarque as caixas de seleção das configurações que você deseja desabilitar.</span><span class="sxs-lookup"><span data-stu-id="0db61-123">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="0db61-124">Para compilar um código instrumentado usando a linha de comando</span><span class="sxs-lookup"><span data-stu-id="0db61-124">To compile instrumented code using the command line</span></span>  
  
1.  <span data-ttu-id="0db61-125">Defina uma opção de compilador condicional na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="0db61-125">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="0db61-126">O compilador incluirá o código de rastreamento ou de depuração no executável.</span><span class="sxs-lookup"><span data-stu-id="0db61-126">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="0db61-127">Por exemplo, a seguinte instrução do compilador inserida na linha de comando incluirá o código de rastreamento em um executável compilado:</span><span class="sxs-lookup"><span data-stu-id="0db61-127">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="0db61-128">Para o Visual Basic: **vbc /r:System.dll /d:TRACE=TRUE /d:DEBUG=FALSE MyApplication.vb**</span><span class="sxs-lookup"><span data-stu-id="0db61-128">For Visual Basic: **vbc /r:System.dll /d:TRACE=TRUE /d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="0db61-129">Para o C#: **csc /r:System.dll /d:TRACE /d:DEBUG=FALSE MyApplication.cs**</span><span class="sxs-lookup"><span data-stu-id="0db61-129">For C#: **csc /r:System.dll /d:TRACE /d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="0db61-130">Para compilar mais de um arquivo de aplicativo, deixe um espaço em branco entre os nomes de arquivo, por exemplo, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** ou **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="0db61-130">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="0db61-131">O significado das diretivas de compilação condicional usadas nos exemplos acima é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0db61-131">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="0db61-132">Diretiva</span><span class="sxs-lookup"><span data-stu-id="0db61-132">Directive</span></span>|<span data-ttu-id="0db61-133">Significado</span><span class="sxs-lookup"><span data-stu-id="0db61-133">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="0db61-134">compilador do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0db61-134">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="0db61-135">Compilador C#</span><span class="sxs-lookup"><span data-stu-id="0db61-135">C# compiler</span></span>|  
    |`/r:`|<span data-ttu-id="0db61-136">Referencia um assembly externo (EXE ou DLL)</span><span class="sxs-lookup"><span data-stu-id="0db61-136">References an external assembly (EXE or DLL)</span></span>|  
    |`/d:`|<span data-ttu-id="0db61-137">Define um símbolo de compilação condicional</span><span class="sxs-lookup"><span data-stu-id="0db61-137">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="0db61-138">É necessário escrever TRACE ou DEBUG com letras maiúsculas.</span><span class="sxs-lookup"><span data-stu-id="0db61-138">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="0db61-139">Para obter mais informações sobre os comandos de compilação condicional, insira `vbc /?` (para o Visual Basic) ou `csc /?` (para o C#) no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="0db61-139">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="0db61-140">Para obter mais informações, consulte [Compilando por meio da linha de comando](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) ou [Invocando o compilador de linha de comando](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="0db61-140">For more information, see [Building from the Command Line](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="0db61-141">Para executar a compilação condicional usando #CONST ou #define</span><span class="sxs-lookup"><span data-stu-id="0db61-141">To perform conditional compilation using #CONST or #define</span></span>  
  
1.  <span data-ttu-id="0db61-142">Digite a instrução apropriada para a linguagem de programação na parte superior do arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="0db61-142">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="0db61-143">Linguagem</span><span class="sxs-lookup"><span data-stu-id="0db61-143">Language</span></span>|<span data-ttu-id="0db61-144">Instrução</span><span class="sxs-lookup"><span data-stu-id="0db61-144">Statement</span></span>|<span data-ttu-id="0db61-145">Resultado</span><span class="sxs-lookup"><span data-stu-id="0db61-145">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="0db61-146">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="0db61-146">**Visual Basic**</span></span>|<span data-ttu-id="0db61-147">**#CONST TRACE = true**</span><span class="sxs-lookup"><span data-stu-id="0db61-147">**#CONST TRACE = true**</span></span>|<span data-ttu-id="0db61-148">Habilita o rastreamento</span><span class="sxs-lookup"><span data-stu-id="0db61-148">Enables tracing</span></span>|  
    ||<span data-ttu-id="0db61-149">**#CONST TRACE = false**</span><span class="sxs-lookup"><span data-stu-id="0db61-149">**#CONST TRACE = false**</span></span>|<span data-ttu-id="0db61-150">Desabilita o rastreamento</span><span class="sxs-lookup"><span data-stu-id="0db61-150">Disables tracing</span></span>|  
    ||<span data-ttu-id="0db61-151">**#CONST DEBUG = true**</span><span class="sxs-lookup"><span data-stu-id="0db61-151">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="0db61-152">Habilita a depuração</span><span class="sxs-lookup"><span data-stu-id="0db61-152">Enables debugging</span></span>|  
    ||<span data-ttu-id="0db61-153">**#CONST DEBUG = false**</span><span class="sxs-lookup"><span data-stu-id="0db61-153">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="0db61-154">Desabilita a depuração</span><span class="sxs-lookup"><span data-stu-id="0db61-154">Disables debugging</span></span>|  
    |<span data-ttu-id="0db61-155">**C#**</span><span class="sxs-lookup"><span data-stu-id="0db61-155">**C#**</span></span>|<span data-ttu-id="0db61-156">**#define TRACE**</span><span class="sxs-lookup"><span data-stu-id="0db61-156">**#define TRACE**</span></span>|<span data-ttu-id="0db61-157">Habilita o rastreamento</span><span class="sxs-lookup"><span data-stu-id="0db61-157">Enables tracing</span></span>|  
    ||<span data-ttu-id="0db61-158">**#undef TRACE**</span><span class="sxs-lookup"><span data-stu-id="0db61-158">**#undef TRACE**</span></span>|<span data-ttu-id="0db61-159">Desabilita o rastreamento</span><span class="sxs-lookup"><span data-stu-id="0db61-159">Disables tracing</span></span>|  
    ||<span data-ttu-id="0db61-160">**#define DEBUG**</span><span class="sxs-lookup"><span data-stu-id="0db61-160">**#define DEBUG**</span></span>|<span data-ttu-id="0db61-161">Habilita a depuração</span><span class="sxs-lookup"><span data-stu-id="0db61-161">Enables debugging</span></span>|  
    ||<span data-ttu-id="0db61-162">**#undef DEBUG**</span><span class="sxs-lookup"><span data-stu-id="0db61-162">**#undef DEBUG**</span></span>|<span data-ttu-id="0db61-163">Desabilita a depuração</span><span class="sxs-lookup"><span data-stu-id="0db61-163">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="0db61-164">Para desabilitar o rastreamento ou a depuração</span><span class="sxs-lookup"><span data-stu-id="0db61-164">To disable tracing or debugging</span></span>  
  
1.  <span data-ttu-id="0db61-165">Exclua a diretiva do compilador do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="0db61-165">Delete the compiler directive from your source code.</span></span>  
  
     <span data-ttu-id="0db61-166">\- ou -</span><span class="sxs-lookup"><span data-stu-id="0db61-166">\- or -</span></span>  
  
2.  <span data-ttu-id="0db61-167">Comente a diretiva do compilador.</span><span class="sxs-lookup"><span data-stu-id="0db61-167">Comment out the compiler directive.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0db61-168">Quando você estiver pronto para compilar, escolha **Compilar** no menu **Compilar** ou use o método de linha de comando, mas sem digitar o **d:** para definir símbolos de compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="0db61-168">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0db61-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0db61-169">See Also</span></span>  
 <span data-ttu-id="0db61-170">[Rastreando e instrumentando aplicativos](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md) </span><span class="sxs-lookup"><span data-stu-id="0db61-170">[Tracing and Instrumenting Applications](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md) </span></span>  
 <span data-ttu-id="0db61-171">[Como criar, inicializar e configurar opções de rastreamento](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md) </span><span class="sxs-lookup"><span data-stu-id="0db61-171">[How to: Create, Initialize and Configure Trace Switches](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md) </span></span>  
 <span data-ttu-id="0db61-172">[Opções de rastreamento](../../../docs/framework/debug-trace-profile/trace-switches.md) </span><span class="sxs-lookup"><span data-stu-id="0db61-172">[Trace Switches](../../../docs/framework/debug-trace-profile/trace-switches.md) </span></span>  
 <span data-ttu-id="0db61-173">[Ouvintes de rastreamento](../../../docs/framework/debug-trace-profile/trace-listeners.md) </span><span class="sxs-lookup"><span data-stu-id="0db61-173">[Trace Listeners](../../../docs/framework/debug-trace-profile/trace-listeners.md) </span></span>  
 <span data-ttu-id="0db61-174">[Como adicionar instruções de rastreamento ao código do aplicativo](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md) </span><span class="sxs-lookup"><span data-stu-id="0db61-174">[How to: Add Trace Statements to Application Code](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md) </span></span>  
 <span data-ttu-id="0db61-175">[Como Configurar Variáveis de Ambiente para a Linha de Comando do Visual Studio](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) </span><span class="sxs-lookup"><span data-stu-id="0db61-175">[How to: Set Environment Variables for the Visual Studio Command Line](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) </span></span>  
 [<span data-ttu-id="0db61-176">Como invocar o compilador de linha de comando</span><span class="sxs-lookup"><span data-stu-id="0db61-176">How to: Invoke the Command-Line Compiler</span></span>](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)

