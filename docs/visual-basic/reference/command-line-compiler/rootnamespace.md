---
title: /RootNamespace | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /rootnamespace
- rootnamespace
dev_langs:
- VB
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9a7a26407e981d3aea58d970d88bf25025e6bba6
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="rootnamespace"></a><span data-ttu-id="4e4f6-102">/rootnamespace</span><span class="sxs-lookup"><span data-stu-id="4e4f6-102">/rootnamespace</span></span>
<span data-ttu-id="4e4f6-103">Especifica um namespace para todas as declarações de tipo.</span><span class="sxs-lookup"><span data-stu-id="4e4f6-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e4f6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4e4f6-104">Syntax</span></span>  
  
```  
/rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="4e4f6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4e4f6-105">Arguments</span></span>  
  
|<span data-ttu-id="4e4f6-106">Termo</span><span class="sxs-lookup"><span data-stu-id="4e4f6-106">Term</span></span>|<span data-ttu-id="4e4f6-107">Definição</span><span class="sxs-lookup"><span data-stu-id="4e4f6-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="4e4f6-108">O nome do namespace no qual colocar todas as declarações de tipo para o projeto atual.</span><span class="sxs-lookup"><span data-stu-id="4e4f6-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e4f6-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="4e4f6-109">Remarks</span></span>  
 <span data-ttu-id="4e4f6-110">Se você usar o arquivo executável do Visual Studio (Devenv.exe) para compilar um projeto criado no ambiente de desenvolvimento integrado do Visual Studio, use `/rootnamespace` para especificar o valor de <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A>propriedade.</xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="4e4f6-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `/rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="4e4f6-111">Consulte [opções de linha de comando Devenv](https://docs.microsoft.com/visualstudio/ide/reference/devenv-command-line-switches) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="4e4f6-111">See [Devenv Command Line Switches](https://docs.microsoft.com/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="4e4f6-112">Use o common language runtime MSIL Disassembler (eu`ldasm.exe`) para exibir os nomes de namespace em seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="4e4f6-112">Use the common language runtime MSIL Disassembler (I`ldasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="4e4f6-113">Para definir /rootnamespace no Visual Studio ambiente de desenvolvimento integrado</span><span class="sxs-lookup"><span data-stu-id="4e4f6-113">To set /rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="4e4f6-114">1.  Tenha um projeto selecionado no **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="4e4f6-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="4e4f6-115">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="4e4f6-115">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="4e4f6-116">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="4e4f6-116">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="4e4f6-117">2.  Clique o **aplicativo** guia.</span><span class="sxs-lookup"><span data-stu-id="4e4f6-117">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="4e4f6-118">3.  Modificar o valor de **Namespace raiz** caixa.</span><span class="sxs-lookup"><span data-stu-id="4e4f6-118">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4e4f6-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4e4f6-119">Example</span></span>  
 <span data-ttu-id="4e4f6-120">O seguinte código compila `In.vb` e inclui todas as declarações de tipo no namespace `mynamespace`.</span><span class="sxs-lookup"><span data-stu-id="4e4f6-120">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e4f6-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e4f6-121">See Also</span></span>  
 <span data-ttu-id="4e4f6-122">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="4e4f6-122">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="4e4f6-123"> [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1) </span><span class="sxs-lookup"><span data-stu-id="4e4f6-123"> [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1) </span></span>  
<span data-ttu-id="4e4f6-124"> [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="4e4f6-124"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
