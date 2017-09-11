---
title: /recurse | Documentos do Microsoft
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
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
caps.latest.revision: 12
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
ms.openlocfilehash: 9ceb2f3bc9e4d0f1088258f504b7a49c58a29e35
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="recurse"></a><span data-ttu-id="39f2c-102">/recurse</span><span class="sxs-lookup"><span data-stu-id="39f2c-102">/recurse</span></span>
<span data-ttu-id="39f2c-103">Compila arquivos de código-fonte no todos os diretórios filhos do diretório especificado ou o diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="39f2c-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39f2c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39f2c-104">Syntax</span></span>  
  
```  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="39f2c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="39f2c-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="39f2c-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="39f2c-106">Optional.</span></span> <span data-ttu-id="39f2c-107">O diretório no qual você deseja começar a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="39f2c-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="39f2c-108">Se não for especificado, a pesquisa começará no diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="39f2c-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="39f2c-109">Necessário.</span><span class="sxs-lookup"><span data-stu-id="39f2c-109">Required.</span></span> <span data-ttu-id="39f2c-110">Os arquivos para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="39f2c-110">The file(s) to search for.</span></span> <span data-ttu-id="39f2c-111">Caracteres curinga são permitidos.</span><span class="sxs-lookup"><span data-stu-id="39f2c-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39f2c-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="39f2c-112">Remarks</span></span>  
 <span data-ttu-id="39f2c-113">Você pode usar caracteres curinga em um nome de arquivo para compilar todos os arquivos correspondentes no diretório do projeto sem usar `/recurse`.</span><span class="sxs-lookup"><span data-stu-id="39f2c-113">You can use wildcards in a file name to compile all matching files in the project directory without using `/recurse`.</span></span> <span data-ttu-id="39f2c-114">Se nenhum nome de arquivo de saída for especificado, o compilador baseia o nome do arquivo de saída no primeiro arquivo de saída processado.</span><span class="sxs-lookup"><span data-stu-id="39f2c-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="39f2c-115">Isso geralmente é o primeiro arquivo na lista de arquivos compilados quando exibidos em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="39f2c-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="39f2c-116">Por esse motivo, é melhor especificar um arquivo de saída usando o `/out` opção.</span><span class="sxs-lookup"><span data-stu-id="39f2c-116">For this reason, it is best to specify an output file using the `/out` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39f2c-117">O `/recurse` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="39f2c-117">The `/recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39f2c-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39f2c-118">Example</span></span>  
 <span data-ttu-id="39f2c-119">O código a seguir compila todos os [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] arquivos no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="39f2c-119">The following code compiles all [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files in the current directory.</span></span>  
  
```  
vbc *.vb  
```  
  
 <span data-ttu-id="39f2c-120">O código a seguir compila todos os [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] arquivos de `Test\ABC` directory e quaisquer diretórios abaixo dela e, em seguida, gera `Test.ABC.dll`.</span><span class="sxs-lookup"><span data-stu-id="39f2c-120">The following code compiles all [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```  
vbc /target:library /out:Test.ABC.dll /recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="39f2c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39f2c-121">See Also</span></span>  
 <span data-ttu-id="39f2c-122">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="39f2c-122">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="39f2c-123"> [entrada/saída (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md) </span><span class="sxs-lookup"><span data-stu-id="39f2c-123"> [/out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md) </span></span>  
<span data-ttu-id="39f2c-124"> [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="39f2c-124"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
