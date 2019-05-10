---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 70cef109e4f2947fb4e38b9bfd19433257cce136
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663503"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="44149-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="44149-102">-moduleassemblyname</span></span>
<span data-ttu-id="44149-103">Especifica o nome do assembly do qual esse módulo fará parte.</span><span class="sxs-lookup"><span data-stu-id="44149-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44149-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44149-104">Syntax</span></span>  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="44149-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="44149-105">Arguments</span></span>  
  
|<span data-ttu-id="44149-106">Termo</span><span class="sxs-lookup"><span data-stu-id="44149-106">Term</span></span>|<span data-ttu-id="44149-107">Definição</span><span class="sxs-lookup"><span data-stu-id="44149-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="44149-108">O nome do assembly que esse módulo fará parte.</span><span class="sxs-lookup"><span data-stu-id="44149-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44149-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="44149-109">Remarks</span></span>  
 <span data-ttu-id="44149-110">O compilador processa os `-moduleassemblyname` somente se de opção a `-target:module` opção foi especificada.</span><span class="sxs-lookup"><span data-stu-id="44149-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="44149-111">Isso faz com que o compilador crie um módulo.</span><span class="sxs-lookup"><span data-stu-id="44149-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="44149-112">O módulo criado pelo compilador é válido somente para o conjunto especificado com o `-moduleassemblyname` opção.</span><span class="sxs-lookup"><span data-stu-id="44149-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="44149-113">Se você colocar o módulo em um assembly diferente, ocorrerão erros de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="44149-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="44149-114">O `-moduleassemblyname` opção é necessária somente quando as seguintes condições forem verdadeiras:</span><span class="sxs-lookup"><span data-stu-id="44149-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
- <span data-ttu-id="44149-115">Um tipo de dados no módulo precisa acessar um `Friend` tipo em um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="44149-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
- <span data-ttu-id="44149-116">O assembly referenciado concedeu acesso de assembly amigável para o assembly no qual o módulo será compilado.</span><span class="sxs-lookup"><span data-stu-id="44149-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="44149-117">Para obter mais informações sobre como criar um módulo, consulte [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="44149-117">For more information about creating a module, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="44149-118">Para obter mais informações sobre assemblies amigáveis, consulte [Assemblies amigáveis](../../../standard/assembly/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="44149-118">For more information about friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44149-119">O `-moduleassemblyname` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando você compila em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="44149-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44149-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44149-120">See also</span></span>

- [<span data-ttu-id="44149-121">Como: Criar um assembly de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="44149-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="44149-122">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="44149-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="44149-123">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44149-123">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="44149-124">-main</span><span class="sxs-lookup"><span data-stu-id="44149-124">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="44149-125">-referência (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44149-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="44149-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="44149-126">-addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [<span data-ttu-id="44149-127">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="44149-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="44149-128">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="44149-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="44149-129">Assemblies Amigáveis</span><span class="sxs-lookup"><span data-stu-id="44149-129">Friend Assemblies</span></span>](../../../standard/assembly/friend-assemblies.md)
