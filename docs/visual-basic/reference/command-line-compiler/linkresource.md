---
title: -linkresource
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 8c4f753f94aedaf0a4f997a3f9b99fb3f417abf8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91065678"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="1c148-102">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c148-102">-linkresource (Visual Basic)</span></span>

<span data-ttu-id="1c148-103">Cria um link a um recurso gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1c148-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c148-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c148-104">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="1c148-105">ou</span><span class="sxs-lookup"><span data-stu-id="1c148-105">or</span></span>  

```console
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1c148-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="1c148-106">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="1c148-107">Necessário.</span><span class="sxs-lookup"><span data-stu-id="1c148-107">Required.</span></span> <span data-ttu-id="1c148-108">O arquivo de recurso a ser vinculado ao assembly.</span><span class="sxs-lookup"><span data-stu-id="1c148-108">The resource file to link to the assembly.</span></span> <span data-ttu-id="1c148-109">Se o nome do arquivo contiver um espaço, coloque o nome entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="1c148-109">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="1c148-110">Opcional.</span><span class="sxs-lookup"><span data-stu-id="1c148-110">Optional.</span></span> <span data-ttu-id="1c148-111">O nome lógico do recurso.</span><span class="sxs-lookup"><span data-stu-id="1c148-111">The logical name for the resource.</span></span> <span data-ttu-id="1c148-112">O nome usado para carregar o recurso.</span><span class="sxs-lookup"><span data-stu-id="1c148-112">The name that is used to load the resource.</span></span> <span data-ttu-id="1c148-113">O padrão é o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="1c148-113">The default is the name of the file.</span></span> <span data-ttu-id="1c148-114">Opcionalmente, você pode especificar se o arquivo é público ou privado no manifesto do assembly, por exemplo: `-linkres:filename.res,myname.res,public` .</span><span class="sxs-lookup"><span data-stu-id="1c148-114">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="1c148-115">Por padrão, `filename` é público no assembly.</span><span class="sxs-lookup"><span data-stu-id="1c148-115">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c148-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="1c148-116">Remarks</span></span>  

 <span data-ttu-id="1c148-117">A `-linkresource` opção não incorpora o arquivo de recurso no arquivo de saída; use a `-resource` opção para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="1c148-117">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="1c148-118">A `-linkresource` opção requer uma das `-target` opções diferentes de `-target:module` .</span><span class="sxs-lookup"><span data-stu-id="1c148-118">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="1c148-119">Se `filename` for um arquivo de recurso .NET Framework criado, por exemplo, pelo [Resgen.exe (gerador de arquivo de recurso)](../../../framework/tools/resgen-exe-resource-file-generator.md) ou no ambiente de desenvolvimento, ele poderá ser acessado com membros no <xref:System.Resources> namespace.</span><span class="sxs-lookup"><span data-stu-id="1c148-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="1c148-120">(Para obter mais informações, consulte <xref:System.Resources.ResourceManager> .) Para acessar todos os outros recursos em tempo de execução, use os métodos que começam com `GetManifestResource` na <xref:System.Reflection.Assembly> classe.</span><span class="sxs-lookup"><span data-stu-id="1c148-120">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="1c148-121">O nome do arquivo pode ser qualquer formato de arquivo.</span><span class="sxs-lookup"><span data-stu-id="1c148-121">The file name can be any file format.</span></span> <span data-ttu-id="1c148-122">Por exemplo, crie uma parte DLL nativa do assembly de maneira que possa ser instalada no cache de assembly global e acessado no código gerenciado no assembly.</span><span class="sxs-lookup"><span data-stu-id="1c148-122">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="1c148-123">A forma abreviada de `-linkresource` é `-linkres`.</span><span class="sxs-lookup"><span data-stu-id="1c148-123">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c148-124">A `-linkresource` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ela está disponível somente quando você compila a partir da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="1c148-124">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c148-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c148-125">Example</span></span>  

 <span data-ttu-id="1c148-126">O código a seguir compila `in.vb` e vincula ao arquivo de recurso `rf.resource` .</span><span class="sxs-lookup"><span data-stu-id="1c148-126">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c148-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="1c148-127">See also</span></span>

- [<span data-ttu-id="1c148-128">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1c148-128">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="1c148-129">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c148-129">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="1c148-130">-recurso (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c148-130">-resource (Visual Basic)</span></span>](resource.md)
- [<span data-ttu-id="1c148-131">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c148-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
