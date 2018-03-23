---
title: -/vbruntime
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6c6529fabddc75fb6ac751e0314011f05db7869
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-vbruntime"></a><span data-ttu-id="e955e-102">-/vbruntime</span><span class="sxs-lookup"><span data-stu-id="e955e-102">-vbruntime</span></span>
<span data-ttu-id="e955e-103">Especifica que o compilador deve compilar sem uma referência à biblioteca de tempo de execução do Visual Basic, ou com uma referência a uma biblioteca de tempo de execução específica.</span><span class="sxs-lookup"><span data-stu-id="e955e-103">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e955e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e955e-104">Syntax</span></span>  
  
```  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a><span data-ttu-id="e955e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e955e-105">Arguments</span></span>  
 \-  
 <span data-ttu-id="e955e-106">Compile sem uma referência à biblioteca de tempo de execução do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e955e-106">Compile without a reference to the Visual Basic Runtime Library.</span></span>  
  
 \+  
 <span data-ttu-id="e955e-107">Compile com uma referência à biblioteca de tempo de execução do Visual Basic padrão.</span><span class="sxs-lookup"><span data-stu-id="e955e-107">Compile with a reference to the default Visual Basic Runtime Library.</span></span>  
  
 \*  
 <span data-ttu-id="e955e-108">Compilar sem uma referência à biblioteca de tempo de execução do Visual Basic e inserir a funcionalidade básica da biblioteca de tempo de execução do Visual Basic no assembly.</span><span class="sxs-lookup"><span data-stu-id="e955e-108">Compile without a reference to the Visual Basic Runtime Library, and embed core functionality from the Visual Basic Runtime Library into the assembly.</span></span>  
  
 `path`  
 <span data-ttu-id="e955e-109">Compile com uma referência à biblioteca especificada (DLL).</span><span class="sxs-lookup"><span data-stu-id="e955e-109">Compile with a reference to the specified library (DLL).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e955e-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="e955e-110">Remarks</span></span>  
 <span data-ttu-id="e955e-111">O `-vbruntime` opção de compilador permite que você especifique que o compilador deve compilar sem uma referência à biblioteca de tempo de execução do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e955e-111">The `-vbruntime` compiler option enables you to specify that the compiler should compile without a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="e955e-112">Se você compilar sem uma referência à biblioteca de tempo de execução do Visual Basic, erros ou avisos serão registrados em construções de código ou linguagem que geram uma chamada para um auxiliar de tempo de execução do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e955e-112">If you compile without a reference to the Visual Basic Runtime Library, errors or warnings are logged on code or language constructs that generate a call to a Visual Basic runtime helper.</span></span> <span data-ttu-id="e955e-113">(Um *auxiliar de tempo de execução do Visual Basic* é uma função definida no Microsoft.VisualBasic.dll que é chamado em tempo de execução para executar uma semântica de linguagem específica.)</span><span class="sxs-lookup"><span data-stu-id="e955e-113">(A *Visual Basic runtime helper* is a function defined in Microsoft.VisualBasic.dll that is called at runtime to execute a specific language semantic.)</span></span>  
  
 <span data-ttu-id="e955e-114">O `-vbruntime+` opção produz o mesmo comportamento que ocorre se nenhuma `-vbruntime` opção é especificada.</span><span class="sxs-lookup"><span data-stu-id="e955e-114">The `-vbruntime+` option produces the same behavior that occurs if no `-vbruntime` switch is specified.</span></span> <span data-ttu-id="e955e-115">Você pode usar o `-vbruntime+` opção de substituição anterior `-vbruntime` comutadores.</span><span class="sxs-lookup"><span data-stu-id="e955e-115">You can use the `-vbruntime+` option to override previous `-vbruntime` switches.</span></span>  
  
 <span data-ttu-id="e955e-116">A maioria dos objetos do `My` tipo não estão disponíveis quando você usa o `-vbruntime-` ou `-vbruntime:path` opções.</span><span class="sxs-lookup"><span data-stu-id="e955e-116">Most objects of the `My` type are unavailable when you use the `-vbruntime-` or `-vbruntime:path` options.</span></span>  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a><span data-ttu-id="e955e-117">Incorporar a funcionalidade básica de tempo de execução do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e955e-117">Embedding Visual Basic Runtime core functionality</span></span>  
 <span data-ttu-id="e955e-118">O `-vbruntime*` opção permite que você compilar sem uma referência a uma biblioteca de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e955e-118">The `-vbruntime*` option enables you to compile without a reference to a runtime library.</span></span> <span data-ttu-id="e955e-119">Em vez disso, a funcionalidade básica da biblioteca de tempo de execução do Visual Basic é inserida no assembly de usuário.</span><span class="sxs-lookup"><span data-stu-id="e955e-119">Instead, core functionality from the Visual Basic Runtime Library is embedded in the user assembly.</span></span> <span data-ttu-id="e955e-120">Você pode usar essa opção se seu aplicativo é executado em plataformas que não contêm o tempo de execução do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e955e-120">You can use this option if your application runs on platforms that do not contain the Visual Basic runtime.</span></span>  
  
 <span data-ttu-id="e955e-121">Os seguintes membros de tempo de execução são inseridos:</span><span class="sxs-lookup"><span data-stu-id="e955e-121">The following runtime members are embedded:</span></span>  
  
-   <span data-ttu-id="e955e-122">Classe <xref:Microsoft.VisualBasic.CompilerServices.Conversions></span><span class="sxs-lookup"><span data-stu-id="e955e-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> class</span></span>  
  
-   <span data-ttu-id="e955e-123">Método <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29></span><span class="sxs-lookup"><span data-stu-id="e955e-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> method</span></span>  
  
-   <span data-ttu-id="e955e-124">Método <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29></span><span class="sxs-lookup"><span data-stu-id="e955e-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> method</span></span>  
  
-   <span data-ttu-id="e955e-125">Método <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29></span><span class="sxs-lookup"><span data-stu-id="e955e-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> method</span></span>  
  
-   <span data-ttu-id="e955e-126"><xref:Microsoft.VisualBasic.Constants.vbBack> constante</span><span class="sxs-lookup"><span data-stu-id="e955e-126"><xref:Microsoft.VisualBasic.Constants.vbBack> constant</span></span>  
  
-   <span data-ttu-id="e955e-127"><xref:Microsoft.VisualBasic.Constants.vbCr> constante</span><span class="sxs-lookup"><span data-stu-id="e955e-127"><xref:Microsoft.VisualBasic.Constants.vbCr> constant</span></span>  
  
-   <span data-ttu-id="e955e-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> constante</span><span class="sxs-lookup"><span data-stu-id="e955e-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> constant</span></span>  
  
-   <span data-ttu-id="e955e-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> constante</span><span class="sxs-lookup"><span data-stu-id="e955e-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> constant</span></span>  
  
-   <span data-ttu-id="e955e-130"><xref:Microsoft.VisualBasic.Constants.vbLf> constante</span><span class="sxs-lookup"><span data-stu-id="e955e-130"><xref:Microsoft.VisualBasic.Constants.vbLf> constant</span></span>  
  
-   <span data-ttu-id="e955e-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> constante</span><span class="sxs-lookup"><span data-stu-id="e955e-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> constant</span></span>  
  
-   <span data-ttu-id="e955e-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> constante</span><span class="sxs-lookup"><span data-stu-id="e955e-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> constant</span></span>  
  
-   <span data-ttu-id="e955e-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> constante</span><span class="sxs-lookup"><span data-stu-id="e955e-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> constant</span></span>  
  
-   <span data-ttu-id="e955e-134"><xref:Microsoft.VisualBasic.Constants.vbTab> constante</span><span class="sxs-lookup"><span data-stu-id="e955e-134"><xref:Microsoft.VisualBasic.Constants.vbTab> constant</span></span>  
  
-   <span data-ttu-id="e955e-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constante</span><span class="sxs-lookup"><span data-stu-id="e955e-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constant</span></span>  
  
-   <span data-ttu-id="e955e-136">Alguns objetos do `My` tipo</span><span class="sxs-lookup"><span data-stu-id="e955e-136">Some objects of the `My` type</span></span>  
  
 <span data-ttu-id="e955e-137">Se você compilar usando o `-vbruntime*` opção e seu código faz referência a um membro da biblioteca de tempo de execução do Visual Basic que não são inseridos com a funcionalidade básica, o compilador retorna um erro que indica que o membro não está disponível.</span><span class="sxs-lookup"><span data-stu-id="e955e-137">If you compile using the `-vbruntime*` option and your code references a member from the Visual Basic Runtime Library that is not embedded with the core functionality, the compiler returns an error that indicates that the member is not available.</span></span>  
  
## <a name="referencing-a-specified-library"></a><span data-ttu-id="e955e-138">Fazendo referência a uma biblioteca especificada</span><span class="sxs-lookup"><span data-stu-id="e955e-138">Referencing a specified library</span></span>  
 <span data-ttu-id="e955e-139">Você pode usar o `path` argumento para compilar com uma referência a uma biblioteca de tempo de execução personalizado em vez do padrão de biblioteca de tempo de execução do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e955e-139">You can use the `path` argument to compile with a reference to a custom runtime library instead of the default Visual Basic Runtime Library.</span></span>  
  
 <span data-ttu-id="e955e-140">Se o valor para o `path` argumento é um caminho totalmente qualificado para uma DLL, o compilador usará esse arquivo como a biblioteca de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e955e-140">If the value for the `path` argument is a fully qualified path to a DLL, the compiler will use that file as the runtime library.</span></span> <span data-ttu-id="e955e-141">Se o valor para o `path` argumento não é um caminho totalmente qualificado para uma DLL, o compilador do Visual Basic irá procurar a DLL identificada na pasta atual primeiro.</span><span class="sxs-lookup"><span data-stu-id="e955e-141">If the value for the `path` argument is not a fully qualified path to a DLL, the Visual Basic compiler will search for the identified DLL in the current folder first.</span></span> <span data-ttu-id="e955e-142">Ele procurará no caminho especificado usando o [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="e955e-142">It will then search in the path that you have specified by using the [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) compiler option.</span></span> <span data-ttu-id="e955e-143">Se o `-sdkpath` opção de compilador não for usada, o compilador irá procurar a DLL identificada na pasta do .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span><span class="sxs-lookup"><span data-stu-id="e955e-143">If the `-sdkpath` compiler option is not used, the compiler will search for the identified DLL in the .NET Framework folder (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e955e-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e955e-144">Example</span></span>  
 <span data-ttu-id="e955e-145">O exemplo a seguir mostra como usar o `-vbruntime` opção para compilar com uma referência a uma biblioteca personalizada.</span><span class="sxs-lookup"><span data-stu-id="e955e-145">The following example shows how to use the `-vbruntime` option to compile with a reference to a custom library.</span></span>  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="e955e-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e955e-146">See Also</span></span>  
 [<span data-ttu-id="e955e-147">Núcleo do Visual Basic – novo modo de compilação no Visual Studio 2010 SP1</span><span class="sxs-lookup"><span data-stu-id="e955e-147">Visual Basic Core – New compilation mode in Visual Studio 2010 SP1</span></span>](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx)  
 [<span data-ttu-id="e955e-148">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e955e-148">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="e955e-149">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="e955e-149">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="e955e-150">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="e955e-150">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
