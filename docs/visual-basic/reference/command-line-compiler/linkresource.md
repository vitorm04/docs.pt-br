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
ms.openlocfilehash: 97e0ccd46f413cc05b659731436bb141ee178419
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46478783"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="f920a-102">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f920a-102">-linkresource (Visual Basic)</span></span>
<span data-ttu-id="f920a-103">Cria um link a um recurso gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f920a-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f920a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f920a-104">Syntax</span></span>  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f920a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f920a-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="f920a-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="f920a-106">Required.</span></span> <span data-ttu-id="f920a-107">O arquivo de recurso para vincular ao assembly.</span><span class="sxs-lookup"><span data-stu-id="f920a-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="f920a-108">Se o nome do arquivo contiver um espaço, coloque o nome entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="f920a-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="f920a-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="f920a-109">Optional.</span></span> <span data-ttu-id="f920a-110">O nome lógico para o recurso.</span><span class="sxs-lookup"><span data-stu-id="f920a-110">The logical name for the resource.</span></span> <span data-ttu-id="f920a-111">O nome que é usado para carregar o recurso.</span><span class="sxs-lookup"><span data-stu-id="f920a-111">The name that is used to load the resource.</span></span> <span data-ttu-id="f920a-112">O padrão é o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="f920a-112">The default is the name of the file.</span></span> <span data-ttu-id="f920a-113">Opcionalmente, você pode especificar se o arquivo é pública ou privada no manifesto do assembly, por exemplo: `-linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="f920a-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="f920a-114">Por padrão, `filename` é público no assembly.</span><span class="sxs-lookup"><span data-stu-id="f920a-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f920a-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="f920a-115">Remarks</span></span>  
 <span data-ttu-id="f920a-116">O `-linkresource` opção não insere o arquivo de recurso no arquivo de saída; use o `-resource` opção para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="f920a-116">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="f920a-117">O `-linkresource` opção requer um dos `-target` diferente de opções `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="f920a-117">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="f920a-118">Se `filename` é um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arquivo de recurso criado, por exemplo, pelo [Resgen.exe (gerador de arquivo de recurso)](../../../framework/tools/resgen-exe-resource-file-generator.md) ou no ambiente de desenvolvimento, ele pode ser acessado com membros no <xref:System.Resources> namespace.</span><span class="sxs-lookup"><span data-stu-id="f920a-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="f920a-119">(Para obter mais informações, consulte <xref:System.Resources.ResourceManager>.) Para acessar todos os outros recursos em tempo de execução, use os métodos que começam com `GetManifestResource` no <xref:System.Reflection.Assembly> classe.</span><span class="sxs-lookup"><span data-stu-id="f920a-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="f920a-120">O nome do arquivo pode ser qualquer formato de arquivo.</span><span class="sxs-lookup"><span data-stu-id="f920a-120">The file name can be any file format.</span></span> <span data-ttu-id="f920a-121">Por exemplo, crie uma parte DLL nativa do assembly de maneira que possa ser instalada no cache de assembly global e acessado no código gerenciado no assembly.</span><span class="sxs-lookup"><span data-stu-id="f920a-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="f920a-122">A forma abreviada de `-linkresource` é `-linkres`.</span><span class="sxs-lookup"><span data-stu-id="f920a-122">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f920a-123">O `-linkresource` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando você compila da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="f920a-123">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f920a-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f920a-124">Example</span></span>  
 <span data-ttu-id="f920a-125">O seguinte código compila `in.vb` e links para o arquivo de recurso `rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="f920a-125">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f920a-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f920a-126">See also</span></span>

- [<span data-ttu-id="f920a-127">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f920a-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
- [<span data-ttu-id="f920a-128">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f920a-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
- [<span data-ttu-id="f920a-129">-resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f920a-129">-resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)  
- [<span data-ttu-id="f920a-130">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="f920a-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
