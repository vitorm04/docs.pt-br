---
title: -platform (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: 5150e871d75c3c34dab10f10cdac3d8322d7a834
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849871"
---
# <a name="-platform-c-compiler-options"></a><span data-ttu-id="b2e0c-102">-platform (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="b2e0c-102">-platform (C# Compiler Options)</span></span>

<span data-ttu-id="b2e0c-103">Especifica qual versão do CLR (Common Language Runtime) pode executar o assembly.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-103">Specifies which version of the Common Language Runtime (CLR) can run the assembly.</span></span>

## <a name="syntax"></a><span data-ttu-id="b2e0c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2e0c-104">Syntax</span></span>

```console
-platform:string
```

## <a name="parameters"></a><span data-ttu-id="b2e0c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b2e0c-105">Parameters</span></span>

`string` \
<span data-ttu-id="b2e0c-106">anycpu (padrão), anycpu32bitpreferred, ARM, x64, x86 ou Itanium.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-106">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2e0c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b2e0c-107">Remarks</span></span>

- <span data-ttu-id="b2e0c-108">O **anycpu** (padrão) compila seu assembly para que ele seja executado em qualquer plataforma.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-108">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="b2e0c-109">Seu aplicativo será executado como um processo de 64 bits sempre que possível e realizará fallback para 32 bits quando apenas esse modo estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-109">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>

- <span data-ttu-id="b2e0c-110">**anycpu32bitpreferred** compila seu assembly para que ele seja executado em qualquer plataforma.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-110">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="b2e0c-111">Seu aplicativo é executado no modo 32 bits em sistemas que dão suporte para aplicativos de 32 bits e 64 bits.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-111">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="b2e0c-112">É possível especificar essa opção apenas para projetos que definem como destino o .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-112">You can specify this option only for projects that target the .NET Framework 4.5.</span></span>

- <span data-ttu-id="b2e0c-113">O **ARM** compila seu assembly para que ele seja executado em um computador que tem um processador ARM (Advanced RISC Machine).</span><span class="sxs-lookup"><span data-stu-id="b2e0c-113">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>

- <span data-ttu-id="b2e0c-114">**ARM64** compila o assembly para execução pelo CLR de 64 bits em um computador que tem um processador ARM (Máquina RISC Avançada) que dá suporte ao conjunto de instruções A64.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-114">**ARM64** compiles your assembly to run by the 64-bit CLR on a computer that has an Advanced RISC Machine (ARM) processor that supports the A64 instruction set.</span></span>

- <span data-ttu-id="b2e0c-115">**x64** compila o assembly para ser executado pelo CLR de 64 bits em um computador que dá suporte ao conjunto de instruções AMD64 ou EM64T.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-115">**x64** compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>

- <span data-ttu-id="b2e0c-116">**x86** compila o assembly para ser executado pelo CLR compatível com x86 de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-116">**x86** compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>

- <span data-ttu-id="b2e0c-117">**Itanium** compila o assembly para ser executado pelo CLR de 64 bits em um computador com um processador Itanium.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-117">**Itanium** compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>

<span data-ttu-id="b2e0c-118">Em um sistema operacional do Windows de 64 bits:</span><span class="sxs-lookup"><span data-stu-id="b2e0c-118">On a 64-bit Windows operating system:</span></span>

- <span data-ttu-id="b2e0c-119">Os assemblies compilados com **-platform:x86** são executados no CLR de 32 bits em execução no WOW64.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-119">Assemblies compiled with **-platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>

- <span data-ttu-id="b2e0c-120">Uma DLL compilada com o **-platform:anycpu** é executada no mesmo CLR que o processo no qual ela é carregada.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-120">A DLL compiled with the **-platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>

- <span data-ttu-id="b2e0c-121">Os executáveis compilados com **-platform:anycpu** são executados no CLR de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-121">Executables that are compiled with the **-platform:anycpu** execute on the 64-bit CLR.</span></span>

- <span data-ttu-id="b2e0c-122">Os executáveis compilados com **-platform:anycpu32bitpreferred** são executados no CLR de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-122">Executables compiled with **-platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>

<span data-ttu-id="b2e0c-123">A configuração **anycpu32bitpreferred** é válida apenas para arquivos .EXE (executáveis) e requer o .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-123">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires the .NET Framework 4.5.</span></span>

<span data-ttu-id="b2e0c-124">Para obter mais informações sobre o desenvolvimento de um aplicativo para ser executado em um sistema operacional Windows de 64 bits, consulte [Aplicativos de 64 bits](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="b2e0c-124">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="b2e0c-125">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b2e0c-125">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="b2e0c-126">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-126">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="b2e0c-127">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-127">Click the **Build** property page.</span></span>

3. <span data-ttu-id="b2e0c-128">Modifique a propriedade **Destino da plataforma** e, para projetos que definem como destino o .NET Framework 4.5, marque ou desmarque a caixa de seleção **Preferir 32 bits**.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-128">Modify the **Platform target** property and, for projects that target the .NET Framework 4.5, select or clear the **Prefer 32-bit** check box.</span></span>

> [!NOTE]
> <span data-ttu-id="b2e0c-129">`-platform`Não está disponível no ambiente de desenvolvimento no Visual C# Express.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-129">`-platform` is not available in the development environment in Visual C# Express.</span></span>

<span data-ttu-id="b2e0c-130">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-130">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>

## <a name="example"></a><span data-ttu-id="b2e0c-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b2e0c-131">Example</span></span>

<span data-ttu-id="b2e0c-132">O exemplo a seguir mostra como usar a opção **-platform** para especificar que o aplicativo deve ser executado pelo CLR de 64 bits em um sistema de operacional Windows de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="b2e0c-132">The following example shows how to use the **-platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>

```console
csc -platform:anycpu filename.cs
```

## <a name="see-also"></a><span data-ttu-id="b2e0c-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2e0c-133">See also</span></span>

- [<span data-ttu-id="b2e0c-134">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="b2e0c-134">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="b2e0c-135">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="b2e0c-135">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
