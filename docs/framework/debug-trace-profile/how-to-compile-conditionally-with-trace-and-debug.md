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
ms.openlocfilehash: df1f1c7e28464781a73a0939c3413f4c9d620d7d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942381"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="013d2-102">Como: compilar condicionalmente com Trace e Debug</span><span class="sxs-lookup"><span data-stu-id="013d2-102">How to: Compile Conditionally with Trace and Debug</span></span>
<span data-ttu-id="013d2-103">Enquanto você estiver depurando um aplicativo durante o desenvolvimento, a saída de rastreamento e de depuração é enviada para a janela de Saída no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="013d2-103">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="013d2-104">No entanto, para incluir recursos de rastreamento em um aplicativo implantado, compile os aplicativos instrumentados com a diretiva do compilador **TRACE** habilitada.</span><span class="sxs-lookup"><span data-stu-id="013d2-104">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="013d2-105">Isso permite que o código de rastreamento seja compilado na versão de lançamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="013d2-105">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="013d2-106">Se você não habilitar a diretiva **TRACE**, todo o código de rastreamento será ignorado durante a compilação e não será incluído no código executável que será implantado.</span><span class="sxs-lookup"><span data-stu-id="013d2-106">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="013d2-107">Os métodos de rastreamento e de depuração têm atributos condicionais associados.</span><span class="sxs-lookup"><span data-stu-id="013d2-107">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="013d2-108">Por exemplo, se o atributo condicional do rastreamento for **true**, todas as instruções de rastreamento serão incluídas em um assembly (um arquivo .exe ou .dll compilado); se o atributo condicional de **Trace** for **false**, as instruções de rastreamento não serão incluídas.</span><span class="sxs-lookup"><span data-stu-id="013d2-108">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="013d2-109">É possível ativar o atributo condicional **Trace** ou **Debug** em um build, ambos ou nenhum.</span><span class="sxs-lookup"><span data-stu-id="013d2-109">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="013d2-110">Portanto, há quatro tipos de compilação: **Depurar**, **rastrear**, ambos ou nenhum.</span><span class="sxs-lookup"><span data-stu-id="013d2-110">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="013d2-111">Alguns builds de versão para implantação de produção podem não conter nenhum dos dois; a maioria dos builds de depuração contém ambos.</span><span class="sxs-lookup"><span data-stu-id="013d2-111">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="013d2-112">É possível especificar as configurações do compilador para o aplicativo de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="013d2-112">You can specify the compiler settings for your application in several ways:</span></span>  
  
- <span data-ttu-id="013d2-113">As páginas de propriedades</span><span class="sxs-lookup"><span data-stu-id="013d2-113">The property pages</span></span>  
  
- <span data-ttu-id="013d2-114">A linha de comando</span><span class="sxs-lookup"><span data-stu-id="013d2-114">The command line</span></span>  
  
- <span data-ttu-id="013d2-115">**#CONST** (para o Visual Basic) e **#define** (para o C#)</span><span class="sxs-lookup"><span data-stu-id="013d2-115">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="013d2-116">Para alterar as configurações de compilação na caixa de diálogo das páginas de propriedades</span><span class="sxs-lookup"><span data-stu-id="013d2-116">To change compile settings from the property pages dialog box</span></span>  
  
1. <span data-ttu-id="013d2-117">Clique com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="013d2-117">Right-click the project node in **Solution Explorer**.</span></span>  
  
2. <span data-ttu-id="013d2-118">Escolha **Propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="013d2-118">Choose **Properties** from the shortcut menu.</span></span>  
  
    - <span data-ttu-id="013d2-119">No Visual Basic, clique na guia **Compilar** no painel esquerdo da página de propriedades e, em seguida, clique no botão **Opções Avançadas de Compilação** para exibir a caixa de diálogo **Configurações Avançadas do Compilador**.</span><span class="sxs-lookup"><span data-stu-id="013d2-119">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="013d2-120">Marque as caixas de seleção para as configurações do compilador que você deseja habilitar.</span><span class="sxs-lookup"><span data-stu-id="013d2-120">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="013d2-121">Desmarque as caixas de seleção das configurações que você deseja desabilitar.</span><span class="sxs-lookup"><span data-stu-id="013d2-121">Clear the check boxes for settings you want to disable.</span></span>  
  
    - <span data-ttu-id="013d2-122">No C#, clique na guia **Compilar** no painel esquerdo da página de propriedades e, em seguida, marque as caixas de seleção para as configurações do compilador que você deseja habilitar.</span><span class="sxs-lookup"><span data-stu-id="013d2-122">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="013d2-123">Desmarque as caixas de seleção das configurações que você deseja desabilitar.</span><span class="sxs-lookup"><span data-stu-id="013d2-123">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="013d2-124">Para compilar um código instrumentado usando a linha de comando</span><span class="sxs-lookup"><span data-stu-id="013d2-124">To compile instrumented code using the command line</span></span>  
  
