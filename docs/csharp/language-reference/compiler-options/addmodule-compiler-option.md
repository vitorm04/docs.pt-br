---
description: -addmodule (opções do compilador C#)
title: -addmodule (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: ec72fc76b3d550029b1286f64b8f86e69e721468
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150564"
---
# <a name="-addmodule-c-compiler-options"></a><span data-ttu-id="41a3f-103">-addmodule (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="41a3f-103">-addmodule (C# Compiler Options)</span></span>

<span data-ttu-id="41a3f-104">Essa opção adiciona um módulo criado com a opção target:module para a compilação atual.</span><span class="sxs-lookup"><span data-stu-id="41a3f-104">This option adds a module that was created with the target:module switch to the current compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41a3f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41a3f-105">Syntax</span></span>  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="41a3f-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="41a3f-106">Arguments</span></span>  

 <span data-ttu-id="41a3f-107">`file`, `file2`</span><span class="sxs-lookup"><span data-stu-id="41a3f-107">`file`, `file2`</span></span>  
 <span data-ttu-id="41a3f-108">Um arquivo de saída que contém metadados.</span><span class="sxs-lookup"><span data-stu-id="41a3f-108">An output file that contains metadata.</span></span> <span data-ttu-id="41a3f-109">O arquivo não pode conter um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="41a3f-109">The file cannot contain an assembly manifest.</span></span> <span data-ttu-id="41a3f-110">Para importar mais de um arquivo, separe os nomes de arquivo com vírgula ou ponto e vírgula.</span><span class="sxs-lookup"><span data-stu-id="41a3f-110">To import more than one file, separate file names with either a comma or a semicolon.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41a3f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="41a3f-111">Remarks</span></span>  

 <span data-ttu-id="41a3f-112">Todos os módulos adicionados com **-addmodule** devem estar no mesmo diretório que o arquivo de saída em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="41a3f-112">All modules added with **-addmodule** must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="41a3f-113">Ou seja, é possível especificar um módulo em qualquer diretório em tempo de compilação, mas o módulo deve estar no diretório do aplicativo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="41a3f-113">That is, you can specify a module in any directory at compile time but the module must be in the application directory at run time.</span></span> <span data-ttu-id="41a3f-114">Se o módulo não estiver no diretório do aplicativo em tempo de execução, um <xref:System.TypeLoadException> será obtido.</span><span class="sxs-lookup"><span data-stu-id="41a3f-114">If the module is not in the application directory at run time, you will get a <xref:System.TypeLoadException>.</span></span>  
  
 <span data-ttu-id="41a3f-115">`file` não pode conter um assembly.</span><span class="sxs-lookup"><span data-stu-id="41a3f-115">`file` cannot contain an assembly.</span></span> <span data-ttu-id="41a3f-116">Por exemplo, se o arquivo de saída foi criado com [-target:module](./target-module-compiler-option.md), seus metadados podem ser importados com **-addmodule**.</span><span class="sxs-lookup"><span data-stu-id="41a3f-116">For example, if the output file was created with [-target:module](./target-module-compiler-option.md), its metadata can be imported with **-addmodule**.</span></span>  
  
 <span data-ttu-id="41a3f-117">Se o arquivo de saída tiver sido criado com uma opção **-target** diferente de **-target:module**, seus metadados não poderão ser importados com o **-addmodule**, mas poderão ser importados com [-reference](./reference-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="41a3f-117">If the output file was created with a **-target** option other than **-target:module**, its metadata cannot be imported with **-addmodule** but can be imported with [-reference](./reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="41a3f-118">Essa opção do compilador não está disponível no Visual Studio; um projeto não pode referenciar um módulo.</span><span class="sxs-lookup"><span data-stu-id="41a3f-118">This compiler option is unavailable in Visual Studio; a project cannot reference a module.</span></span> <span data-ttu-id="41a3f-119">Além disso, essa opção do compilador não pode ser alterada programaticamente.</span><span class="sxs-lookup"><span data-stu-id="41a3f-119">In addition, this compiler option cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41a3f-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41a3f-120">Example</span></span>  

 <span data-ttu-id="41a3f-121">Compile o arquivo de origem `input.cs` e adicione metadados de `metad1.netmodule` e `metad2.netmodule` para produzir `out.exe`:</span><span class="sxs-lookup"><span data-stu-id="41a3f-121">Compile source file `input.cs` and add metadata from `metad1.netmodule` and `metad2.netmodule` to produce `out.exe`:</span></span>  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="41a3f-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="41a3f-122">See also</span></span>

- [<span data-ttu-id="41a3f-123">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="41a3f-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="41a3f-124">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="41a3f-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="41a3f-125">Assemblies de multiarquivo</span><span class="sxs-lookup"><span data-stu-id="41a3f-125">Multifile Assemblies</span></span>](../../../framework/app-domains/multifile-assemblies.md)
- [<span data-ttu-id="41a3f-126">Como compilar um assembly de multiarquivos</span><span class="sxs-lookup"><span data-stu-id="41a3f-126">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
