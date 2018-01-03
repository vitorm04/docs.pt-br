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
ms.openlocfilehash: b02171b28034d676b7027e96c2c66e36be9ae604
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="rootnamespace"></a><span data-ttu-id="3bf46-102">/rootnamespace</span><span class="sxs-lookup"><span data-stu-id="3bf46-102">/rootnamespace</span></span>
<span data-ttu-id="3bf46-103">Especifica um namespace para todas as declarações de tipo.</span><span class="sxs-lookup"><span data-stu-id="3bf46-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bf46-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3bf46-104">Syntax</span></span>  
  
```  
/rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="3bf46-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3bf46-105">Arguments</span></span>  
  
|<span data-ttu-id="3bf46-106">Termo</span><span class="sxs-lookup"><span data-stu-id="3bf46-106">Term</span></span>|<span data-ttu-id="3bf46-107">Definição</span><span class="sxs-lookup"><span data-stu-id="3bf46-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="3bf46-108">O nome do namespace no qual colocar todas as declarações de tipo para o projeto atual.</span><span class="sxs-lookup"><span data-stu-id="3bf46-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bf46-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="3bf46-109">Remarks</span></span>  
 <span data-ttu-id="3bf46-110">Se você usar o arquivo executável do Visual Studio (Devenv.exe) para compilar um projeto criado no ambiente de desenvolvimento integrado do Visual Studio, use `/rootnamespace` para especificar o valor da <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="3bf46-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `/rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="3bf46-111">Consulte [opções de linha de comando Devenv](/visualstudio/ide/reference/devenv-command-line-switches) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3bf46-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="3bf46-112">Use o common language runtime MSIL Disassembler (`Ildasm.exe`) para exibir os nomes de namespace em seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="3bf46-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="3bf46-113">Para definir /rootnamespace no Visual Studio ambiente de desenvolvimento integrado</span><span class="sxs-lookup"><span data-stu-id="3bf46-113">To set /rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="3bf46-114">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="3bf46-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="3bf46-115">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="3bf46-115">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="3bf46-116">2.  Clique na guia **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="3bf46-116">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="3bf46-117">3.  Modificar o valor de **Namespace raiz** caixa.</span><span class="sxs-lookup"><span data-stu-id="3bf46-117">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3bf46-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3bf46-118">Example</span></span>  
 <span data-ttu-id="3bf46-119">O código a seguir compila `In.vb` e inclui todas as declarações de tipo no namespace `mynamespace`.</span><span class="sxs-lookup"><span data-stu-id="3bf46-119">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3bf46-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3bf46-120">See Also</span></span>  
 [<span data-ttu-id="3bf46-121">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3bf46-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="3bf46-122">Ildasm.exe (IL Disassembler)</span><span class="sxs-lookup"><span data-stu-id="3bf46-122">Ildasm.exe (IL Disassembler)</span></span>](https://msdn.microsoft.com/library/f7dy01k1)  
 [<span data-ttu-id="3bf46-123">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="3bf46-123">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
