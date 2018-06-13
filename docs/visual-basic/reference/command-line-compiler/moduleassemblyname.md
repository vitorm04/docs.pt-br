---
title: -/moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8b579c2c3ae22469706326ee17109b8e39dab60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650784"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="16258-102">-/moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="16258-102">-moduleassemblyname</span></span>
<span data-ttu-id="16258-103">Especifica o nome do assembly do qual esse módulo fará parte.</span><span class="sxs-lookup"><span data-stu-id="16258-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16258-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16258-104">Syntax</span></span>  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="16258-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="16258-105">Arguments</span></span>  
  
|<span data-ttu-id="16258-106">Termo</span><span class="sxs-lookup"><span data-stu-id="16258-106">Term</span></span>|<span data-ttu-id="16258-107">Definição</span><span class="sxs-lookup"><span data-stu-id="16258-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="16258-108">O nome do assembly que este módulo fará parte do.</span><span class="sxs-lookup"><span data-stu-id="16258-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16258-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="16258-109">Remarks</span></span>  
 <span data-ttu-id="16258-110">O compilador processa o `-moduleassemblyname` se única opção de `-target:module` opção foi especificada.</span><span class="sxs-lookup"><span data-stu-id="16258-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="16258-111">Isso faz com que o compilador criar um módulo.</span><span class="sxs-lookup"><span data-stu-id="16258-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="16258-112">O módulo criado pelo compilador é válido somente para o conjunto especificado com o `-moduleassemblyname` opção.</span><span class="sxs-lookup"><span data-stu-id="16258-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="16258-113">Se você colocar o módulo em um assembly diferente, ocorrerão erros de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="16258-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="16258-114">O `-moduleassemblyname` opção é necessária somente quando os seguintes condições forem verdadeiras:</span><span class="sxs-lookup"><span data-stu-id="16258-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
-   <span data-ttu-id="16258-115">Um tipo de dados no módulo precisa acessar um `Friend` tipo em um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="16258-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
-   <span data-ttu-id="16258-116">O assembly referenciado concedeu acesso de assembly friend ao assembly no qual o módulo será criado.</span><span class="sxs-lookup"><span data-stu-id="16258-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="16258-117">Para obter mais informações sobre como criar um módulo, consulte [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="16258-117">For more information about creating a module, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="16258-118">Para obter mais informações sobre assemblies amigáveis, consulte [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span><span class="sxs-lookup"><span data-stu-id="16258-118">For more information about friend assemblies, see [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16258-119">O `-moduleassemblyname` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível apenas quando você compila a partir de um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="16258-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16258-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16258-120">See Also</span></span>  
 [<span data-ttu-id="16258-121">Como Compilar um Assembly de Vários Arquivos</span><span class="sxs-lookup"><span data-stu-id="16258-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="16258-122">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="16258-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="16258-123">-alvo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16258-123">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="16258-124">-main</span><span class="sxs-lookup"><span data-stu-id="16258-124">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)  
 [<span data-ttu-id="16258-125">-referência (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16258-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="16258-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="16258-126">-addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [<span data-ttu-id="16258-127">Assemblies e o Cache de Assembly Global</span><span class="sxs-lookup"><span data-stu-id="16258-127">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="16258-128">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="16258-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="16258-129">Assemblies Amigáveis</span><span class="sxs-lookup"><span data-stu-id="16258-129">Friend Assemblies</span></span>](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)
