---
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
ms.openlocfilehash: 073660fa732c04cdc987af5617b894a277ebcc0f
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970121"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="e96cd-102">-target (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="e96cd-102">-target (C# Compiler Options)</span></span>
<span data-ttu-id="e96cd-103">A opção do compilador **-target** pode ser especificada em uma das quatro formas:</span><span class="sxs-lookup"><span data-stu-id="e96cd-103">The **-target** compiler option can be specified in one of four forms:</span></span>  
  
 [<span data-ttu-id="e96cd-104">/target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="e96cd-104">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="e96cd-105">Para criar um arquivo .exe para aplicativos [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e96cd-105">To create an .exe file for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [<span data-ttu-id="e96cd-106">/target:exe</span><span class="sxs-lookup"><span data-stu-id="e96cd-106">-target:exe</span></span>](./target-exe-compiler-option.md)  
 <span data-ttu-id="e96cd-107">Para criar um arquivo .exe.</span><span class="sxs-lookup"><span data-stu-id="e96cd-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="e96cd-108">/target:library</span><span class="sxs-lookup"><span data-stu-id="e96cd-108">-target:library</span></span>](./target-library-compiler-option.md)  
 <span data-ttu-id="e96cd-109">Para criar uma biblioteca de códigos.</span><span class="sxs-lookup"><span data-stu-id="e96cd-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="e96cd-110">/target:module</span><span class="sxs-lookup"><span data-stu-id="e96cd-110">-target:module</span></span>](./target-module-compiler-option.md)  
 <span data-ttu-id="e96cd-111">Para criar um módulo.</span><span class="sxs-lookup"><span data-stu-id="e96cd-111">To create a module.</span></span>  
  
 [<span data-ttu-id="e96cd-112">/target:winexe</span><span class="sxs-lookup"><span data-stu-id="e96cd-112">-target:winexe</span></span>](./target-winexe-compiler-option.md)  
 <span data-ttu-id="e96cd-113">Para criar um programa do Windows.</span><span class="sxs-lookup"><span data-stu-id="e96cd-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="e96cd-114">/target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="e96cd-114">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)  
 <span data-ttu-id="e96cd-115">Para criar um arquivo .winmdobj intermediário.</span><span class="sxs-lookup"><span data-stu-id="e96cd-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="e96cd-116">A menos que você especifique **-target:module**, o **-target** faz com que um manifesto do assembly do .NET Framework seja colocado em um arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="e96cd-116">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="e96cd-117">Para obter mais informações, consulte [assemblies no .net](../../../standard/assembly/index.md) e [atributos comuns](../../programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="e96cd-117">For more information, see [Assemblies in .NET](../../../standard/assembly/index.md) and [Common Attributes](../../programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
 <span data-ttu-id="e96cd-118">O manifesto do assembly é colocado no primeiro arquivo de saída .exe na compilação ou na primeira DLL, se não houver nenhum arquivo de saída .exe.</span><span class="sxs-lookup"><span data-stu-id="e96cd-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="e96cd-119">Por exemplo, na linha de comando a seguir, o manifesto será colocado em `1.exe`:</span><span class="sxs-lookup"><span data-stu-id="e96cd-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="e96cd-120">O compilador cria apenas um manifesto do assembly por compilação.</span><span class="sxs-lookup"><span data-stu-id="e96cd-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="e96cd-121">As informações sobre todos os arquivos em uma compilação são colocados no manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="e96cd-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="e96cd-122">Todos os arquivos de saída, exceto os criados com **-target:module** podem conter um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="e96cd-122">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="e96cd-123">Ao gerar vários arquivos de saída na linha de comando, apenas um manifesto do assembly pode ser criado e ele deve ir para o primeiro arquivo de saída especificado na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="e96cd-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="e96cd-124">Não importa qual é o primeiro arquivo de saída ( **-target:exe**, **-target:winexe**, **-target:library** ou **-target:module**), todos os outros arquivos de saída produzidos na mesma compilação devem ser módulos ( **-target:module**).</span><span class="sxs-lookup"><span data-stu-id="e96cd-124">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="e96cd-125">Se você criar um assembly, pode indicar que todo ou parte do seu código está em conformidade com CLS com o atributo <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e96cd-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="e96cd-126">Para obter mais informações sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="e96cd-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e96cd-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e96cd-127">See also</span></span>

- [<span data-ttu-id="e96cd-128">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="e96cd-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="e96cd-129">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="e96cd-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="e96cd-130">-subsystemversion (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="e96cd-130">-subsystemversion (C# Compiler Options)</span></span>](./subsystemversion-compiler-option.md)
