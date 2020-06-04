---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: fc8dfe41ea56531ff34cd5e551ef24d636227e47
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400494"
---
# <a name="-recurse"></a><span data-ttu-id="bedf7-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="bedf7-102">-recurse</span></span>
<span data-ttu-id="bedf7-103">Compila os arquivos de código-fonte em todos os diretórios filho do diretório especificado ou do diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="bedf7-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bedf7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bedf7-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="bedf7-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="bedf7-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="bedf7-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="bedf7-106">Optional.</span></span> <span data-ttu-id="bedf7-107">O diretório no qual você deseja que a pesquisa comece.</span><span class="sxs-lookup"><span data-stu-id="bedf7-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="bedf7-108">Se não for especificado, a pesquisa começará no diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="bedf7-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="bedf7-109">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="bedf7-109">Required.</span></span> <span data-ttu-id="bedf7-110">Os arquivos a serem pesquisados.</span><span class="sxs-lookup"><span data-stu-id="bedf7-110">The file(s) to search for.</span></span> <span data-ttu-id="bedf7-111">São permitidos caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="bedf7-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bedf7-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="bedf7-112">Remarks</span></span>  
 <span data-ttu-id="bedf7-113">Você pode usar caracteres curinga em um nome de arquivo para compilar todos os arquivos correspondentes no diretório do projeto sem usar o `-recurse` .</span><span class="sxs-lookup"><span data-stu-id="bedf7-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="bedf7-114">Se nenhum nome de arquivo de saída for especificado, o compilador baseará o nome do arquivo de saída no primeiro arquivo de entrada processado.</span><span class="sxs-lookup"><span data-stu-id="bedf7-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="bedf7-115">Esse é geralmente o primeiro arquivo na lista de arquivos compilados quando exibidos em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="bedf7-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="bedf7-116">Por esse motivo, é melhor especificar um arquivo de saída usando a `-out` opção.</span><span class="sxs-lookup"><span data-stu-id="bedf7-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bedf7-117">A `-recurse` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ela está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="bedf7-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bedf7-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bedf7-118">Example</span></span>  
 <span data-ttu-id="bedf7-119">O comando a seguir compila todos os arquivos de Visual Basic no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="bedf7-119">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="bedf7-120">O comando a seguir compila todos os arquivos de Visual Basic no `Test\ABC` diretório e em todos os diretórios abaixo dele e, em seguida, gera `Test.ABC.dll` .</span><span class="sxs-lookup"><span data-stu-id="bedf7-120">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="bedf7-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="bedf7-121">See also</span></span>

- [<span data-ttu-id="bedf7-122">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bedf7-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="bedf7-123">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bedf7-123">-out (Visual Basic)</span></span>](out.md)
- [<span data-ttu-id="bedf7-124">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="bedf7-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
