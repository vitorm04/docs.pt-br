---
description: -target:winexe (opções do compilador C#)
title: -target:winexe (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 5f8717115464ec3d9798228d7d50a8f08b2db300
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89466086"
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="7f90c-103">-target:winexe (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="7f90c-103">-target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="7f90c-104">A opção **-target:winexe** faz com que o compilador crie um programa do Windows executável (EXE).</span><span class="sxs-lookup"><span data-stu-id="7f90c-104">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f90c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f90c-105">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="7f90c-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="7f90c-106">Remarks</span></span>  
 <span data-ttu-id="7f90c-107">O arquivo executável será criado com a extensão .exe.</span><span class="sxs-lookup"><span data-stu-id="7f90c-107">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="7f90c-108">Um programa do Windows é aquele que fornece uma interface do usuário da biblioteca .NET ou com as APIs do Windows.</span><span class="sxs-lookup"><span data-stu-id="7f90c-108">A Windows program is one that provides a user interface from either the .NET library or with the Windows APIs.</span></span>  
  
 <span data-ttu-id="7f90c-109">Use [-target:exe](./target-exe-compiler-option.md) para criar um aplicativo do console.</span><span class="sxs-lookup"><span data-stu-id="7f90c-109">Use [-target:exe](./target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="7f90c-110">A menos que seja especificado de outra forma com a opção [-out](./out-compiler-option.md), o nome do arquivo de saída usará o nome do arquivo de entrada que contém o método [Main](../../programming-guide/main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="7f90c-110">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="7f90c-111">Quando especificado na linha de comando, todos os arquivos até a próxima opção **-out** ou [-target](./target-compiler-option.md) serão usados para criar o programa do Windows.</span><span class="sxs-lookup"><span data-stu-id="7f90c-111">When specified at the command line, all files until the next **-out** or [-target](./target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="7f90c-112">Somente um método **Main** é necessário nos arquivos de código-fonte que são compilados em um arquivo .exe.</span><span class="sxs-lookup"><span data-stu-id="7f90c-112">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="7f90c-113">A opção [-main](./main-compiler-option.md) permite especificar qual classe contém o método **Main**, nos casos em que o código tem mais de uma classe com um método **Main**.</span><span class="sxs-lookup"><span data-stu-id="7f90c-113">The [-main](./main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="7f90c-114">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7f90c-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="7f90c-115">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="7f90c-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="7f90c-116">Clique na página de propriedades do **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="7f90c-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="7f90c-117">Modifique a propriedade **Tipo de saída**.</span><span class="sxs-lookup"><span data-stu-id="7f90c-117">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="7f90c-118">Para obter informações sobre como definir essa opção do compilador programaticamente, consulte <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="7f90c-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f90c-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f90c-119">Example</span></span>  
 <span data-ttu-id="7f90c-120">Compile `in.cs` em um programa do Windows:</span><span class="sxs-lookup"><span data-stu-id="7f90c-120">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f90c-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="7f90c-121">See also</span></span>

- [<span data-ttu-id="7f90c-122">-Target (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="7f90c-122">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="7f90c-123">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="7f90c-123">C# Compiler Options</span></span>](./index.md)
