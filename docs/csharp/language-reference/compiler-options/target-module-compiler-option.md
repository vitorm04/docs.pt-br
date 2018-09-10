---
title: -target:module (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 7cc0e48a7a4a3ec3f28c89e80fadf6aa7e1130f2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865056"
---
# <a name="-targetmodule-c-compiler-options"></a><span data-ttu-id="59a71-102">-target:module (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="59a71-102">-target:module (C# Compiler Options)</span></span>
<span data-ttu-id="59a71-103">Essa opção faz com que o compilador não gere um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="59a71-103">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59a71-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59a71-104">Syntax</span></span>  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="59a71-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="59a71-105">Remarks</span></span>  
 <span data-ttu-id="59a71-106">Por padrão, o arquivo de saída criado por meio da compilação com essa opção terá uma extensão .netmodule.</span><span class="sxs-lookup"><span data-stu-id="59a71-106">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="59a71-107">Um arquivo que não tem um manifesto do assembly não pode ser carregado pelo Common Language Runtime do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="59a71-107">A file that does not have an assembly manifest cannot be loaded by the .NET Framework common language runtime.</span></span> <span data-ttu-id="59a71-108">No entanto, esse arquivo pode ser incorporado no manifesto do assembly de um assembly por meio de [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="59a71-108">However, such a file can be incorporated into the assembly manifest of an assembly by means of [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="59a71-109">Se mais de um módulo for criado em uma única compilação, tipos [internos](../../../csharp/language-reference/keywords/internal.md) em um módulo estarão disponíveis para outros módulos na compilação.</span><span class="sxs-lookup"><span data-stu-id="59a71-109">If more than one module is created in a single compilation, [internal](../../../csharp/language-reference/keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="59a71-110">Quando o código em um módulo referenciar tipos `internal` em outro módulo, os dois módulos deverão ser incorporados em um manifesto do assembly, por meio de **-addmodule**.</span><span class="sxs-lookup"><span data-stu-id="59a71-110">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **-addmodule**.</span></span>  
  
 <span data-ttu-id="59a71-111">Não há suporte para a criação de um módulo no ambiente de desenvolvimento do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="59a71-111">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="59a71-112">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="59a71-112">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59a71-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59a71-113">Example</span></span>  
 <span data-ttu-id="59a71-114">Compile `in.cs`, criando `in.netmodule`:</span><span class="sxs-lookup"><span data-stu-id="59a71-114">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="59a71-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59a71-115">See Also</span></span>  

- [<span data-ttu-id="59a71-116">-target (opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="59a71-116">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
- [<span data-ttu-id="59a71-117">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="59a71-117">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
