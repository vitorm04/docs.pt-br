---
description: -target (opções do compilador C#)
title: -target (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: bcae4b64bdd2a939e35666a9068611b273c261da
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91188415"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="998ad-103">-target (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="998ad-103">-target (C# Compiler Options)</span></span>

<span data-ttu-id="998ad-104">A opção **-target** do compilador pode ser especificada em uma das seguintes formas:</span><span class="sxs-lookup"><span data-stu-id="998ad-104">The **-target** compiler option can be specified in one of the following forms:</span></span>  
  
 [<span data-ttu-id="998ad-105">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="998ad-105">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="998ad-106">Para criar um arquivo. exe para aplicativos da loja do Windows 8. x.</span><span class="sxs-lookup"><span data-stu-id="998ad-106">To create an .exe file for Windows 8.x Store apps.</span></span>  
  
 [<span data-ttu-id="998ad-107">-target:exe</span><span class="sxs-lookup"><span data-stu-id="998ad-107">-target:exe</span></span>](./target-exe-compiler-option.md)  
 <span data-ttu-id="998ad-108">Para criar um arquivo .exe.</span><span class="sxs-lookup"><span data-stu-id="998ad-108">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="998ad-109">-target:library</span><span class="sxs-lookup"><span data-stu-id="998ad-109">-target:library</span></span>](./target-library-compiler-option.md)  
 <span data-ttu-id="998ad-110">Para criar uma biblioteca de códigos.</span><span class="sxs-lookup"><span data-stu-id="998ad-110">To create a code library.</span></span>  
  
 [<span data-ttu-id="998ad-111">-target:module</span><span class="sxs-lookup"><span data-stu-id="998ad-111">-target:module</span></span>](./target-module-compiler-option.md)  
 <span data-ttu-id="998ad-112">Para criar um módulo.</span><span class="sxs-lookup"><span data-stu-id="998ad-112">To create a module.</span></span>  
  
 [<span data-ttu-id="998ad-113">-target:winexe</span><span class="sxs-lookup"><span data-stu-id="998ad-113">-target:winexe</span></span>](./target-winexe-compiler-option.md)  
 <span data-ttu-id="998ad-114">Para criar um programa do Windows.</span><span class="sxs-lookup"><span data-stu-id="998ad-114">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="998ad-115">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="998ad-115">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)  
 <span data-ttu-id="998ad-116">Para criar um arquivo .winmdobj intermediário.</span><span class="sxs-lookup"><span data-stu-id="998ad-116">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="998ad-117">A menos que você especifique **-target: módulo**, **-target** faz com que um manifesto de assembly .NET Framework seja colocado em um arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="998ad-117">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="998ad-118">Para obter mais informações, consulte [assemblies no .net](../../../standard/assembly/index.md) e [atributos comuns](../attributes/global.md).</span><span class="sxs-lookup"><span data-stu-id="998ad-118">For more information, see [Assemblies in .NET](../../../standard/assembly/index.md) and [Common Attributes](../attributes/global.md).</span></span>  
  
 <span data-ttu-id="998ad-119">O manifesto do assembly é colocado no primeiro arquivo de saída .exe na compilação ou na primeira DLL, se não houver nenhum arquivo de saída .exe.</span><span class="sxs-lookup"><span data-stu-id="998ad-119">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="998ad-120">Por exemplo, na linha de comando a seguir, o manifesto será colocado em `1.exe`:</span><span class="sxs-lookup"><span data-stu-id="998ad-120">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="998ad-121">O compilador cria apenas um manifesto do assembly por compilação.</span><span class="sxs-lookup"><span data-stu-id="998ad-121">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="998ad-122">As informações sobre todos os arquivos em uma compilação são colocados no manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="998ad-122">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="998ad-123">Todos os arquivos de saída exceto aqueles criados com **-target: o módulo** pode conter um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="998ad-123">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="998ad-124">Ao gerar vários arquivos de saída na linha de comando, apenas um manifesto do assembly pode ser criado e ele deve ir para o primeiro arquivo de saída especificado na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="998ad-124">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="998ad-125">Não importa qual é o primeiro arquivo de saída (**-target:exe**, **-target:winexe**, **-target:library** ou **-target:module**), todos os outros arquivos de saída produzidos na mesma compilação devem ser módulos (**-target:module**).</span><span class="sxs-lookup"><span data-stu-id="998ad-125">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="998ad-126">Se você criar um assembly, pode indicar que todo ou parte do seu código está em conformidade com CLS com o atributo <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="998ad-126">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="998ad-127">Para obter mais informações sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="998ad-127">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="998ad-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="998ad-128">See also</span></span>

- [<span data-ttu-id="998ad-129">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="998ad-129">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="998ad-130">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="998ad-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="998ad-131">-subsystemversion (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="998ad-131">-subsystemversion (C# Compiler Options)</span></span>](./subsystemversion-compiler-option.md)
