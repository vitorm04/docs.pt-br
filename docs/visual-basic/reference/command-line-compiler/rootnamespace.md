---
title: /rootnamespace
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6b5da8e5eacacde9de5bdc54ef2d5e4d7f0d2653
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="rootnamespace"></a><span data-ttu-id="28330-102">/rootnamespace</span><span class="sxs-lookup"><span data-stu-id="28330-102">/rootnamespace</span></span>
<span data-ttu-id="28330-103">Especifica um namespace para todas as declarações de tipo.</span><span class="sxs-lookup"><span data-stu-id="28330-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28330-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28330-104">Syntax</span></span>  
  
```  
/rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="28330-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="28330-105">Arguments</span></span>  
  
|<span data-ttu-id="28330-106">Termo</span><span class="sxs-lookup"><span data-stu-id="28330-106">Term</span></span>|<span data-ttu-id="28330-107">Definição</span><span class="sxs-lookup"><span data-stu-id="28330-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="28330-108">O nome do namespace no qual colocar todas as declarações de tipo para o projeto atual.</span><span class="sxs-lookup"><span data-stu-id="28330-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28330-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="28330-109">Remarks</span></span>  
 <span data-ttu-id="28330-110">Se você usar o arquivo executável do Visual Studio (Devenv.exe) para compilar um projeto criado no ambiente de desenvolvimento integrado do Visual Studio, use `/rootnamespace` para especificar o valor da <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="28330-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `/rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="28330-111">Consulte [opções de linha de comando Devenv](/visualstudio/ide/reference/devenv-command-line-switches) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="28330-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="28330-112">Use o common language runtime MSIL Disassembler (`Ildasm.exe`) para exibir os nomes de namespace em seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="28330-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="28330-113">Para definir /rootnamespace no Visual Studio ambiente de desenvolvimento integrado</span><span class="sxs-lookup"><span data-stu-id="28330-113">To set /rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="28330-114">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="28330-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="28330-115">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="28330-115">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="28330-116">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="28330-116">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="28330-117">2.  Clique na guia **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="28330-117">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="28330-118">3.  Modificar o valor de **Namespace raiz** caixa.</span><span class="sxs-lookup"><span data-stu-id="28330-118">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="28330-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="28330-119">Example</span></span>  
 <span data-ttu-id="28330-120">O código a seguir compila `In.vb` e inclui todas as declarações de tipo no namespace `mynamespace`.</span><span class="sxs-lookup"><span data-stu-id="28330-120">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="28330-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28330-121">See Also</span></span>  
 [<span data-ttu-id="28330-122">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28330-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="28330-123">Ildasm.exe (IL Disassembler)</span><span class="sxs-lookup"><span data-stu-id="28330-123">Ildasm.exe (IL Disassembler)</span></span>](https://msdn.microsoft.com/library/f7dy01k1)  
 [<span data-ttu-id="28330-124">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="28330-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
