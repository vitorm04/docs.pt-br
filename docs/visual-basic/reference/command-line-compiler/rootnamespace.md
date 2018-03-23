---
title: -rootnamespace
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
ms.openlocfilehash: 45dce293549674e7e6aac2714e1a7a569719c597
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-rootnamespace"></a><span data-ttu-id="8d3c1-102">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="8d3c1-102">-rootnamespace</span></span>
<span data-ttu-id="8d3c1-103">Especifica um namespace para todas as declarações de tipo.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d3c1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d3c1-104">Syntax</span></span>  
  
```  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="8d3c1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8d3c1-105">Arguments</span></span>  
  
|<span data-ttu-id="8d3c1-106">Termo</span><span class="sxs-lookup"><span data-stu-id="8d3c1-106">Term</span></span>|<span data-ttu-id="8d3c1-107">Definição</span><span class="sxs-lookup"><span data-stu-id="8d3c1-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="8d3c1-108">O nome do namespace no qual colocar todas as declarações de tipo para o projeto atual.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d3c1-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d3c1-109">Remarks</span></span>  
 <span data-ttu-id="8d3c1-110">Se você usar o arquivo executável do Visual Studio (Devenv.exe) para compilar um projeto criado no ambiente de desenvolvimento integrado do Visual Studio, use `-rootnamespace` para especificar o valor da <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `-rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="8d3c1-111">Consulte [opções de linha de comando Devenv](/visualstudio/ide/reference/devenv-command-line-switches) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="8d3c1-112">Use o common language runtime MSIL Disassembler (`Ildasm.exe`) para exibir os nomes de namespace em seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="8d3c1-113">Para definir - rootnamespace no ambiente de desenvolvimento integrado do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8d3c1-113">To set -rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="8d3c1-114">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8d3c1-115">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-115">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="8d3c1-116">2.  Clique na guia **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-116">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="8d3c1-117">3.  Modificar o valor de **Namespace raiz** caixa.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-117">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8d3c1-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8d3c1-118">Example</span></span>  
 <span data-ttu-id="8d3c1-119">O código a seguir compila `In.vb` e inclui todas as declarações de tipo no namespace `mynamespace`.</span><span class="sxs-lookup"><span data-stu-id="8d3c1-119">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d3c1-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d3c1-120">See Also</span></span>  
 [<span data-ttu-id="8d3c1-121">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8d3c1-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="8d3c1-122">Ildasm.exe (IL Disassembler)</span><span class="sxs-lookup"><span data-stu-id="8d3c1-122">Ildasm.exe (IL Disassembler)</span></span>](https://msdn.microsoft.com/library/f7dy01k1)  
 [<span data-ttu-id="8d3c1-123">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="8d3c1-123">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
