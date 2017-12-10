---
title: /platform (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4177b9da15bb89f37a7b3cbb27937e09d1c12635
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="platform-visual-basic"></a><span data-ttu-id="7ffa1-102">/platform (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ffa1-102">/platform (Visual Basic)</span></span>
<span data-ttu-id="7ffa1-103">Especifica qual versão de plataforma do common language runtime (CLR) pode executar o arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-103">Specifies which platform version of common language runtime (CLR) can run the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ffa1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7ffa1-104">Syntax</span></span>  
  
```  
/platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a><span data-ttu-id="7ffa1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7ffa1-105">Arguments</span></span>  
  
|<span data-ttu-id="7ffa1-106">Termo</span><span class="sxs-lookup"><span data-stu-id="7ffa1-106">Term</span></span>|<span data-ttu-id="7ffa1-107">Definição</span><span class="sxs-lookup"><span data-stu-id="7ffa1-107">Definition</span></span>|  
|---|---|  
|`x86`|<span data-ttu-id="7ffa1-108">Compila o assembly para ser executado pelo CLR compatível com x86, de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-108">Compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>|  
|`x64`|<span data-ttu-id="7ffa1-109">Compila o assembly para ser executado pelo CLR de 64 bits em um computador que oferece suporte ao conjunto de instruções de AMD64 ou EM64T.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-109">Compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>|  
|`Itanium`|<span data-ttu-id="7ffa1-110">Compila o assembly para ser executado pelo CLR de 64 bits em um computador com um processador Itanium.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-110">Compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>|  
|`arm`|<span data-ttu-id="7ffa1-111">Compila o assembly para ser executado em um computador com um processador ARM (Advanced RISC Machine).</span><span class="sxs-lookup"><span data-stu-id="7ffa1-111">Compiles your assembly to be run on a computer with an ARM (Advanced RISC Machine) processor.</span></span>|  
|`anycpu`|<span data-ttu-id="7ffa1-112">Compila o assembly para ser executado em qualquer plataforma.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-112">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="7ffa1-113">O aplicativo será executado como um aplicativo de 32 bits em versões de 32 bits do Windows e como um aplicativo de 64 bits em versões de 64 bits do Windows.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-113">The application will run as a 32-bit application on 32-bit versions of Windows and as a 64-bit application on 64-bit versions of Windows.</span></span> <span data-ttu-id="7ffa1-114">Este sinalizador é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-114">This flag is the default value.</span></span>|  
|`anycpu32bitpreferred`|<span data-ttu-id="7ffa1-115">Compila o assembly para ser executado em qualquer plataforma.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-115">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="7ffa1-116">O aplicativo será executado como um aplicativo de 32 bits em versões de 32 bits e 64 bits do Windows.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-116">The application will run as a 32-bit application on both 32-bit and 64-bit versions of Windows.</span></span> <span data-ttu-id="7ffa1-117">Esse sinalizador é válido somente para executáveis (.EXE) e requer [!INCLUDE[net_v45](~/includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7ffa1-117">This flag is valid only for executables (.EXE) and requires [!INCLUDE[net_v45](~/includes/net-v45-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ffa1-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="7ffa1-118">Remarks</span></span>  
 <span data-ttu-id="7ffa1-119">Use a opção `/platform` para especificar o tipo de processador direcionada pelo arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-119">Use the `/platform` option to specify the type of processor targeted by the output file.</span></span>  
  
 <span data-ttu-id="7ffa1-120">Em geral, os assemblies do .NET Framework gravados no Visual Basic serão executados da mesma maneira, independentemente da plataforma.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-120">In general, .NET Framework assemblies written in Visual Basic will run the same regardless of the platform.</span></span> <span data-ttu-id="7ffa1-121">No entanto, existem alguns casos em que se comportam de formas diferentes em plataformas distintas.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-121">However, there are some cases that behave differently on different platforms.</span></span> <span data-ttu-id="7ffa1-122">Esses casos comuns são:</span><span class="sxs-lookup"><span data-stu-id="7ffa1-122">These common cases are:</span></span>  
  
-   <span data-ttu-id="7ffa1-123">Estruturas que contêm membros que alteram o tamanho de acordo com a plataforma, como qualquer tipo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-123">Structures that contain members that change size depending on the platform, such as any pointer type.</span></span>  
  
-   <span data-ttu-id="7ffa1-124">Aritmética de ponteiro que inclui tamanhos constantes.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-124">Pointer arithmetic that includes constant sizes.</span></span>  
  
-   <span data-ttu-id="7ffa1-125">As declarações COM ou de invocação de plataforma incorreta que usam `Integer` para identificadores em vez de <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-125">Incorrect platform invoke or COM declarations that use `Integer` for handles instead of <xref:System.IntPtr>.</span></span>  
  
-   <span data-ttu-id="7ffa1-126">Convertendo <xref:System.IntPtr> para `Integer`.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-126">Casting <xref:System.IntPtr> to `Integer`.</span></span>  
  
-   <span data-ttu-id="7ffa1-127">Usando a invocação de plataforma ou a interoperabilidade COM com os componentes que não existem em todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-127">Using platform invoke or COM interop with components that do not exist on all platforms.</span></span>  
  
 <span data-ttu-id="7ffa1-128">O **/platform** opção reduz alguns problemas se você souber que você fez suposições sobre a arquitetura do seu código será executado em.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-128">The **/platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span></span> <span data-ttu-id="7ffa1-129">Especificamente:</span><span class="sxs-lookup"><span data-stu-id="7ffa1-129">Specifically:</span></span>  
  
-   <span data-ttu-id="7ffa1-130">Se decidir atingir uma plataforma de 64 bits e o aplicativo for executado em uma máquina de 32 bits, a mensagem de erro vem muito mais cedo e mais direcionada ao problema do que o erro que ocorre sem usar essa comutador.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-130">If you decide to target a 64-bit platform, and the application is run on a 32-bit machine, the error message comes much earlier and is more targeted at the problem than the error that occurs without using this switch.</span></span>  
  
-   <span data-ttu-id="7ffa1-131">Se você definir o sinalizador `x86` na opção e, em seguida, o aplicativo for executado em uma máquina de 64 bits, o aplicativo será executado no subsistema WOW em vez de ser executado nativamente.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-131">If you set the `x86` flag on the option and the application is subsequently run on a 64-bit machine, the application will run in the WOW subsystem instead of running natively.</span></span>  
  
 <span data-ttu-id="7ffa1-132">Em um sistema operacional do Windows de 64 bits:</span><span class="sxs-lookup"><span data-stu-id="7ffa1-132">On a 64-bit Windows operating system:</span></span>  
  
-   <span data-ttu-id="7ffa1-133">Assemblies compilados com `/platform:x86` serão executados no CLR de 32 bits em execução no WOW64.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-133">Assemblies compiled with `/platform:x86` will execute on the 32-bit CLR running under WOW64.</span></span>  
  
-   <span data-ttu-id="7ffa1-134">Executáveis compilados com o `/platform:anycpu` serão executados no CLR de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-134">Executables compiled with the `/platform:anycpu` will execute on the 64-bit CLR.</span></span>  
  
-   <span data-ttu-id="7ffa1-135">Uma DLL compilada com o `/platform:anycpu` será executada no mesmo CLR que o processo no qual foi carregado.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-135">A DLL compiled with the `/platform:anycpu` will execute on the same CLR as the process into which it loaded.</span></span>  
  
-   <span data-ttu-id="7ffa1-136">Executáveis compilados com `/platform:anycpu32bitpreferred` serão executados no CLR de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-136">Executables that are compiled with `/platform:anycpu32bitpreferred` will execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="7ffa1-137">Para obter mais informações sobre como desenvolver um aplicativo para ser executado em uma versão de 64 bits do Windows, consulte [aplicativos 64-bit](../../../../docs/framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="7ffa1-137">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../../docs/framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set-platform-in-the-visual-studio-ide"></a><span data-ttu-id="7ffa1-138">Para definir /platform no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7ffa1-138">To set /platform in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="7ffa1-139">Em **Solution Explorer**, escolha o projeto, abra o **projeto** menu e clique **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-139">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="7ffa1-140">Para obter mais informações, consulte [NIB: Gerenciando propriedades de projeto com o Designer de projeto](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span><span class="sxs-lookup"><span data-stu-id="7ffa1-140">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="7ffa1-141">No **compilar** guia, marque ou desmarque o **preferir 32-bit** caixa de seleção, ou no **CPU de destino** , escolha um valor.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-141">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span></span>  
  
     <span data-ttu-id="7ffa1-142">Para obter mais informações, consulte [página de compilação, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="7ffa1-142">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ffa1-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7ffa1-143">Example</span></span>  
 <span data-ttu-id="7ffa1-144">O exemplo a seguir mostra como usar a opção do compilador `/platform`.</span><span class="sxs-lookup"><span data-stu-id="7ffa1-144">The following example illustrates how to use the `/platform` compiler option.</span></span>  
  
```  
vbc /platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ffa1-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ffa1-145">See Also</span></span>  
 [<span data-ttu-id="7ffa1-146">/Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ffa1-146">/target (Visual Basic)</span></span>](target.md)  
 [<span data-ttu-id="7ffa1-147">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7ffa1-147">Visual Basic Command-Line Compiler</span></span>](index.md)  
 [<span data-ttu-id="7ffa1-148">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="7ffa1-148">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
