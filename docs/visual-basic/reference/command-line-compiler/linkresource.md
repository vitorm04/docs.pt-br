---
title: -linkresource (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: d92b0d08daf660880b648875c67c3b78069143d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924848"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="bff15-102">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bff15-102">-linkresource (Visual Basic)</span></span>
<span data-ttu-id="bff15-103">Cria um link a um recurso gerenciado.</span><span class="sxs-lookup"><span data-stu-id="bff15-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bff15-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bff15-104">Syntax</span></span>  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="bff15-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="bff15-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="bff15-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="bff15-106">Required.</span></span> <span data-ttu-id="bff15-107">O arquivo de recurso a ser vinculado ao assembly.</span><span class="sxs-lookup"><span data-stu-id="bff15-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="bff15-108">Se o nome do arquivo contiver um espaço, coloque o nome entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="bff15-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="bff15-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="bff15-109">Optional.</span></span> <span data-ttu-id="bff15-110">O nome lógico do recurso.</span><span class="sxs-lookup"><span data-stu-id="bff15-110">The logical name for the resource.</span></span> <span data-ttu-id="bff15-111">O nome usado para carregar o recurso.</span><span class="sxs-lookup"><span data-stu-id="bff15-111">The name that is used to load the resource.</span></span> <span data-ttu-id="bff15-112">O padrão é o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="bff15-112">The default is the name of the file.</span></span> <span data-ttu-id="bff15-113">Opcionalmente, você pode especificar se o arquivo é público ou privado no manifesto do assembly, por exemplo: `-linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="bff15-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="bff15-114">Por padrão, `filename` é público no assembly.</span><span class="sxs-lookup"><span data-stu-id="bff15-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bff15-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="bff15-115">Remarks</span></span>  
 <span data-ttu-id="bff15-116">A `-linkresource` opção não incorpora o arquivo de recurso no arquivo de saída; use a `-resource` opção para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="bff15-116">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="bff15-117">A `-linkresource` opção requer uma `-target` das opções diferentes de `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="bff15-117">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="bff15-118">Se `filename` for um arquivo de recurso .NET Framework criado, por exemplo, pelo [Resgen. exe (gerador de arquivo de recurso)](../../../framework/tools/resgen-exe-resource-file-generator.md) ou no ambiente de desenvolvimento, ele poderá ser acessado <xref:System.Resources> com membros no namespace.</span><span class="sxs-lookup"><span data-stu-id="bff15-118">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="bff15-119">(Para obter mais informações, consulte <xref:System.Resources.ResourceManager>.) Para acessar todos os outros recursos em tempo de execução, use os métodos que `GetManifestResource` começam com <xref:System.Reflection.Assembly> na classe.</span><span class="sxs-lookup"><span data-stu-id="bff15-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="bff15-120">O nome do arquivo pode ser qualquer formato de arquivo.</span><span class="sxs-lookup"><span data-stu-id="bff15-120">The file name can be any file format.</span></span> <span data-ttu-id="bff15-121">Por exemplo, crie uma parte DLL nativa do assembly de maneira que possa ser instalada no cache de assembly global e acessado no código gerenciado no assembly.</span><span class="sxs-lookup"><span data-stu-id="bff15-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="bff15-122">A forma abreviada de `-linkresource` é `-linkres`.</span><span class="sxs-lookup"><span data-stu-id="bff15-122">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bff15-123">A `-linkresource` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ela está disponível somente quando você compila a partir da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="bff15-123">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bff15-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bff15-124">Example</span></span>  
 <span data-ttu-id="bff15-125">O código a seguir compila `in.vb` e vincula ao arquivo `rf.resource`de recurso.</span><span class="sxs-lookup"><span data-stu-id="bff15-125">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="bff15-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bff15-126">See also</span></span>

- [<span data-ttu-id="bff15-127">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bff15-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="bff15-128">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bff15-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="bff15-129">-recurso (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bff15-129">-resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)
- [<span data-ttu-id="bff15-130">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="bff15-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
