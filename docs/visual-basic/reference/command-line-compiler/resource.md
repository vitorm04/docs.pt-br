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
ms.openlocfilehash: a781d543dd32ffb3d0ac0b11c544dbfd8cd5d806
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348562"
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="99d1b-102">-resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99d1b-102">-resource (Visual Basic)</span></span>
<span data-ttu-id="99d1b-103">Embeds a managed resource in an assembly.</span><span class="sxs-lookup"><span data-stu-id="99d1b-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99d1b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="99d1b-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="99d1b-105">ou</span><span class="sxs-lookup"><span data-stu-id="99d1b-105">or</span></span>  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="99d1b-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="99d1b-106">Arguments</span></span>  
  
|<span data-ttu-id="99d1b-107">Termo</span><span class="sxs-lookup"><span data-stu-id="99d1b-107">Term</span></span>|<span data-ttu-id="99d1b-108">Definição</span><span class="sxs-lookup"><span data-stu-id="99d1b-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="99d1b-109">Necessário.</span><span class="sxs-lookup"><span data-stu-id="99d1b-109">Required.</span></span> <span data-ttu-id="99d1b-110">The name of the resource file to embed in the output file.</span><span class="sxs-lookup"><span data-stu-id="99d1b-110">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="99d1b-111">By default, `filename` is public in the assembly.</span><span class="sxs-lookup"><span data-stu-id="99d1b-111">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="99d1b-112">Enclose the file name in quotation marks (" ") if it contains a space.</span><span class="sxs-lookup"><span data-stu-id="99d1b-112">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="99d1b-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="99d1b-113">Optional.</span></span> <span data-ttu-id="99d1b-114">The logical name for the resource; the name used to load it.</span><span class="sxs-lookup"><span data-stu-id="99d1b-114">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="99d1b-115">O padrão é o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="99d1b-115">The default is the name of the file.</span></span> <span data-ttu-id="99d1b-116">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="99d1b-116">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99d1b-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="99d1b-117">Remarks</span></span>  
 <span data-ttu-id="99d1b-118">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span><span class="sxs-lookup"><span data-stu-id="99d1b-118">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="99d1b-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span><span class="sxs-lookup"><span data-stu-id="99d1b-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="99d1b-120">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="99d1b-120">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="99d1b-121">A forma abreviada de `-resource` é `-res`.</span><span class="sxs-lookup"><span data-stu-id="99d1b-121">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="99d1b-122">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="99d1b-122">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="99d1b-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99d1b-123">Example</span></span>  
 <span data-ttu-id="99d1b-124">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="99d1b-124">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="99d1b-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99d1b-125">See also</span></span>

- [<span data-ttu-id="99d1b-126">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="99d1b-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="99d1b-127">-win32resource</span><span class="sxs-lookup"><span data-stu-id="99d1b-127">-win32resource</span></span>](../../../visual-basic/reference/command-line-compiler/win32resource.md)
- [<span data-ttu-id="99d1b-128">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99d1b-128">-linkresource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/linkresource.md)
- [<span data-ttu-id="99d1b-129">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99d1b-129">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="99d1b-130">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="99d1b-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
