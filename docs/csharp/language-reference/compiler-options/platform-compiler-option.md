---
title: "-platform (opções do compilador C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /platform
dev_langs:
- CSharp
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
caps.latest.revision: 46
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 44d4cadbc45eb141ecb7a83345d2a7a834ce5299
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="platform-c-compiler-options"></a><span data-ttu-id="d90e7-102">/platform (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="d90e7-102">/platform (C# Compiler Options)</span></span>
<span data-ttu-id="d90e7-103">Especifica qual versão do CLR (Common Language Runtime) pode executar o assembly.</span><span class="sxs-lookup"><span data-stu-id="d90e7-103">Specifies which version of the common language runtime (CLR) can run the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d90e7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d90e7-104">Syntax</span></span>  
  
```console  
/platform:string  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d90e7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d90e7-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="d90e7-106">anycpu (padrão), anycpu32bitpreferred, ARM, x64, x86 ou Itanium.</span><span class="sxs-lookup"><span data-stu-id="d90e7-106">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d90e7-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d90e7-107">Remarks</span></span>  
  
-   <span data-ttu-id="d90e7-108">O **anycpu** (padrão) compila seu assembly para que ele seja executado em qualquer plataforma.</span><span class="sxs-lookup"><span data-stu-id="d90e7-108">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="d90e7-109">Seu aplicativo será executado como um processo de 64 bits sempre que possível e realizará fallback para 32 bits quando apenas esse modo estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="d90e7-109">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>  
  
-   <span data-ttu-id="d90e7-110">**anycpu32bitpreferred** compila seu assembly para que ele seja executado em qualquer plataforma.</span><span class="sxs-lookup"><span data-stu-id="d90e7-110">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="d90e7-111">Seu aplicativo é executado no modo 32 bits em sistemas que dão suporte para aplicativos de 32 bits e 64 bits.</span><span class="sxs-lookup"><span data-stu-id="d90e7-111">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="d90e7-112">É possível especificar essa opção apenas para projetos que definem como destino o .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="d90e7-112">You can specify this option only for projects that target the .NET Framework 4.5.</span></span>  
  
-   <span data-ttu-id="d90e7-113">O **ARM** compila seu assembly para que ele seja executado em um computador que tem um processador ARM (Advanced RISC Machine).</span><span class="sxs-lookup"><span data-stu-id="d90e7-113">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>  
  
-   <span data-ttu-id="d90e7-114">O **x64** compila seu assembly para que ele seja executado pelo Common Language Runtime de 64 bits em um computador que dá suporte ao conjunto de instruções AMD64 e EM64T.</span><span class="sxs-lookup"><span data-stu-id="d90e7-114">**x64** compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span>  
  
-   <span data-ttu-id="d90e7-115">O **x86** compila seu assembly para que ele seja executado pelo Common Language Runtime compatível com x86 de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="d90e7-115">**x86** compiles your assembly to be run by the 32-bit, x86-compatible common language runtime.</span></span>  
  
-   <span data-ttu-id="d90e7-116">O **Itanium** compila seu assembly para que ele seja executado pelo Common Language Runtime de 64 bits em um computador com um processador Itanium.</span><span class="sxs-lookup"><span data-stu-id="d90e7-116">**Itanium** compiles your assembly to be run by the 64-bit common language runtime on a computer with an Itanium processor.</span></span>  
  
 <span data-ttu-id="d90e7-117">Em um sistema operacional do Windows de 64 bits:</span><span class="sxs-lookup"><span data-stu-id="d90e7-117">On a 64-bit Windows operating system:</span></span>  
  
-   <span data-ttu-id="d90e7-118">Os assemblies compilados com **/platform:x86** são executados no CLR de 32 bits em execução no WOW64.</span><span class="sxs-lookup"><span data-stu-id="d90e7-118">Assemblies compiled with **/platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>  
  
-   <span data-ttu-id="d90e7-119">Uma DLL compilada com o **/platform:anycpu** é executada no mesmo CLR que o processo no qual ela é carregada.</span><span class="sxs-lookup"><span data-stu-id="d90e7-119">A DLL compiled with the **/platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>  
  
-   <span data-ttu-id="d90e7-120">Os executáveis compilados com **/platform:anycpu** são executados no CLR de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="d90e7-120">Executables that are compiled with the **/platform:anycpu** execute on the 64-bit CLR.</span></span>  
  
-   <span data-ttu-id="d90e7-121">Os executáveis compilados com **/platform:anycpu32bitpreferred** são executados no CLR de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="d90e7-121">Executables compiled with **/platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="d90e7-122">A configuração **anycpu32bitpreferred** é válida apenas para arquivos .EXE (executáveis) e requer o .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="d90e7-122">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="d90e7-123">Para obter mais informações sobre o desenvolvimento de um aplicativo para ser executado em um sistema operacional Windows de 64 bits, consulte [Aplicativos de 64 bits](https://msdn.microsoft.com/library/ms241064).</span><span class="sxs-lookup"><span data-stu-id="d90e7-123">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](https://msdn.microsoft.com/library/ms241064).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d90e7-124">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d90e7-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="d90e7-125">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="d90e7-125">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="d90e7-126">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="d90e7-126">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="d90e7-127">Modifique a propriedade **Destino da plataforma** e, para projetos que definem como destino o .NET Framework 4.5, marque ou desmarque a caixa de seleção **Preferir 32 bits**.</span><span class="sxs-lookup"><span data-stu-id="d90e7-127">Modify the **Platform target** property and, for projects that target the .NET Framework 4.5, select or clear the **Prefer 32-bit** check box.</span></span>  
  
 <span data-ttu-id="d90e7-128">**Observe que /platform** não está disponível no ambiente de desenvolvimento no Visual C# Express.</span><span class="sxs-lookup"><span data-stu-id="d90e7-128">**Note /platform** is not available in the development environment in Visual C# Express.</span></span>  
  
 <span data-ttu-id="d90e7-129">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span><span class="sxs-lookup"><span data-stu-id="d90e7-129">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d90e7-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d90e7-130">Example</span></span>  
 <span data-ttu-id="d90e7-131">O exemplo a seguir mostra como usar a opção **/platform** para especificar que o aplicativo deve ser executado pelo CLR de 64 bits em um sistema de operacional do Windows de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="d90e7-131">The following example shows how to use the **/platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>  
  
```console  
csc /platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="d90e7-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d90e7-132">See Also</span></span>  
 <span data-ttu-id="d90e7-133">[Opções do compilador do C#](index.md) </span><span class="sxs-lookup"><span data-stu-id="d90e7-133">[C# Compiler Options](index.md) </span></span>  
 [<span data-ttu-id="d90e7-134">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="d90e7-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

