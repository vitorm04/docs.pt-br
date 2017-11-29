---
title: /addmodule
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fff292605e125776ae25e667d4813d770ed0a0aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="addmodule"></a><span data-ttu-id="ae793-102">/addmodule</span><span class="sxs-lookup"><span data-stu-id="ae793-102">/addmodule</span></span>
<span data-ttu-id="ae793-103">Faz com que o compilador verifique todos os tipos de informações de arquivos especificados disponíveis para o projeto que você está compilando.</span><span class="sxs-lookup"><span data-stu-id="ae793-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae793-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae793-104">Syntax</span></span>  
  
```  
/addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="ae793-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ae793-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="ae793-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="ae793-106">Required.</span></span> <span data-ttu-id="ae793-107">Lista delimitada por vírgulas de arquivos que contêm metadados, mas não contêm manifestos de assembly.</span><span class="sxs-lookup"><span data-stu-id="ae793-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="ae793-108">Nomes de arquivos que contenham espaços devem ficar entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="ae793-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae793-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ae793-109">Remarks</span></span>  
 <span data-ttu-id="ae793-110">Os arquivos listados pelo `fileList` parâmetro deve ser criado com o `/target:module` opção, ou com o equivalente do compilador outro para `/target:module`.</span><span class="sxs-lookup"><span data-stu-id="ae793-110">The files listed by the `fileList` parameter must be created with the `/target:module` option, or with another compiler's equivalent to `/target:module`.</span></span>  
  
 <span data-ttu-id="ae793-111">Todos os módulos adicionados com `/addmodule` deve estar no mesmo diretório que o arquivo de saída em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ae793-111">All modules added with `/addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="ae793-112">Ou seja, você pode especificar um módulo em qualquer diretório no tempo de compilação, mas o módulo deve estar no diretório de aplicativo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ae793-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="ae793-113">Se não for, você receberá um <xref:System.TypeLoadException> erro.</span><span class="sxs-lookup"><span data-stu-id="ae793-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="ae793-114">Se você especificar (implícita ou explicitamente) qualquer[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) opção diferente de `/target:module` com `/addmodule`, os arquivos que você passa para `/addmodule` se tornam parte do assembly do projeto.</span><span class="sxs-lookup"><span data-stu-id="ae793-114">If you specify (implicitly or explicitly) any[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `/target:module` with `/addmodule`, the files you pass to `/addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="ae793-115">Um assembly é necessário para executar um arquivo de saída que tem um ou mais arquivos adicionados com `/addmodule`.</span><span class="sxs-lookup"><span data-stu-id="ae793-115">An assembly is required to run an output file that has one or more files added with `/addmodule`.</span></span>  
  
 <span data-ttu-id="ae793-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) importar metadados de um arquivo que contém um assembly.</span><span class="sxs-lookup"><span data-stu-id="ae793-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae793-117">O `/addmodule` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ae793-117">The `/addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae793-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae793-118">Example</span></span>  
 <span data-ttu-id="ae793-119">O código a seguir cria um módulo.</span><span class="sxs-lookup"><span data-stu-id="ae793-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 <span data-ttu-id="ae793-120">O código a seguir importa os tipos do módulo.</span><span class="sxs-lookup"><span data-stu-id="ae793-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 <span data-ttu-id="ae793-121">Quando você executa `t1`, ele produz `802`.</span><span class="sxs-lookup"><span data-stu-id="ae793-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae793-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae793-122">See Also</span></span>  
 [<span data-ttu-id="ae793-123">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae793-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ae793-124">/Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae793-124">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="ae793-125">/Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae793-125">/reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="ae793-126">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae793-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
