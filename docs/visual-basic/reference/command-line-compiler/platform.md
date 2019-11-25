---
title: -platform
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: a6226b73d5d5d4d48a71afe39e8a546019d4c0bc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352339"
---
# <a name="-platform-visual-basic"></a><span data-ttu-id="fbe45-102">-platform (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbe45-102">-platform (Visual Basic)</span></span>
<span data-ttu-id="fbe45-103">Especifica qual versão de plataforma do common language runtime (CLR) pode executar o arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="fbe45-103">Specifies which platform version of common language runtime (CLR) can run the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbe45-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbe45-104">Syntax</span></span>  
  
```console  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a><span data-ttu-id="fbe45-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fbe45-105">Arguments</span></span>  
  
|<span data-ttu-id="fbe45-106">Termo</span><span class="sxs-lookup"><span data-stu-id="fbe45-106">Term</span></span>|<span data-ttu-id="fbe45-107">Definição</span><span class="sxs-lookup"><span data-stu-id="fbe45-107">Definition</span></span>|  
|---|---|  
|`x86`|<span data-ttu-id="fbe45-108">Compila o assembly para ser executado pelo CLR compatível com x86, de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="fbe45-108">Compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>|  
|`x64`|<span data-ttu-id="fbe45-109">Compila o assembly para ser executado pelo CLR de 64 bits em um computador que oferece suporte ao conjunto de instruções de AMD64 ou EM64T.</span><span class="sxs-lookup"><span data-stu-id="fbe45-109">Compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>|  
|`Itanium`|<span data-ttu-id="fbe45-110">Compila o assembly para ser executado pelo CLR de 64 bits em um computador com um processador Itanium.</span><span class="sxs-lookup"><span data-stu-id="fbe45-110">Compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>|  
|`arm`|<span data-ttu-id="fbe45-111">Compila o assembly para ser executado em um computador com um processador ARM (Advanced RISC Machine).</span><span class="sxs-lookup"><span data-stu-id="fbe45-111">Compiles your assembly to be run on a computer with an ARM (Advanced RISC Machine) processor.</span></span>|  
|`anycpu`|<span data-ttu-id="fbe45-112">Compila o assembly para ser executado em qualquer plataforma.</span><span class="sxs-lookup"><span data-stu-id="fbe45-112">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="fbe45-113">O aplicativo será executado como um aplicativo de 32 bits em versões de 32 bits do Windows e como um aplicativo de 64 bits em versões de 64 bits do Windows.</span><span class="sxs-lookup"><span data-stu-id="fbe45-113">The application will run as a 32-bit application on 32-bit versions of Windows and as a 64-bit application on 64-bit versions of Windows.</span></span> <span data-ttu-id="fbe45-114">Este sinalizador é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="fbe45-114">This flag is the default value.</span></span>|  
|`anycpu32bitpreferred`|<span data-ttu-id="fbe45-115">Compila o assembly para ser executado em qualquer plataforma.</span><span class="sxs-lookup"><span data-stu-id="fbe45-115">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="fbe45-116">O aplicativo será executado como um aplicativo de 32 bits em versões de 32 bits e 64 bits do Windows.</span><span class="sxs-lookup"><span data-stu-id="fbe45-116">The application will run as a 32-bit application on both 32-bit and 64-bit versions of Windows.</span></span> <span data-ttu-id="fbe45-117">This flag is valid only for executables (.EXE) and requires .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="fbe45-117">This flag is valid only for executables (.EXE) and requires .NET Framework 4.5.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbe45-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="fbe45-118">Remarks</span></span>  
 <span data-ttu-id="fbe45-119">Use a opção `-platform` para especificar o tipo de processador direcionada pelo arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="fbe45-119">Use the `-platform` option to specify the type of processor targeted by the output file.</span></span>  
  
 <span data-ttu-id="fbe45-120">Em geral, os assemblies do .NET Framework gravados no Visual Basic serão executados da mesma maneira, independentemente da plataforma.</span><span class="sxs-lookup"><span data-stu-id="fbe45-120">In general, .NET Framework assemblies written in Visual Basic will run the same regardless of the platform.</span></span> <span data-ttu-id="fbe45-121">No entanto, existem alguns casos em que se comportam de formas diferentes em plataformas distintas.</span><span class="sxs-lookup"><span data-stu-id="fbe45-121">However, there are some cases that behave differently on different platforms.</span></span> <span data-ttu-id="fbe45-122">Esses casos comuns são:</span><span class="sxs-lookup"><span data-stu-id="fbe45-122">These common cases are:</span></span>  
  
- <span data-ttu-id="fbe45-123">Estruturas que contêm membros que alteram o tamanho de acordo com a plataforma, como qualquer tipo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="fbe45-123">Structures that contain members that change size depending on the platform, such as any pointer type.</span></span>  
  
- <span data-ttu-id="fbe45-124">Aritmética de ponteiro que inclui tamanhos constantes.</span><span class="sxs-lookup"><span data-stu-id="fbe45-124">Pointer arithmetic that includes constant sizes.</span></span>  
  
- <span data-ttu-id="fbe45-125">As declarações COM ou de invocação de plataforma incorreta que usam `Integer` para identificadores em vez de <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="fbe45-125">Incorrect platform invoke or COM declarations that use `Integer` for handles instead of <xref:System.IntPtr>.</span></span>  
  
- <span data-ttu-id="fbe45-126">Convertendo <xref:System.IntPtr> para `Integer`.</span><span class="sxs-lookup"><span data-stu-id="fbe45-126">Casting <xref:System.IntPtr> to `Integer`.</span></span>  
  
- <span data-ttu-id="fbe45-127">Usando a invocação de plataforma ou a interoperabilidade COM com os componentes que não existem em todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="fbe45-127">Using platform invoke or COM interop with components that do not exist on all platforms.</span></span>  
  
 <span data-ttu-id="fbe45-128">The **-platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span><span class="sxs-lookup"><span data-stu-id="fbe45-128">The **-platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span></span> <span data-ttu-id="fbe45-129">Especificamente:</span><span class="sxs-lookup"><span data-stu-id="fbe45-129">Specifically:</span></span>  
  
- <span data-ttu-id="fbe45-130">Se decidir atingir uma plataforma de 64 bits e o aplicativo for executado em uma máquina de 32 bits, a mensagem de erro vem muito mais cedo e mais direcionada ao problema do que o erro que ocorre sem usar essa comutador.</span><span class="sxs-lookup"><span data-stu-id="fbe45-130">If you decide to target a 64-bit platform, and the application is run on a 32-bit machine, the error message comes much earlier and is more targeted at the problem than the error that occurs without using this switch.</span></span>  
  
- <span data-ttu-id="fbe45-131">Se você definir o sinalizador `x86` na opção e, em seguida, o aplicativo for executado em uma máquina de 64 bits, o aplicativo será executado no subsistema WOW em vez de ser executado nativamente.</span><span class="sxs-lookup"><span data-stu-id="fbe45-131">If you set the `x86` flag on the option and the application is subsequently run on a 64-bit machine, the application will run in the WOW subsystem instead of running natively.</span></span>  
  
 <span data-ttu-id="fbe45-132">Em um sistema operacional do Windows de 64 bits:</span><span class="sxs-lookup"><span data-stu-id="fbe45-132">On a 64-bit Windows operating system:</span></span>  
  
- <span data-ttu-id="fbe45-133">Assemblies compilados com `-platform:x86` serão executados no CLR de 32 bits em execução no WOW64.</span><span class="sxs-lookup"><span data-stu-id="fbe45-133">Assemblies compiled with `-platform:x86` will execute on the 32-bit CLR running under WOW64.</span></span>  
  
- <span data-ttu-id="fbe45-134">Executáveis compilados com o `-platform:anycpu` serão executados no CLR de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="fbe45-134">Executables compiled with the `-platform:anycpu` will execute on the 64-bit CLR.</span></span>  
  
- <span data-ttu-id="fbe45-135">Uma DLL compilada com o `-platform:anycpu` será executada no mesmo CLR que o processo no qual foi carregado.</span><span class="sxs-lookup"><span data-stu-id="fbe45-135">A DLL compiled with the `-platform:anycpu` will execute on the same CLR as the process into which it loaded.</span></span>  
  
- <span data-ttu-id="fbe45-136">Executáveis compilados com `-platform:anycpu32bitpreferred` serão executados no CLR de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="fbe45-136">Executables that are compiled with `-platform:anycpu32bitpreferred` will execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="fbe45-137">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="fbe45-137">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a><span data-ttu-id="fbe45-138">To set -platform in the Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="fbe45-138">To set -platform in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="fbe45-139">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span><span class="sxs-lookup"><span data-stu-id="fbe45-139">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="fbe45-140">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span><span class="sxs-lookup"><span data-stu-id="fbe45-140">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span></span>  
  
     <span data-ttu-id="fbe45-141">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="fbe45-141">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbe45-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fbe45-142">Example</span></span>  
 <span data-ttu-id="fbe45-143">O exemplo a seguir mostra como usar a opção do compilador `-platform`.</span><span class="sxs-lookup"><span data-stu-id="fbe45-143">The following example illustrates how to use the `-platform` compiler option.</span></span>  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="fbe45-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbe45-144">See also</span></span>

- [<span data-ttu-id="fbe45-145">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbe45-145">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="fbe45-146">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fbe45-146">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="fbe45-147">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="fbe45-147">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
