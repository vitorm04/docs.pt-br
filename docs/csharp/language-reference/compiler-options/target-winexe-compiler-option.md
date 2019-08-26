---
title: -target:winexe (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 981f1b0b6ca9f708bb022a3662ab181a4f472040
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606385"
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="cda0e-102">-target:winexe (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="cda0e-102">-target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="cda0e-103">A opção **-target:winexe** faz com que o compilador crie um programa do Windows executável (EXE).</span><span class="sxs-lookup"><span data-stu-id="cda0e-103">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cda0e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cda0e-104">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="cda0e-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="cda0e-105">Remarks</span></span>  
 <span data-ttu-id="cda0e-106">O arquivo executável será criado com a extensão .exe.</span><span class="sxs-lookup"><span data-stu-id="cda0e-106">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="cda0e-107">Um programa do Windows é aquele que fornece uma interface do usuário da biblioteca do .NET Framework ou com as APIs do Windows.</span><span class="sxs-lookup"><span data-stu-id="cda0e-107">A Windows program is one that provides a user interface from either the .NET Framework library or with the Windows APIs.</span></span>  
  
 <span data-ttu-id="cda0e-108">Use [-target:exe](./target-exe-compiler-option.md) para criar um aplicativo do console.</span><span class="sxs-lookup"><span data-stu-id="cda0e-108">Use [-target:exe](./target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="cda0e-109">A menos que seja especificado de outra forma com a opção [-out](./out-compiler-option.md), o nome do arquivo de saída usará o nome do arquivo de entrada que contém o método [Main](../../programming-guide/main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="cda0e-109">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="cda0e-110">Quando especificado na linha de comando, todos os arquivos até a próxima opção **-out** ou [-target](./target-compiler-option.md) serão usados para criar o programa do Windows.</span><span class="sxs-lookup"><span data-stu-id="cda0e-110">When specified at the command line, all files until the next **-out** or [-target](./target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="cda0e-111">Somente um método **Main** é necessário nos arquivos de código-fonte que são compilados em um arquivo .exe.</span><span class="sxs-lookup"><span data-stu-id="cda0e-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="cda0e-112">A opção [-main](./main-compiler-option.md) permite especificar qual classe contém o método **Main**, nos casos em que o código tem mais de uma classe com um método **Main**.</span><span class="sxs-lookup"><span data-stu-id="cda0e-112">The [-main](./main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="cda0e-113">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cda0e-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="cda0e-114">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="cda0e-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="cda0e-115">Clique na página de propriedades do **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="cda0e-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="cda0e-116">Modifique a propriedade **Tipo de saída**.</span><span class="sxs-lookup"><span data-stu-id="cda0e-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="cda0e-117">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="cda0e-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cda0e-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cda0e-118">Example</span></span>  
 <span data-ttu-id="cda0e-119">Compile `in.cs` em um programa do Windows:</span><span class="sxs-lookup"><span data-stu-id="cda0e-119">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="cda0e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cda0e-120">See also</span></span>

- [<span data-ttu-id="cda0e-121">-target (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="cda0e-121">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="cda0e-122">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="cda0e-122">C# Compiler Options</span></span>](./index.md)
