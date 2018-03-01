---
title: "-target:exe (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 515359b7a8a76e20896389b308df34db03f3798d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="-targetexe-c-compiler-options"></a><span data-ttu-id="b415e-102">-target:exe (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="b415e-102">-target:exe (C# Compiler Options)</span></span>
<span data-ttu-id="b415e-103">A opção **-target:exe** faz com que o compilador crie um aplicativo de console executável (EXE).</span><span class="sxs-lookup"><span data-stu-id="b415e-103">The **-target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b415e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b415e-104">Syntax</span></span>  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="b415e-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="b415e-105">Remarks</span></span>  
 <span data-ttu-id="b415e-106">A opção **-target:exe** está em vigor por padrão.</span><span class="sxs-lookup"><span data-stu-id="b415e-106">The **-target:exe** option is in effect by default.</span></span> <span data-ttu-id="b415e-107">O arquivo executável será criado com a extensão .exe.</span><span class="sxs-lookup"><span data-stu-id="b415e-107">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="b415e-108">Use [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) para criar um executável de programa do Windows.</span><span class="sxs-lookup"><span data-stu-id="b415e-108">Use [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="b415e-109">A menos que seja especificado de outra forma com a opção [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md), o nome do arquivo de saída usará o nome do arquivo de entrada que contém o método [Main](../../../csharp/programming-guide/main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="b415e-109">Unless otherwise specified with the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="b415e-110">Quando especificado na linha de comando, todos os arquivos até a próxima opção **-out** ou **-target:module** serão usados para criar o arquivo .exe</span><span class="sxs-lookup"><span data-stu-id="b415e-110">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="b415e-111">Somente um método **Main** é necessário nos arquivos de código-fonte que são compilados em um arquivo .exe.</span><span class="sxs-lookup"><span data-stu-id="b415e-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="b415e-112">A opção do compilador [-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) permite especificar qual classe contém o método **Main**, nos casos em que o código tem mais de uma classe com um método **Main**.</span><span class="sxs-lookup"><span data-stu-id="b415e-112">The [-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="b415e-113">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b415e-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="b415e-114">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="b415e-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="b415e-115">Clique na página de propriedades do **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="b415e-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="b415e-116">Modifique a propriedade **Tipo de saída**.</span><span class="sxs-lookup"><span data-stu-id="b415e-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="b415e-117">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="b415e-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b415e-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b415e-118">Example</span></span>  
 <span data-ttu-id="b415e-119">Cada uma das seguintes linhas de comando compilará `in.cs`, criando `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="b415e-119">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="b415e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b415e-120">See Also</span></span>  
 [<span data-ttu-id="b415e-121">-target (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="b415e-121">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="b415e-122">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="b415e-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
