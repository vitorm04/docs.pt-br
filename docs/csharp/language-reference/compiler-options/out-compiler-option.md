---
title: -out (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: 6c8408c0c613e361dae0c1db19f854e9421ca467
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970374"
---
# <a name="-out-c-compiler-options"></a><span data-ttu-id="1bc52-102">-out (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="1bc52-102">-out (C# Compiler Options)</span></span>
<span data-ttu-id="1bc52-103">A opção **-out** especifica o nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="1bc52-103">The **-out** option specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bc52-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1bc52-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="1bc52-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1bc52-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="1bc52-106">O nome do arquivo de saída criado pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="1bc52-106">The name of the output file created by the compiler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bc52-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="1bc52-107">Remarks</span></span>  
 <span data-ttu-id="1bc52-108">Na linha de comando, é possível especificar vários arquivos de saída para a compilação.</span><span class="sxs-lookup"><span data-stu-id="1bc52-108">On the command line, it is possible to specify multiple output files for your compilation.</span></span> <span data-ttu-id="1bc52-109">O compilador espera encontrar um ou mais arquivos de código-fonte após a opção **-out**.</span><span class="sxs-lookup"><span data-stu-id="1bc52-109">The compiler expects to find one or more source code files following the **-out** option.</span></span> <span data-ttu-id="1bc52-110">Em seguida, todos os arquivos de código-fonte serão compilados no arquivo de saída especificado por essa opção **-out**.</span><span class="sxs-lookup"><span data-stu-id="1bc52-110">Then, all source code files will be compiled into the output file specified by that **-out** option.</span></span>  
  
 <span data-ttu-id="1bc52-111">Especifique o nome completo e a extensão do arquivo que você deseja criar.</span><span class="sxs-lookup"><span data-stu-id="1bc52-111">Specify the full name and extension of the file you want to create.</span></span>  
  
 <span data-ttu-id="1bc52-112">Se você não especificar o nome do arquivo de saída:</span><span class="sxs-lookup"><span data-stu-id="1bc52-112">If you do not specify the name of the output file:</span></span>  
  
- <span data-ttu-id="1bc52-113">Um .exe extrairá seu nome do arquivo de código-fonte que contém o método **principal**.</span><span class="sxs-lookup"><span data-stu-id="1bc52-113">An .exe will take its name from the source code file that contains the **Main** method.</span></span>  
  
- <span data-ttu-id="1bc52-114">Um arquivo .dll ou .netmodule extrairá seu nome do primeiro arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="1bc52-114">A .dll or .netmodule will take its name from the first source code file.</span></span>  
  
 <span data-ttu-id="1bc52-115">Um arquivo de código-fonte usado para compilar um arquivo de saída não pode ser usado na mesma compilação para a compilação de outro arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="1bc52-115">A source code file used to compile one output file cannot be used in the same compilation for the compilation of another output file.</span></span>  
  
 <span data-ttu-id="1bc52-116">Ao produzir vários arquivos de saída em uma compilação de linha de comando, tenha em mente que somente um dos arquivos de saída pode ser um assembly e que somente o primeiro arquivo de saída especificado (implícita ou explicitamente com **-out**) pode ser o assembly.</span><span class="sxs-lookup"><span data-stu-id="1bc52-116">When producing multiple output files in a command-line compilation, keep in mind that only one of the output files can be an assembly and that only the first output file specified (implicitly or explicitly with **-out**) can be the assembly.</span></span>  
  
 <span data-ttu-id="1bc52-117">Os módulos produzidos como parte de uma compilação se tornam arquivos associados a qualquer assembly também produzido na compilação.</span><span class="sxs-lookup"><span data-stu-id="1bc52-117">Any modules produced as part of a compilation become files associated with any assembly also produced in the compilation.</span></span> <span data-ttu-id="1bc52-118">Use [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) para exibir o manifesto do assembly para ver os arquivos associados.</span><span class="sxs-lookup"><span data-stu-id="1bc52-118">Use [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) to view the assembly manifest to see the associated files.</span></span>  
  
 <span data-ttu-id="1bc52-119">A opção do compilador -out é necessária para que um exe seja o destino de um assembly amigável.</span><span class="sxs-lookup"><span data-stu-id="1bc52-119">The -out compiler option is required in order for an exe to be the target of a friend assembly.</span></span> <span data-ttu-id="1bc52-120">Para obter mais informações, consulte [Assemblies amigáveis](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="1bc52-120">For more information see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1bc52-121">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1bc52-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="1bc52-122">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="1bc52-122">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="1bc52-123">Clique na página de propriedades do **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="1bc52-123">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="1bc52-124">Modifique a propriedade **Nome do Assembly**.</span><span class="sxs-lookup"><span data-stu-id="1bc52-124">Modify the **Assembly name** property.</span></span>  
  
     <span data-ttu-id="1bc52-125">Para definir essa opção do compilador de maneira programática: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> é uma propriedade somente leitura, determinada por uma combinação do tipo de projeto (exe, biblioteca e assim por diante) e o nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="1bc52-125">To set this compiler option programmatically: the <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> is a read-only property, which is determined by a combination of the project type (exe, library, and so forth) and the assembly name.</span></span> <span data-ttu-id="1bc52-126">Será necessário modificar uma ou ambas as propriedades para definir o nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="1bc52-126">Modifying one or both of these properties will be necessary to set the output file name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bc52-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1bc52-127">Example</span></span>  
 <span data-ttu-id="1bc52-128">Compile `t.cs` e crie o arquivo de saída `t.exe`, bem como compile `t2.cs` e crie o arquivo de saída de módulo `mymodule.netmodule`:</span><span class="sxs-lookup"><span data-stu-id="1bc52-128">Compile `t.cs` and create output file `t.exe`, as well as build `t2.cs` and create module output file `mymodule.netmodule`:</span></span>  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bc52-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1bc52-129">See also</span></span>

- [<span data-ttu-id="1bc52-130">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="1bc52-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="1bc52-131">Assemblies Amigáveis</span><span class="sxs-lookup"><span data-stu-id="1bc52-131">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
- [<span data-ttu-id="1bc52-132">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="1bc52-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
