---
title: -resource
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: cf9fe8dae0d35df694891633a6e3cf950bfb7376
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363611"
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="856ff-102">-recurso (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="856ff-102">-resource (Visual Basic)</span></span>
<span data-ttu-id="856ff-103">Insere um recurso gerenciado em um assembly.</span><span class="sxs-lookup"><span data-stu-id="856ff-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="856ff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="856ff-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="856ff-105">ou</span><span class="sxs-lookup"><span data-stu-id="856ff-105">or</span></span>  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="856ff-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="856ff-106">Arguments</span></span>  
  
|<span data-ttu-id="856ff-107">Termo</span><span class="sxs-lookup"><span data-stu-id="856ff-107">Term</span></span>|<span data-ttu-id="856ff-108">Definição</span><span class="sxs-lookup"><span data-stu-id="856ff-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="856ff-109">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="856ff-109">Required.</span></span> <span data-ttu-id="856ff-110">O nome do arquivo de recurso a ser inserido no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="856ff-110">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="856ff-111">Por padrão, `filename` é público no assembly.</span><span class="sxs-lookup"><span data-stu-id="856ff-111">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="856ff-112">Coloque o nome de arquivo entre aspas ("") se ele contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="856ff-112">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="856ff-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="856ff-113">Optional.</span></span> <span data-ttu-id="856ff-114">O nome lógico do recurso; o nome usado para carregá-lo.</span><span class="sxs-lookup"><span data-stu-id="856ff-114">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="856ff-115">O padrão é o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="856ff-115">The default is the name of the file.</span></span> <span data-ttu-id="856ff-116">Opcionalmente, você pode especificar se o recurso é público ou privado no manifesto do assembly, como com o seguinte:`-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="856ff-116">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="856ff-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="856ff-117">Remarks</span></span>  
 <span data-ttu-id="856ff-118">Use `-linkresource` para vincular um recurso a um assembly sem colocar o arquivo de recurso no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="856ff-118">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="856ff-119">Se `filename` for um arquivo de recurso .NET Framework criado, por exemplo, pelo [Resgen. exe (gerador de arquivo de recurso)](../../../framework/tools/resgen-exe-resource-file-generator.md) ou no ambiente de desenvolvimento, ele poderá ser acessado com membros no <xref:System.Resources> namespace (consulte <xref:System.Resources.ResourceManager> para obter mais informações).</span><span class="sxs-lookup"><span data-stu-id="856ff-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="856ff-120">Para acessar todos os outros recursos em tempo de execução, use um dos seguintes métodos: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A> , <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> ou <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> .</span><span class="sxs-lookup"><span data-stu-id="856ff-120">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="856ff-121">A forma abreviada de `-resource` é `-res`.</span><span class="sxs-lookup"><span data-stu-id="856ff-121">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="856ff-122">Para obter informações sobre como definir `-resource` no IDE do Visual Studio, consulte [Gerenciando recursos de aplicativos (.net)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="856ff-122">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="856ff-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="856ff-123">Example</span></span>  
 <span data-ttu-id="856ff-124">O código a seguir compila `In.vb` e anexa o arquivo de recurso `Rf.resource` .</span><span class="sxs-lookup"><span data-stu-id="856ff-124">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="856ff-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="856ff-125">See also</span></span>

- [<span data-ttu-id="856ff-126">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="856ff-126">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="856ff-127">-win32resource</span><span class="sxs-lookup"><span data-stu-id="856ff-127">-win32resource</span></span>](win32resource.md)
- [<span data-ttu-id="856ff-128">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="856ff-128">-linkresource (Visual Basic)</span></span>](linkresource.md)
- [<span data-ttu-id="856ff-129">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="856ff-129">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="856ff-130">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="856ff-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
