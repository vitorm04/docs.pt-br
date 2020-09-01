---
description: -target:module (opções do compilador C#)
title: -target:module (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 2c592d2fe001bb0908a06a6eb3287a39040b8715
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128446"
---
# <a name="-targetmodule-c-compiler-options"></a><span data-ttu-id="55655-103">-target:module (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="55655-103">-target:module (C# Compiler Options)</span></span>
<span data-ttu-id="55655-104">Essa opção faz com que o compilador não gere um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="55655-104">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55655-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55655-105">Syntax</span></span>  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="55655-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="55655-106">Remarks</span></span>  
 <span data-ttu-id="55655-107">Por padrão, o arquivo de saída criado por meio da compilação com essa opção terá uma extensão .netmodule.</span><span class="sxs-lookup"><span data-stu-id="55655-107">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="55655-108">Um arquivo que não tem um manifesto do assembly não pode ser carregado pelo Common Language Runtime do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55655-108">A file that does not have an assembly manifest cannot be loaded by the .NET Framework common language runtime.</span></span> <span data-ttu-id="55655-109">No entanto, esse arquivo pode ser incorporado no manifesto do assembly de um assembly por meio de [-addmodule](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="55655-109">However, such a file can be incorporated into the assembly manifest of an assembly by means of [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="55655-110">Se mais de um módulo for criado em uma única compilação, tipos [internos](../keywords/internal.md) em um módulo estarão disponíveis para outros módulos na compilação.</span><span class="sxs-lookup"><span data-stu-id="55655-110">If more than one module is created in a single compilation, [internal](../keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="55655-111">Quando o código em um módulo referenciar tipos `internal` em outro módulo, os dois módulos deverão ser incorporados em um manifesto do assembly, por meio de **-addmodule**.</span><span class="sxs-lookup"><span data-stu-id="55655-111">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **-addmodule**.</span></span>  
  
 <span data-ttu-id="55655-112">Não há suporte para a criação de um módulo no ambiente de desenvolvimento do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="55655-112">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="55655-113">Para obter informações sobre como definir essa opção do compilador programaticamente, consulte <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="55655-113">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55655-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="55655-114">Example</span></span>  
 <span data-ttu-id="55655-115">Compile `in.cs`, criando `in.netmodule`:</span><span class="sxs-lookup"><span data-stu-id="55655-115">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="55655-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="55655-116">See also</span></span>

- [<span data-ttu-id="55655-117">-Target (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="55655-117">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="55655-118">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="55655-118">C# Compiler Options</span></span>](./index.md)
