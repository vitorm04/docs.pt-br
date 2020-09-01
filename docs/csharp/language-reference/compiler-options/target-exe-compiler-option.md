---
description: -target:exe (opções do compilador C#)
title: -target:exe (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 3cea52fe872fcb407206ee2063b93dc81447a3b2
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128498"
---
# <a name="-targetexe-c-compiler-options"></a><span data-ttu-id="ec988-103">-target:exe (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="ec988-103">-target:exe (C# Compiler Options)</span></span>
<span data-ttu-id="ec988-104">A opção **-target:exe** faz com que o compilador crie um aplicativo de console executável (EXE).</span><span class="sxs-lookup"><span data-stu-id="ec988-104">The **-target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec988-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec988-105">Syntax</span></span>  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="ec988-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec988-106">Remarks</span></span>  
 <span data-ttu-id="ec988-107">A opção **-target:exe** está em vigor por padrão.</span><span class="sxs-lookup"><span data-stu-id="ec988-107">The **-target:exe** option is in effect by default.</span></span> <span data-ttu-id="ec988-108">O arquivo executável será criado com a extensão .exe.</span><span class="sxs-lookup"><span data-stu-id="ec988-108">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="ec988-109">Use [-target:winexe](./target-winexe-compiler-option.md) para criar um executável de programa do Windows.</span><span class="sxs-lookup"><span data-stu-id="ec988-109">Use [-target:winexe](./target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="ec988-110">A menos que seja especificado de outra forma com a opção [-out](./out-compiler-option.md), o nome do arquivo de saída usará o nome do arquivo de entrada que contém o método [Main](../../programming-guide/main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="ec988-110">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="ec988-111">Quando especificado na linha de comando, todos os arquivos até a próxima opção **-out** ou **-target:module** serão usados para criar o arquivo .exe</span><span class="sxs-lookup"><span data-stu-id="ec988-111">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="ec988-112">Somente um método **Main** é necessário nos arquivos de código-fonte que são compilados em um arquivo .exe.</span><span class="sxs-lookup"><span data-stu-id="ec988-112">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="ec988-113">A opção do compilador [-main](./main-compiler-option.md) permite especificar qual classe contém o método **Main**, nos casos em que o código tem mais de uma classe com um método **Main**.</span><span class="sxs-lookup"><span data-stu-id="ec988-113">The [-main](./main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ec988-114">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ec988-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="ec988-115">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="ec988-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="ec988-116">Clique na página de propriedades do **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="ec988-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="ec988-117">Modifique a propriedade **Tipo de saída**.</span><span class="sxs-lookup"><span data-stu-id="ec988-117">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="ec988-118">Para obter informações sobre como definir essa opção do compilador programaticamente, consulte <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="ec988-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec988-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ec988-119">Example</span></span>  
 <span data-ttu-id="ec988-120">Cada uma das seguintes linhas de comando compilará `in.cs`, criando `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="ec988-120">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec988-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="ec988-121">See also</span></span>

- [<span data-ttu-id="ec988-122">-Target (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="ec988-122">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="ec988-123">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="ec988-123">C# Compiler Options</span></span>](./index.md)
