---
title: -platform (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: db9b3d31ba9657d26c1fb76ce4002afad949a881
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788902"
---
# <a name="-platform-visual-basic"></a><span data-ttu-id="123eb-102">-platform (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="123eb-102">-platform (Visual Basic)</span></span>
<span data-ttu-id="123eb-103">Especifica qual versão de plataforma do common language runtime (CLR) pode executar o arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="123eb-103">Specifies which platform version of common language runtime (CLR) can run the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="123eb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="123eb-104">Syntax</span></span>  
  
```  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a><span data-ttu-id="123eb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="123eb-105">Arguments</span></span>  
  
|<span data-ttu-id="123eb-106">Termo</span><span class="sxs-lookup"><span data-stu-id="123eb-106">Term</span></span>|<span data-ttu-id="123eb-107">Definição</span><span class="sxs-lookup"><span data-stu-id="123eb-107">Definition</span></span>|  
|---|---|  
|`x86`|<span data-ttu-id="123eb-108">Compila o assembly para ser executado pelo CLR compatível com x86, de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="123eb-108">Compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>|  
|`x64`|<span data-ttu-id="123eb-109">Compila o assembly para ser executado pelo CLR de 64 bits em um computador que oferece suporte ao conjunto de instruções de AMD64 ou EM64T.</span><span class="sxs-lookup"><span data-stu-id="123eb-109">Compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>|  
|`Itanium`|<span data-ttu-id="123eb-110">Compila o assembly para ser executado pelo CLR de 64 bits em um computador com um processador Itanium.</span><span class="sxs-lookup"><span data-stu-id="123eb-110">Compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>|  
|`arm`|<span data-ttu-id="123eb-111">Compila o assembly para ser executado em um computador com um processador ARM (Advanced RISC Machine).</span><span class="sxs-lookup"><span data-stu-id="123eb-111">Compiles your assembly to be run on a computer with an ARM (Advanced RISC Machine) processor.</span></span>|  
|`anycpu`|<span data-ttu-id="123eb-112">Compila o assembly para ser executado em qualquer plataforma.</span><span class="sxs-lookup"><span data-stu-id="123eb-112">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="123eb-113">O aplicativo será executado como um aplicativo de 32 bits em versões de 32 bits do Windows e como um aplicativo de 64 bits em versões de 64 bits do Windows.</span><span class="sxs-lookup"><span data-stu-id="123eb-113">The application will run as a 32-bit application on 32-bit versions of Windows and as a 64-bit application on 64-bit versions of Windows.</span></span> <span data-ttu-id="123eb-114">Este sinalizador é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="123eb-114">This flag is the default value.</span></span>|  
|`anycpu32bitpreferred`|<span data-ttu-id="123eb-115">Compila o assembly para ser executado em qualquer plataforma.</span><span class="sxs-lookup"><span data-stu-id="123eb-115">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="123eb-116">O aplicativo será executado como um aplicativo de 32 bits em versões de 32 bits e 64 bits do Windows.</span><span class="sxs-lookup"><span data-stu-id="123eb-116">The application will run as a 32-bit application on both 32-bit and 64-bit versions of Windows.</span></span> <span data-ttu-id="123eb-117">Esse sinalizador é válido somente para executáveis (.EXE) e requer [!INCLUDE[net_v45](~/includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="123eb-117">This flag is valid only for executables (.EXE) and requires [!INCLUDE[net_v45](~/includes/net-v45-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="123eb-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="123eb-118">Remarks</span></span>  
 <span data-ttu-id="123eb-119">Use a opção `-platform` para especificar o tipo de processador direcionada pelo arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="123eb-119">Use the `-platform` option to specify the type of processor targeted by the output file.</span></span>  
  
 <span data-ttu-id="123eb-120">Em geral, os assemblies do .NET Framework gravados no Visual Basic serão executados da mesma maneira, independentemente da plataforma.</span><span class="sxs-lookup"><span data-stu-id="123eb-120">In general, .NET Framework assemblies written in Visual Basic will run the same regardless of the platform.</span></span> <span data-ttu-id="123eb-121">No entanto, existem alguns casos em que se comportam de formas diferentes em plataformas distintas.</span><span class="sxs-lookup"><span data-stu-id="123eb-121">However, there are some cases that behave differently on different platforms.</span></span> <span data-ttu-id="123eb-122">Esses casos comuns são:</span><span class="sxs-lookup"><span data-stu-id="123eb-122">These common cases are:</span></span>  
  
- <span data-ttu-id="123eb-123">Estruturas que contêm membros que alteram o tamanho de acordo com a plataforma, como qualquer tipo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="123eb-123">Structures that contain members that change size depending on the platform, such as any pointer type.</span></span>  
  
- <span data-ttu-id="123eb-124">Aritmética de ponteiro que inclui tamanhos constantes.</span><span class="sxs-lookup"><span data-stu-id="123eb-124">Pointer arithmetic that includes constant sizes.</span></span>  
  
- <span data-ttu-id="123eb-125">As declarações COM ou de invocação de plataforma incorreta que usam `Integer` para identificadores em vez de <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="123eb-125">Incorrect platform invoke or COM declarations that use `Integer` for handles instead of <xref:System.IntPtr>.</span></span>  
  
- <span data-ttu-id="123eb-126">Convertendo <xref:System.IntPtr> para `Integer`.</span><span class="sxs-lookup"><span data-stu-id="123eb-126">Casting <xref:System.IntPtr> to `Integer`.</span></span>  
  
- <span data-ttu-id="123eb-127">Usando a invocação de plataforma ou a interoperabilidade COM com os componentes que não existem em todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="123eb-127">Using platform invoke or COM interop with components that do not exist on all platforms.</span></span>  
  
 <span data-ttu-id="123eb-128">O **-plataforma** opção reduzirá alguns problemas se você souber que fez suposições sobre a arquitetura do seu código será executado em.</span><span class="sxs-lookup"><span data-stu-id="123eb-128">The **-platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span></span> <span data-ttu-id="123eb-129">Especificamente:</span><span class="sxs-lookup"><span data-stu-id="123eb-129">Specifically:</span></span>  
  
- <span data-ttu-id="123eb-130">Se decidir atingir uma plataforma de 64 bits e o aplicativo for executado em uma máquina de 32 bits, a mensagem de erro vem muito mais cedo e mais direcionada ao problema do que o erro que ocorre sem usar essa comutador.</span><span class="sxs-lookup"><span data-stu-id="123eb-130">If you decide to target a 64-bit platform, and the application is run on a 32-bit machine, the error message comes much earlier and is more targeted at the problem than the error that occurs without using this switch.</span></span>  
  
- <span data-ttu-id="123eb-131">Se você definir o sinalizador `x86` na opção e, em seguida, o aplicativo for executado em uma máquina de 64 bits, o aplicativo será executado no subsistema WOW em vez de ser executado nativamente.</span><span class="sxs-lookup"><span data-stu-id="123eb-131">If you set the `x86` flag on the option and the application is subsequently run on a 64-bit machine, the application will run in the WOW subsystem instead of running natively.</span></span>  
  
 <span data-ttu-id="123eb-132">Em um sistema operacional do Windows de 64 bits:</span><span class="sxs-lookup"><span data-stu-id="123eb-132">On a 64-bit Windows operating system:</span></span>  
  
- <span data-ttu-id="123eb-133">Assemblies compilados com `-platform:x86` serão executados no CLR de 32 bits em execução no WOW64.</span><span class="sxs-lookup"><span data-stu-id="123eb-133">Assemblies compiled with `-platform:x86` will execute on the 32-bit CLR running under WOW64.</span></span>  
  
- <span data-ttu-id="123eb-134">Executáveis compilados com o `-platform:anycpu` serão executados no CLR de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="123eb-134">Executables compiled with the `-platform:anycpu` will execute on the 64-bit CLR.</span></span>  
  
- <span data-ttu-id="123eb-135">Uma DLL compilada com o `-platform:anycpu` será executada no mesmo CLR que o processo no qual foi carregado.</span><span class="sxs-lookup"><span data-stu-id="123eb-135">A DLL compiled with the `-platform:anycpu` will execute on the same CLR as the process into which it loaded.</span></span>  
  
- <span data-ttu-id="123eb-136">Executáveis compilados com `-platform:anycpu32bitpreferred` serão executados no CLR de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="123eb-136">Executables that are compiled with `-platform:anycpu32bitpreferred` will execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="123eb-137">Para obter mais informações sobre como desenvolver um aplicativo seja executado em uma versão de 64 bits do Windows, consulte [aplicativos de 64 bits](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="123eb-137">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a><span data-ttu-id="123eb-138">Para definir - plataforma no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="123eb-138">To set -platform in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="123eb-139">Na **Gerenciador de soluções**, escolha o projeto, abra o **Project** menu e, em seguida, clique **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="123eb-139">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="123eb-140">No **compilar** guia, marque ou desmarque as **preferir 32 bits** caixa de seleção, ou, no **Target CPU** , escolha um valor.</span><span class="sxs-lookup"><span data-stu-id="123eb-140">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span></span>  
  
     <span data-ttu-id="123eb-141">Para obter mais informações, consulte [compilar página, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="123eb-141">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="example"></a><span data-ttu-id="123eb-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="123eb-142">Example</span></span>  
 <span data-ttu-id="123eb-143">O exemplo a seguir mostra como usar a opção do compilador `-platform`.</span><span class="sxs-lookup"><span data-stu-id="123eb-143">The following example illustrates how to use the `-platform` compiler option.</span></span>  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="123eb-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="123eb-144">See also</span></span>

- [<span data-ttu-id="123eb-145">/Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="123eb-145">/target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="123eb-146">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="123eb-146">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="123eb-147">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="123eb-147">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
