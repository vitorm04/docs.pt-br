---
title: -rootnamespace
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
ms.openlocfilehash: 4df4e74fc13c922f51f5b74c3c152bdea28b4431
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005203"
---
# <a name="-rootnamespace"></a><span data-ttu-id="3c0ca-102">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="3c0ca-102">-rootnamespace</span></span>
<span data-ttu-id="3c0ca-103">Especifica um namespace para todas as declarações de tipo.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c0ca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c0ca-104">Syntax</span></span>  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="3c0ca-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="3c0ca-105">Arguments</span></span>  
  
|<span data-ttu-id="3c0ca-106">Termo</span><span class="sxs-lookup"><span data-stu-id="3c0ca-106">Term</span></span>|<span data-ttu-id="3c0ca-107">Definição</span><span class="sxs-lookup"><span data-stu-id="3c0ca-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="3c0ca-108">O nome do namespace no qual incluir todas as declarações de tipo para o projeto atual.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c0ca-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="3c0ca-109">Remarks</span></span>  
 <span data-ttu-id="3c0ca-110">Se você usar o arquivo executável do Visual Studio (devenv. exe) para compilar um projeto criado no ambiente de desenvolvimento integrado do Visual Studio `-rootnamespace` , use para especificar o valor <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> da propriedade.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `-rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="3c0ca-111">Consulte [Opções de linha de comando do devenv](/visualstudio/ide/reference/devenv-command-line-switches) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="3c0ca-112">Use o Common Language Runtime o desmontador MSIL`Ildasm.exe`() para exibir os nomes de namespace em seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="3c0ca-113">Para Set-RootNamespace no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3c0ca-113">To set -rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="3c0ca-114">1. ter um projeto selecionado em **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="3c0ca-115">No menu **Projeto** , clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="3c0ca-115">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="3c0ca-116">2. Clique na guia **aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="3c0ca-116">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="3c0ca-117">3. modifique o valor na caixa **namespace raiz** .</span><span class="sxs-lookup"><span data-stu-id="3c0ca-117">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3c0ca-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3c0ca-118">Example</span></span>  
 <span data-ttu-id="3c0ca-119">O código a seguir compila `In.vb` e inclui todas as declarações de tipo no namespace. `mynamespace`</span><span class="sxs-lookup"><span data-stu-id="3c0ca-119">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c0ca-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="3c0ca-120">See also</span></span>

- [<span data-ttu-id="3c0ca-121">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3c0ca-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="3c0ca-122">ILDASM. exe (desmontador de IL)</span><span class="sxs-lookup"><span data-stu-id="3c0ca-122">Ildasm.exe (IL Disassembler)</span></span>](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="3c0ca-123">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="3c0ca-123">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
