---
title: -recurse (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: 1fc5591cb73164e15384eb4407a6e61e903eedbb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43398771"
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="8c138-102">-recurse (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="8c138-102">-recurse (C# Compiler Options)</span></span>
<span data-ttu-id="8c138-103">A opção -recurse permite compilar arquivos de código-fonte em todos os diretórios filho do diretório especificado (dir) ou do diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="8c138-103">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c138-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c138-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="8c138-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8c138-105">Arguments</span></span>  
 <span data-ttu-id="8c138-106">`dir` (opcional)</span><span class="sxs-lookup"><span data-stu-id="8c138-106">`dir` (optional)</span></span>  
 <span data-ttu-id="8c138-107">O diretório no qual você deseja que a pesquisa comece.</span><span class="sxs-lookup"><span data-stu-id="8c138-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="8c138-108">Se ele não for especificado, a pesquisa começará no diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="8c138-108">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="8c138-109">Os arquivos a serem pesquisados.</span><span class="sxs-lookup"><span data-stu-id="8c138-109">The file(s) to search for.</span></span> <span data-ttu-id="8c138-110">São permitidos caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="8c138-110">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c138-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c138-111">Remarks</span></span>  
 <span data-ttu-id="8c138-112">A opção **-recurse** permite compilar arquivos de código-fonte em todos os diretórios filho do diretório especificado (`dir`) ou do diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="8c138-112">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="8c138-113">É possível usar curingas em um nome de arquivo para compilar todos os arquivos correspondentes no diretório do projeto sem usar **-recurse**.</span><span class="sxs-lookup"><span data-stu-id="8c138-113">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="8c138-114">Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.</span><span class="sxs-lookup"><span data-stu-id="8c138-114">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c138-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8c138-115">Example</span></span>  
 <span data-ttu-id="8c138-116">Compila todos os arquivos C# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="8c138-116">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="8c138-117">Compila todos os arquivos C# no diretório dir1\dir2 e quaisquer diretórios abaixo dele e gera dir2.dll:</span><span class="sxs-lookup"><span data-stu-id="8c138-117">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c138-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c138-118">See Also</span></span>  

- [<span data-ttu-id="8c138-119">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="8c138-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="8c138-120">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="8c138-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
