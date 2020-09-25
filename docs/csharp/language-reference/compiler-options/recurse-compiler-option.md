---
description: -recurse (opções do compilador C#)
title: -recurse (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: 9e84ff95f7f0addac1c2c2d79af0ab53572da27f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193797"
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="d28f1-103">-recurse (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="d28f1-103">-recurse (C# Compiler Options)</span></span>

<span data-ttu-id="d28f1-104">A opção -recurse permite compilar arquivos de código-fonte em todos os diretórios filho do diretório especificado (dir) ou do diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="d28f1-104">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d28f1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d28f1-105">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="d28f1-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="d28f1-106">Arguments</span></span>  

 <span data-ttu-id="d28f1-107">`dir` (opcional)</span><span class="sxs-lookup"><span data-stu-id="d28f1-107">`dir` (optional)</span></span>  
 <span data-ttu-id="d28f1-108">O diretório no qual você deseja que a pesquisa comece.</span><span class="sxs-lookup"><span data-stu-id="d28f1-108">The directory in which you want the search to begin.</span></span> <span data-ttu-id="d28f1-109">Se ele não for especificado, a pesquisa começará no diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="d28f1-109">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="d28f1-110">Os arquivos a serem pesquisados.</span><span class="sxs-lookup"><span data-stu-id="d28f1-110">The file(s) to search for.</span></span> <span data-ttu-id="d28f1-111">São permitidos caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="d28f1-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d28f1-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="d28f1-112">Remarks</span></span>  

 <span data-ttu-id="d28f1-113">A opção **-recurse** permite compilar arquivos de código-fonte em todos os diretórios filho do diretório especificado (`dir`) ou do diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="d28f1-113">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="d28f1-114">É possível usar curingas em um nome de arquivo para compilar todos os arquivos correspondentes no diretório do projeto sem usar **-recurse**.</span><span class="sxs-lookup"><span data-stu-id="d28f1-114">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="d28f1-115">Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.</span><span class="sxs-lookup"><span data-stu-id="d28f1-115">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d28f1-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d28f1-116">Example</span></span>  

 <span data-ttu-id="d28f1-117">Compila todos os arquivos C# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="d28f1-117">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="d28f1-118">Compila todos os arquivos C# no diretório dir1\dir2 e quaisquer diretórios abaixo dele e gera dir2.dll:</span><span class="sxs-lookup"><span data-stu-id="d28f1-118">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="d28f1-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="d28f1-119">See also</span></span>

- [<span data-ttu-id="d28f1-120">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="d28f1-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="d28f1-121">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="d28f1-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
