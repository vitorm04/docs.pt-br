---
title: -addmodule (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: 39955d86085b49ef503ea9ed531df9feafa648ac
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524582"
---
# <a name="-addmodule-c-compiler-options"></a><span data-ttu-id="ea5f0-102">-addmodule (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="ea5f0-102">-addmodule (C# Compiler Options)</span></span>
<span data-ttu-id="ea5f0-103">Essa opção adiciona um módulo criado com a opção target:module para a compilação atual.</span><span class="sxs-lookup"><span data-stu-id="ea5f0-103">This option adds a module that was created with the target:module switch to the current compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea5f0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea5f0-104">Syntax</span></span>  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ea5f0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ea5f0-105">Arguments</span></span>  
 <span data-ttu-id="ea5f0-106">`file`, `file2`</span><span class="sxs-lookup"><span data-stu-id="ea5f0-106">`file`, `file2`</span></span>  
 <span data-ttu-id="ea5f0-107">Um arquivo de saída que contém metadados.</span><span class="sxs-lookup"><span data-stu-id="ea5f0-107">An output file that contains metadata.</span></span> <span data-ttu-id="ea5f0-108">O arquivo não pode conter um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="ea5f0-108">The file cannot contain an assembly manifest.</span></span> <span data-ttu-id="ea5f0-109">Para importar mais de um arquivo, separe os nomes de arquivo com vírgula ou ponto e vírgula.</span><span class="sxs-lookup"><span data-stu-id="ea5f0-109">To import more than one file, separate file names with either a comma or a semicolon.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea5f0-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="ea5f0-110">Remarks</span></span>  
 <span data-ttu-id="ea5f0-111">Todos os módulos adicionados com **-addmodule** devem estar no mesmo diretório que o arquivo de saída em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ea5f0-111">All modules added with **-addmodule** must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="ea5f0-112">Ou seja, é possível especificar um módulo em qualquer diretório em tempo de compilação, mas o módulo deve estar no diretório do aplicativo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ea5f0-112">That is, you can specify a module in any directory at compile time but the module must be in the application directory at run time.</span></span> <span data-ttu-id="ea5f0-113">Se o módulo não estiver no diretório do aplicativo em tempo de execução, um <xref:System.TypeLoadException> será obtido.</span><span class="sxs-lookup"><span data-stu-id="ea5f0-113">If the module is not in the application directory at run time, you will get a <xref:System.TypeLoadException>.</span></span>  
  
 <span data-ttu-id="ea5f0-114">`file` não pode conter um assembly.</span><span class="sxs-lookup"><span data-stu-id="ea5f0-114">`file` cannot contain an assembly.</span></span> <span data-ttu-id="ea5f0-115">Por exemplo, se o arquivo de saída foi criado com [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), seus metadados podem ser importados com **-addmodule**.</span><span class="sxs-lookup"><span data-stu-id="ea5f0-115">For example, if the output file was created with [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), its metadata can be imported with **-addmodule**.</span></span>  
  
 <span data-ttu-id="ea5f0-116">Se o arquivo de saída tiver sido criado com uma opção **-target** diferente de **-target:module**, seus metadados não poderão ser importados com o **-addmodule**, mas poderão ser importados com [-reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="ea5f0-116">If the output file was created with a **-target** option other than **-target:module**, its metadata cannot be imported with **-addmodule** but can be imported with [-reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="ea5f0-117">Essa opção do compilador não está disponível no Visual Studio; um projeto não pode referenciar um módulo.</span><span class="sxs-lookup"><span data-stu-id="ea5f0-117">This compiler option is unavailable in Visual Studio; a project cannot reference a module.</span></span> <span data-ttu-id="ea5f0-118">Além disso, essa opção do compilador não pode ser alterada programaticamente.</span><span class="sxs-lookup"><span data-stu-id="ea5f0-118">In addition, this compiler option cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea5f0-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ea5f0-119">Example</span></span>  
 <span data-ttu-id="ea5f0-120">Compile o arquivo de origem `input.cs` e adicione metadados de `metad1.netmodule` e `metad2.netmodule` para produzir `out.exe`:</span><span class="sxs-lookup"><span data-stu-id="ea5f0-120">Compile source file `input.cs` and add metadata from `metad1.netmodule` and `metad2.netmodule` to produce `out.exe`:</span></span>  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea5f0-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea5f0-121">See Also</span></span>  

- [<span data-ttu-id="ea5f0-122">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="ea5f0-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="ea5f0-123">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="ea5f0-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
- [<span data-ttu-id="ea5f0-124">Assemblies de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="ea5f0-124">Multifile Assemblies</span></span>](../../../framework/app-domains/multifile-assemblies.md)  
- [<span data-ttu-id="ea5f0-125">Como Compilar um Assembly de Vários Arquivos</span><span class="sxs-lookup"><span data-stu-id="ea5f0-125">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
