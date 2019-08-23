---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 052d6937846df39bd94d532e1b63ebe522dbf6c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964684"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="a0a4b-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="a0a4b-102">-moduleassemblyname</span></span>
<span data-ttu-id="a0a4b-103">Especifica o nome do assembly do qual esse módulo fará parte.</span><span class="sxs-lookup"><span data-stu-id="a0a4b-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0a4b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0a4b-104">Syntax</span></span>  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="a0a4b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a0a4b-105">Arguments</span></span>  
  
|<span data-ttu-id="a0a4b-106">Termo</span><span class="sxs-lookup"><span data-stu-id="a0a4b-106">Term</span></span>|<span data-ttu-id="a0a4b-107">Definição</span><span class="sxs-lookup"><span data-stu-id="a0a4b-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="a0a4b-108">O nome do assembly do qual este módulo fará parte.</span><span class="sxs-lookup"><span data-stu-id="a0a4b-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0a4b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a0a4b-109">Remarks</span></span>  
 <span data-ttu-id="a0a4b-110">O compilador processará `-moduleassemblyname` a opção somente se `-target:module` a opção tiver sido especificada.</span><span class="sxs-lookup"><span data-stu-id="a0a4b-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="a0a4b-111">Isso faz com que o compilador crie um módulo.</span><span class="sxs-lookup"><span data-stu-id="a0a4b-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="a0a4b-112">O módulo criado pelo compilador é válido somente para o assembly especificado com a `-moduleassemblyname` opção.</span><span class="sxs-lookup"><span data-stu-id="a0a4b-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="a0a4b-113">Se você posicionar o módulo em um assembly diferente, ocorrerão erros de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a0a4b-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="a0a4b-114">A `-moduleassemblyname` opção é necessária somente quando as seguintes opções são verdadeiras:</span><span class="sxs-lookup"><span data-stu-id="a0a4b-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
- <span data-ttu-id="a0a4b-115">Um tipo de dados no módulo precisa de acesso a `Friend` um tipo em um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="a0a4b-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
- <span data-ttu-id="a0a4b-116">O assembly referenciado concedeu acesso de assembly Friend ao assembly no qual o módulo será compilado.</span><span class="sxs-lookup"><span data-stu-id="a0a4b-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="a0a4b-117">Para obter mais informações sobre como criar um módulo, consulte [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="a0a4b-117">For more information about creating a module, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="a0a4b-118">Para obter mais informações sobre assemblies Friend, consulte [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="a0a4b-118">For more information about friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0a4b-119">A `-moduleassemblyname` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ela está disponível somente quando você compila a partir de um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="a0a4b-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0a4b-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0a4b-120">See also</span></span>

- [<span data-ttu-id="a0a4b-121">Como: Criar um assembly de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="a0a4b-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="a0a4b-122">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a0a4b-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="a0a4b-123">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0a4b-123">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="a0a4b-124">-main</span><span class="sxs-lookup"><span data-stu-id="a0a4b-124">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="a0a4b-125">-referência (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0a4b-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="a0a4b-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="a0a4b-126">-addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [<span data-ttu-id="a0a4b-127">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="a0a4b-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="a0a4b-128">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="a0a4b-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="a0a4b-129">Assemblies Amigáveis</span><span class="sxs-lookup"><span data-stu-id="a0a4b-129">Friend Assemblies</span></span>](../../../standard/assembly/friend-assemblies.md)
