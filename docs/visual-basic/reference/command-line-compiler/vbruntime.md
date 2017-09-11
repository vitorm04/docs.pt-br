---
title: /vbruntime | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbruntime
- /vbruntime
dev_langs:
- VB
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: cb07ed8c2f6070079cc51c290ff5a61305c5a5d3
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="vbruntime"></a><span data-ttu-id="ac742-102">/vbruntime</span><span class="sxs-lookup"><span data-stu-id="ac742-102">/vbruntime</span></span>
<span data-ttu-id="ac742-103">Especifica que o compilador deve compilar sem uma referência à biblioteca de tempo de execução do Visual Basic ou com uma referência a uma biblioteca de tempo de execução específico.</span><span class="sxs-lookup"><span data-stu-id="ac742-103">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac742-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac742-104">Syntax</span></span>  
  
```  
/vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a><span data-ttu-id="ac742-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ac742-105">Arguments</span></span>  
 \-  
 <span data-ttu-id="ac742-106">Compile sem uma referência à biblioteca de tempo de execução do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ac742-106">Compile without a reference to the Visual Basic Runtime Library.</span></span>  
  
 \+  
 <span data-ttu-id="ac742-107">Compile com uma referência à biblioteca de tempo de execução do Visual Basic padrão.</span><span class="sxs-lookup"><span data-stu-id="ac742-107">Compile with a reference to the default Visual Basic Runtime Library.</span></span>  
  
 \*  
 <span data-ttu-id="ac742-108">Compilar sem uma referência à biblioteca de tempo de execução do Visual Basic e incorporar a funcionalidade principal da biblioteca de tempo de execução do Visual Basic no assembly.</span><span class="sxs-lookup"><span data-stu-id="ac742-108">Compile without a reference to the Visual Basic Runtime Library, and embed core functionality from the Visual Basic Runtime Library into the assembly.</span></span>  
  
 `path`  
 <span data-ttu-id="ac742-109">Compile com uma referência à biblioteca especificada (DLL).</span><span class="sxs-lookup"><span data-stu-id="ac742-109">Compile with a reference to the specified library (DLL).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac742-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac742-110">Remarks</span></span>  
 <span data-ttu-id="ac742-111">O `/vbruntime` opção de compilador permite que você especifique que o compilador deve compilar sem uma referência à biblioteca de tempo de execução do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ac742-111">The `/vbruntime` compiler option enables you to specify that the compiler should compile without a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="ac742-112">Se você compilar sem uma referência à biblioteca de tempo de execução do Visual Basic, erros ou avisos serão registrados em construções de código ou linguagem que geram uma chamada para um auxiliar de tempo de execução do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ac742-112">If you compile without a reference to the Visual Basic Runtime Library, errors or warnings are logged on code or language constructs that generate a call to a Visual Basic runtime helper.</span></span> <span data-ttu-id="ac742-113">(Um *auxiliar de tempo de execução do Visual Basic* é uma função definida no Microsoft.VisualBasic.dll que é chamada no tempo de execução para executar uma semântica de linguagem específica.)</span><span class="sxs-lookup"><span data-stu-id="ac742-113">(A *Visual Basic runtime helper* is a function defined in Microsoft.VisualBasic.dll that is called at runtime to execute a specific language semantic.)</span></span>  
  
 <span data-ttu-id="ac742-114">O `/vbruntime+` opção produz o mesmo comportamento que ocorre se nenhuma `/vbruntime` opção é especificada.</span><span class="sxs-lookup"><span data-stu-id="ac742-114">The `/vbruntime+` option produces the same behavior that occurs if no `/vbruntime` switch is specified.</span></span> <span data-ttu-id="ac742-115">Você pode usar o `/vbruntime+` opção Substituir anterior `/vbruntime` comutadores.</span><span class="sxs-lookup"><span data-stu-id="ac742-115">You can use the `/vbruntime+` option to override previous `/vbruntime` switches.</span></span>  
  
 <span data-ttu-id="ac742-116">A maioria dos objetos do `My` tipo não estão disponíveis quando você usa o `/vbruntime-` ou `vbruntime:``path` opções.</span><span class="sxs-lookup"><span data-stu-id="ac742-116">Most objects of the `My` type are unavailable when you use the `/vbruntime-` or `vbruntime:``path` options.</span></span>  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a><span data-ttu-id="ac742-117">Incorporar a funcionalidade básica de tempo de execução do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac742-117">Embedding Visual Basic Runtime core functionality</span></span>  
 <span data-ttu-id="ac742-118">O `/vbruntime*` opção permite que você compilar sem uma referência a uma biblioteca de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ac742-118">The `/vbruntime*` option enables you to compile without a reference to a runtime library.</span></span> <span data-ttu-id="ac742-119">Em vez disso, a funcionalidade básica da biblioteca de tempo de execução do Visual Basic é inserida no assembly de usuário.</span><span class="sxs-lookup"><span data-stu-id="ac742-119">Instead, core functionality from the Visual Basic Runtime Library is embedded in the user assembly.</span></span> <span data-ttu-id="ac742-120">Você pode usar essa opção se seu aplicativo é executado em plataformas que não contêm o tempo de execução do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ac742-120">You can use this option if your application runs on platforms that do not contain the Visual Basic runtime.</span></span>  
  
 <span data-ttu-id="ac742-121">Os seguintes membros de tempo de execução são inseridos:</span><span class="sxs-lookup"><span data-stu-id="ac742-121">The following runtime members are embedded:</span></span>  
  
-   <span data-ttu-id="ac742-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions>classe</xref:Microsoft.VisualBasic.CompilerServices.Conversions></span><span class="sxs-lookup"><span data-stu-id="ac742-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> class</span></span>  
  
-   <span data-ttu-id="ac742-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>método</xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29></span><span class="sxs-lookup"><span data-stu-id="ac742-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> method</span></span>  
  
-   <span data-ttu-id="ac742-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>método</xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29></span><span class="sxs-lookup"><span data-stu-id="ac742-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> method</span></span>  
  
-   <span data-ttu-id="ac742-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>método</xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29></span><span class="sxs-lookup"><span data-stu-id="ac742-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> method</span></span>  
  
-   <span data-ttu-id="ac742-126"><xref:Microsoft.VisualBasic.Constants.vbBack>constante</xref:Microsoft.VisualBasic.Constants.vbBack></span><span class="sxs-lookup"><span data-stu-id="ac742-126"><xref:Microsoft.VisualBasic.Constants.vbBack> constant</span></span>  
  
-   <span data-ttu-id="ac742-127"><xref:Microsoft.VisualBasic.Constants.vbCr>constante</xref:Microsoft.VisualBasic.Constants.vbCr></span><span class="sxs-lookup"><span data-stu-id="ac742-127"><xref:Microsoft.VisualBasic.Constants.vbCr> constant</span></span>  
  
-   <span data-ttu-id="ac742-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf>constante</xref:Microsoft.VisualBasic.Constants.vbCrLf></span><span class="sxs-lookup"><span data-stu-id="ac742-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> constant</span></span>  
  
-   <span data-ttu-id="ac742-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed>constante</xref:Microsoft.VisualBasic.Constants.vbFormFeed></span><span class="sxs-lookup"><span data-stu-id="ac742-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> constant</span></span>  
  
-   <span data-ttu-id="ac742-130"><xref:Microsoft.VisualBasic.Constants.vbLf>constante</xref:Microsoft.VisualBasic.Constants.vbLf></span><span class="sxs-lookup"><span data-stu-id="ac742-130"><xref:Microsoft.VisualBasic.Constants.vbLf> constant</span></span>  
  
-   <span data-ttu-id="ac742-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine>constante</xref:Microsoft.VisualBasic.Constants.vbNewLine></span><span class="sxs-lookup"><span data-stu-id="ac742-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> constant</span></span>  
  
-   <span data-ttu-id="ac742-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar>constante</xref:Microsoft.VisualBasic.Constants.vbNullChar></span><span class="sxs-lookup"><span data-stu-id="ac742-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> constant</span></span>  
  
-   <span data-ttu-id="ac742-133"><xref:Microsoft.VisualBasic.Constants.vbNullString>constante</xref:Microsoft.VisualBasic.Constants.vbNullString></span><span class="sxs-lookup"><span data-stu-id="ac742-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> constant</span></span>  
  
-   <span data-ttu-id="ac742-134"><xref:Microsoft.VisualBasic.Constants.vbTab>constante</xref:Microsoft.VisualBasic.Constants.vbTab></span><span class="sxs-lookup"><span data-stu-id="ac742-134"><xref:Microsoft.VisualBasic.Constants.vbTab> constant</span></span>  
  
-   <span data-ttu-id="ac742-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab>constante</xref:Microsoft.VisualBasic.Constants.vbVerticalTab></span><span class="sxs-lookup"><span data-stu-id="ac742-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constant</span></span>  
  
-   <span data-ttu-id="ac742-136">Alguns objetos do `My` tipo</span><span class="sxs-lookup"><span data-stu-id="ac742-136">Some objects of the `My` type</span></span>  
  
 <span data-ttu-id="ac742-137">Se você compilar usando o `/vbruntime*` opção e seu código referencia um membro da biblioteca de tempo de execução do Visual Basic não são inseridos com a funcionalidade básica, o compilador retorna um erro que indica que o membro não está disponível.</span><span class="sxs-lookup"><span data-stu-id="ac742-137">If you compile using the `/vbruntime*` option and your code references a member from the Visual Basic Runtime Library that is not embedded with the core functionality, the compiler returns an error that indicates that the member is not available.</span></span>  
  
## <a name="referencing-a-specified-library"></a><span data-ttu-id="ac742-138">Fazendo referência a uma biblioteca especificada</span><span class="sxs-lookup"><span data-stu-id="ac742-138">Referencing a specified library</span></span>  
 <span data-ttu-id="ac742-139">Você pode usar o `path` argumento para compilar com uma referência a uma biblioteca de tempo de execução personalizado em vez do padrão de biblioteca de tempo de execução do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ac742-139">You can use the `path` argument to compile with a reference to a custom runtime library instead of the default Visual Basic Runtime Library.</span></span>  
  
 <span data-ttu-id="ac742-140">Se o valor para o `path` argumento é um caminho totalmente qualificado para uma DLL, o compilador usará esse arquivo como a biblioteca de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ac742-140">If the value for the `path` argument is a fully qualified path to a DLL, the compiler will use that file as the runtime library.</span></span> <span data-ttu-id="ac742-141">Se o valor para o `path` argumento não é um caminho totalmente qualificado para uma DLL, o compilador do Visual Basic irá procurar a DLL identificada na pasta atual primeiro.</span><span class="sxs-lookup"><span data-stu-id="ac742-141">If the value for the `path` argument is not a fully qualified path to a DLL, the Visual Basic compiler will search for the identified DLL in the current folder first.</span></span> <span data-ttu-id="ac742-142">Em seguida, ele irá procurar no caminho especificado usando o [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="ac742-142">It will then search in the path that you have specified by using the [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) compiler option.</span></span> <span data-ttu-id="ac742-143">Se o `/sdkpath` opção de compilador não for usada, o compilador irá procurar a DLL identificada na pasta do .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span><span class="sxs-lookup"><span data-stu-id="ac742-143">If the `/sdkpath` compiler option is not used, the compiler will search for the identified DLL in the .NET Framework folder (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac742-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ac742-144">Example</span></span>  
 <span data-ttu-id="ac742-145">O exemplo a seguir mostra como usar o `/vbruntime` opção para compilar com uma referência a uma biblioteca personalizada.</span><span class="sxs-lookup"><span data-stu-id="ac742-145">The following example shows how to use the `/vbruntime` option to compile with a reference to a custom library.</span></span>  
  
```  
vbc /vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac742-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac742-146">See Also</span></span>  
 <span data-ttu-id="ac742-147">[Núcleo do Visual Basic – novo modo de compilação no Visual Studio 2010 SP1](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx) </span><span class="sxs-lookup"><span data-stu-id="ac742-147">[Visual Basic Core – New compilation mode in Visual Studio 2010 SP1](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx) </span></span>  
<span data-ttu-id="ac742-148"> [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="ac742-148"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="ac742-149"> [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="ac742-149"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="ac742-150"> [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)</span><span class="sxs-lookup"><span data-stu-id="ac742-150"> [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)</span></span>
