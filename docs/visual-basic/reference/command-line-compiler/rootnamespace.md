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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13bce09ca9fd1ae9ebb919a9245d8ccf87fbde1d
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276362"
---
# <a name="-rootnamespace"></a><span data-ttu-id="c50eb-102">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="c50eb-102">-rootnamespace</span></span>
<span data-ttu-id="c50eb-103">Especifica um namespace para todas as declarações de tipo.</span><span class="sxs-lookup"><span data-stu-id="c50eb-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c50eb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c50eb-104">Syntax</span></span>  
  
```  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="c50eb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c50eb-105">Arguments</span></span>  
  
|<span data-ttu-id="c50eb-106">Termo</span><span class="sxs-lookup"><span data-stu-id="c50eb-106">Term</span></span>|<span data-ttu-id="c50eb-107">Definição</span><span class="sxs-lookup"><span data-stu-id="c50eb-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="c50eb-108">O nome do namespace no qual Circunscrever todas as declarações de tipo para o projeto atual.</span><span class="sxs-lookup"><span data-stu-id="c50eb-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c50eb-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c50eb-109">Remarks</span></span>  
 <span data-ttu-id="c50eb-110">Se você usar o arquivo executável (Devenv.exe) do Visual Studio para compilar um projeto criado no ambiente de desenvolvimento integrado do Visual Studio, use `-rootnamespace` para especificar o valor da <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="c50eb-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `-rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="c50eb-111">Ver [opções de linha de comando Devenv](/visualstudio/ide/reference/devenv-command-line-switches) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="c50eb-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="c50eb-112">Use o common language runtime MSIL Disassembler (`Ildasm.exe`) para exibir os nomes de namespace em seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="c50eb-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="c50eb-113">Definir - rootnamespace no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c50eb-113">To set -rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="c50eb-114">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="c50eb-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c50eb-115">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="c50eb-115">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="c50eb-116">2.  Clique na guia **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="c50eb-116">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="c50eb-117">3.  Modificar o valor de **Namespace de raiz** caixa.</span><span class="sxs-lookup"><span data-stu-id="c50eb-117">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c50eb-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c50eb-118">Example</span></span>  
 <span data-ttu-id="c50eb-119">O seguinte código compila `In.vb` e inclui todas as declarações de tipo no namespace `mynamespace`.</span><span class="sxs-lookup"><span data-stu-id="c50eb-119">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c50eb-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c50eb-120">See also</span></span>

- [<span data-ttu-id="c50eb-121">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c50eb-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
- [<span data-ttu-id="c50eb-122">Ildasm.exe (IL Disassembler)</span><span class="sxs-lookup"><span data-stu-id="c50eb-122">Ildasm.exe (IL Disassembler)</span></span>](../../../framework/tools/ildasm-exe-il-disassembler.md)  
- [<span data-ttu-id="c50eb-123">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="c50eb-123">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
