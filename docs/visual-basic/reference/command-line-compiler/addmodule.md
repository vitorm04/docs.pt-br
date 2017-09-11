---
title: /addmodule | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2db0db5b5dd94f03e67d8680624e2a4ad23587f7
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="addmodule"></a><span data-ttu-id="4b880-102">/addmodule</span><span class="sxs-lookup"><span data-stu-id="4b880-102">/addmodule</span></span>
<span data-ttu-id="4b880-103">Faz com que o compilador verifique todos os tipos de informações de arquivos especificados disponíveis para o projeto que você está compilando.</span><span class="sxs-lookup"><span data-stu-id="4b880-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b880-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b880-104">Syntax</span></span>  
  
```  
/addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="4b880-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4b880-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="4b880-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4b880-106">Required.</span></span> <span data-ttu-id="4b880-107">Lista delimitada por vírgulas de arquivos que contêm metadados, mas não contêm manifestos assembly.</span><span class="sxs-lookup"><span data-stu-id="4b880-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="4b880-108">Nomes de arquivo que contêm espaços devem estar entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="4b880-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b880-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b880-109">Remarks</span></span>  
 <span data-ttu-id="4b880-110">Os arquivos listados pelo `fileList` parâmetro deve ser criado com o `/target:module` opção, ou com o equivalente do outro compilador `/target:module`.</span><span class="sxs-lookup"><span data-stu-id="4b880-110">The files listed by the `fileList` parameter must be created with the `/target:module` option, or with another compiler's equivalent to `/target:module`.</span></span>  
  
 <span data-ttu-id="4b880-111">Todos os módulos adicionados com `/addmodule` deve estar no mesmo diretório que o arquivo de saída em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4b880-111">All modules added with `/addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="4b880-112">Ou seja, você pode especificar um módulo em qualquer diretório em tempo de compilação, mas o módulo deve estar no diretório do aplicativo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4b880-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="4b880-113">Se não for, você obterá um <xref:System.TypeLoadException>erro.</xref:System.TypeLoadException></span><span class="sxs-lookup"><span data-stu-id="4b880-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="4b880-114">Se você especificar (implícita ou explicitamente) qualquer[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) opção diferente de `/target:module` com `/addmodule`, os arquivos que você passar para `/addmodule` se tornam parte do assembly do projeto.</span><span class="sxs-lookup"><span data-stu-id="4b880-114">If you specify (implicitly or explicitly) any[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `/target:module` with `/addmodule`, the files you pass to `/addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="4b880-115">Um assembly é necessário para executar um arquivo de saída que tem um ou mais arquivos adicionados com `/addmodule`.</span><span class="sxs-lookup"><span data-stu-id="4b880-115">An assembly is required to run an output file that has one or more files added with `/addmodule`.</span></span>  
  
 <span data-ttu-id="4b880-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) para importar metadados de um arquivo que contém um assembly.</span><span class="sxs-lookup"><span data-stu-id="4b880-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b880-117">O `/addmodule` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="4b880-117">The `/addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b880-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4b880-118">Example</span></span>  
 <span data-ttu-id="4b880-119">O código a seguir cria um módulo.</span><span class="sxs-lookup"><span data-stu-id="4b880-119">The following code creates a module.</span></span>  
  
 <span data-ttu-id="4b880-120">[!code-vb[47 VbVbalrCompiler](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4b880-120">[!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]</span></span>  
  
 <span data-ttu-id="4b880-121">O código a seguir importa tipos do módulo.</span><span class="sxs-lookup"><span data-stu-id="4b880-121">The following code imports the module's types.</span></span>  
  
 <span data-ttu-id="4b880-122">[!code-vb[48 VbVbalrCompiler](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="4b880-122">[!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]</span></span>  
  
 <span data-ttu-id="4b880-123">Quando você executa `t1`, ele produz `802`.</span><span class="sxs-lookup"><span data-stu-id="4b880-123">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b880-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b880-124">See Also</span></span>  
 <span data-ttu-id="4b880-125">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="4b880-125">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="4b880-126"> [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="4b880-126"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="4b880-127"> [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span><span class="sxs-lookup"><span data-stu-id="4b880-127"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span></span>  
<span data-ttu-id="4b880-128"> [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="4b880-128"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
