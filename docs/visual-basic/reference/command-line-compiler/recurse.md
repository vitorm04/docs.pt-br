---
title: /recurse
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb69c7c44dcc2e8da5eb8a76f7d22f936a6d948f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="recurse"></a><span data-ttu-id="111c0-102">/recurse</span><span class="sxs-lookup"><span data-stu-id="111c0-102">/recurse</span></span>
<span data-ttu-id="111c0-103">Compila arquivos de código-fonte em todos os diretórios filhos do diretório do projeto ou o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="111c0-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="111c0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="111c0-104">Syntax</span></span>  
  
```  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="111c0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="111c0-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="111c0-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="111c0-106">Optional.</span></span> <span data-ttu-id="111c0-107">O diretório no qual você deseja que a pesquisa comece.</span><span class="sxs-lookup"><span data-stu-id="111c0-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="111c0-108">Se não for especificado, a pesquisa começará no diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="111c0-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="111c0-109">Necessário.</span><span class="sxs-lookup"><span data-stu-id="111c0-109">Required.</span></span> <span data-ttu-id="111c0-110">Os arquivos a serem pesquisados.</span><span class="sxs-lookup"><span data-stu-id="111c0-110">The file(s) to search for.</span></span> <span data-ttu-id="111c0-111">São permitidos caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="111c0-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="111c0-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="111c0-112">Remarks</span></span>  
 <span data-ttu-id="111c0-113">Você pode usar curingas no nome do arquivo para compilar todos os arquivos correspondentes no diretório do projeto sem usar `/recurse`.</span><span class="sxs-lookup"><span data-stu-id="111c0-113">You can use wildcards in a file name to compile all matching files in the project directory without using `/recurse`.</span></span> <span data-ttu-id="111c0-114">Se nenhum nome de arquivo de saída for especificado, o compilador baseia o nome do arquivo de saída no primeiro arquivo de saída processado.</span><span class="sxs-lookup"><span data-stu-id="111c0-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="111c0-115">Isso geralmente é o primeiro arquivo na lista de arquivos compilados quando exibidos em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="111c0-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="111c0-116">Por esse motivo, é melhor especificar um arquivo de saída usando o `/out` opção.</span><span class="sxs-lookup"><span data-stu-id="111c0-116">For this reason, it is best to specify an output file using the `/out` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="111c0-117">O `/recurse` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="111c0-117">The `/recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="111c0-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="111c0-118">Example</span></span>  
 <span data-ttu-id="111c0-119">O código a seguir compila todos os [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] arquivos no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="111c0-119">The following code compiles all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory.</span></span>  
  
```  
vbc *.vb  
```  
  
 <span data-ttu-id="111c0-120">O código a seguir compila todos os [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] arquivos de `Test\ABC` diretório e quaisquer diretórios abaixo dela e, em seguida, gera `Test.ABC.dll`.</span><span class="sxs-lookup"><span data-stu-id="111c0-120">The following code compiles all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```  
vbc /target:library /out:Test.ABC.dll /recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="111c0-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="111c0-121">See Also</span></span>  
 [<span data-ttu-id="111c0-122">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="111c0-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="111c0-123">entrada/saída (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="111c0-123">/out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)  
 [<span data-ttu-id="111c0-124">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="111c0-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