1. <span data-ttu-id="013d2-125">Defina uma opção de compilador condicional na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="013d2-125">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="013d2-126">O compilador incluirá o código de rastreamento ou de depuração no executável.</span><span class="sxs-lookup"><span data-stu-id="013d2-126">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="013d2-127">Por exemplo, a seguinte instrução do compilador inserida na linha de comando incluirá o código de rastreamento em um executável compilado:</span><span class="sxs-lookup"><span data-stu-id="013d2-127">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="013d2-128">Para Visual Basic: **Vbc-r:System.dll-d:TRACE = True-d:debug = false MyApplication. vb**</span><span class="sxs-lookup"><span data-stu-id="013d2-128">For Visual Basic: **vbc -r:System.dll -d:TRACE=TRUE -d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="013d2-129">Para C#: **CSC-r:System.dll-d:Trace-d:debug = false MyApplication.cs**</span><span class="sxs-lookup"><span data-stu-id="013d2-129">For C#: **csc -r:System.dll -d:TRACE -d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="013d2-130">Para compilar mais de um arquivo de aplicativo, deixe um espaço em branco entre os nomes de arquivo, por exemplo, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** ou **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="013d2-130">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="013d2-131">O significado das diretivas de compilação condicional usadas nos exemplos acima é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="013d2-131">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="013d2-132">Diretiva</span><span class="sxs-lookup"><span data-stu-id="013d2-132">Directive</span></span>|<span data-ttu-id="013d2-133">Significado</span><span class="sxs-lookup"><span data-stu-id="013d2-133">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="013d2-134">compilador do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="013d2-134">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="013d2-135">Compilador C#</span><span class="sxs-lookup"><span data-stu-id="013d2-135">C# compiler</span></span>|  
    |`-r:`|<span data-ttu-id="013d2-136">Referencia um assembly externo (EXE ou DLL)</span><span class="sxs-lookup"><span data-stu-id="013d2-136">References an external assembly (EXE or DLL)</span></span>|  
    |`-d:`|<span data-ttu-id="013d2-137">Define um símbolo de compilação condicional</span><span class="sxs-lookup"><span data-stu-id="013d2-137">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="013d2-138">É necessário escrever TRACE ou DEBUG com letras maiúsculas.</span><span class="sxs-lookup"><span data-stu-id="013d2-138">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="013d2-139">Para obter mais informações sobre os comandos de compilação condicional, insira `vbc /?` (para o Visual Basic) ou `csc /?` (para o C#) no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="013d2-139">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="013d2-140">Para obter mais informações, consulte [Compilando por meio da linha de comando](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) ou [Invocando o compilador de linha de comando](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="013d2-140">For more information, see [Building from the Command Line](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="013d2-141">Para executar a compilação condicional usando #CONST ou #define</span><span class="sxs-lookup"><span data-stu-id="013d2-141">To perform conditional compilation using #CONST or #define</span></span>  
  
1. <span data-ttu-id="013d2-142">Digite a instrução apropriada para a linguagem de programação na parte superior do arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="013d2-142">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="013d2-143">Idioma</span><span class="sxs-lookup"><span data-stu-id="013d2-143">Language</span></span>|<span data-ttu-id="013d2-144">Instrução</span><span class="sxs-lookup"><span data-stu-id="013d2-144">Statement</span></span>|<span data-ttu-id="013d2-145">Resultado</span><span class="sxs-lookup"><span data-stu-id="013d2-145">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="013d2-146">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="013d2-146">**Visual Basic**</span></span>|<span data-ttu-id="013d2-147">**#CONST TRACE = true**</span><span class="sxs-lookup"><span data-stu-id="013d2-147">**#CONST TRACE = true**</span></span>|<span data-ttu-id="013d2-148">Habilita o rastreamento</span><span class="sxs-lookup"><span data-stu-id="013d2-148">Enables tracing</span></span>|  
    ||<span data-ttu-id="013d2-149">**#CONST TRACE = false**</span><span class="sxs-lookup"><span data-stu-id="013d2-149">**#CONST TRACE = false**</span></span>|<span data-ttu-id="013d2-150">Desabilita o rastreamento</span><span class="sxs-lookup"><span data-stu-id="013d2-150">Disables tracing</span></span>|  
    ||<span data-ttu-id="013d2-151">**#CONST DEBUG = true**</span><span class="sxs-lookup"><span data-stu-id="013d2-151">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="013d2-152">Habilita a depuração</span><span class="sxs-lookup"><span data-stu-id="013d2-152">Enables debugging</span></span>|  
    ||<span data-ttu-id="013d2-153">**#CONST DEBUG = false**</span><span class="sxs-lookup"><span data-stu-id="013d2-153">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="013d2-154">Desabilita a depuração</span><span class="sxs-lookup"><span data-stu-id="013d2-154">Disables debugging</span></span>|  
    |<span data-ttu-id="013d2-155">**C#**</span><span class="sxs-lookup"><span data-stu-id="013d2-155">**C#**</span></span>|<span data-ttu-id="013d2-156">**#define TRACE**</span><span class="sxs-lookup"><span data-stu-id="013d2-156">**#define TRACE**</span></span>|<span data-ttu-id="013d2-157">Habilita o rastreamento</span><span class="sxs-lookup"><span data-stu-id="013d2-157">Enables tracing</span></span>|  
    ||<span data-ttu-id="013d2-158">**#undef TRACE**</span><span class="sxs-lookup"><span data-stu-id="013d2-158">**#undef TRACE**</span></span>|<span data-ttu-id="013d2-159">Desabilita o rastreamento</span><span class="sxs-lookup"><span data-stu-id="013d2-159">Disables tracing</span></span>|  
    ||<span data-ttu-id="013d2-160">**#define DEBUG**</span><span class="sxs-lookup"><span data-stu-id="013d2-160">**#define DEBUG**</span></span>|<span data-ttu-id="013d2-161">Habilita a depuração</span><span class="sxs-lookup"><span data-stu-id="013d2-161">Enables debugging</span></span>|  
    ||<span data-ttu-id="013d2-162">**#undef DEBUG**</span><span class="sxs-lookup"><span data-stu-id="013d2-162">**#undef DEBUG**</span></span>|<span data-ttu-id="013d2-163">Desabilita a depuração</span><span class="sxs-lookup"><span data-stu-id="013d2-163">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="013d2-164">Para desabilitar o rastreamento ou a depuração</span><span class="sxs-lookup"><span data-stu-id="013d2-164">To disable tracing or debugging</span></span>  
  
<span data-ttu-id="013d2-165">Exclua a diretiva do compilador do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="013d2-165">Delete the compiler directive from your source code.</span></span>  
  
<span data-ttu-id="013d2-166">\- ou -</span><span class="sxs-lookup"><span data-stu-id="013d2-166">\- or -</span></span>  
  
<span data-ttu-id="013d2-167">Comente a diretiva do compilador.</span><span class="sxs-lookup"><span data-stu-id="013d2-167">Comment out the compiler directive.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="013d2-168">Quando você estiver pronto para compilar, escolha **Compilar** no menu **Compilar** ou use o método de linha de comando, mas sem digitar o **d:** para definir símbolos de compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="013d2-168">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="013d2-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="013d2-169">See also</span></span>

- [<span data-ttu-id="013d2-170">Rastreando e instrumentando aplicativos</span><span class="sxs-lookup"><span data-stu-id="013d2-170">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="013d2-171">Como: Criar, inicializar e configurar opções de rastreamento</span><span class="sxs-lookup"><span data-stu-id="013d2-171">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="013d2-172">Opções de rastreamento</span><span class="sxs-lookup"><span data-stu-id="013d2-172">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="013d2-173">Ouvintes de rastreamento</span><span class="sxs-lookup"><span data-stu-id="013d2-173">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [<span data-ttu-id="013d2-174">Como: Adicionar instruções de rastreamento ao código do aplicativo</span><span class="sxs-lookup"><span data-stu-id="013d2-174">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="013d2-175">Como: Definir variáveis de ambiente para a linha de comando do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="013d2-175">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [<span data-ttu-id="013d2-176">Como: invocar o compilador de linha de comando</span><span class="sxs-lookup"><span data-stu-id="013d2-176">How to: Invoke the Command-Line Compiler</span></span>](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
