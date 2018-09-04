---
title: -resource (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77c80332e663596244b35fe002218e7bcbaeb46a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523318"
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="ca23f-102">-resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca23f-102">-resource (Visual Basic)</span></span>
<span data-ttu-id="ca23f-103">Insere um recurso gerenciado em um assembly.</span><span class="sxs-lookup"><span data-stu-id="ca23f-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca23f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca23f-104">Syntax</span></span>  
  
```  
-resource:filename[,identifier[,public|private]]  
' -or-  
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ca23f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ca23f-105">Arguments</span></span>  
  
|<span data-ttu-id="ca23f-106">Termo</span><span class="sxs-lookup"><span data-stu-id="ca23f-106">Term</span></span>|<span data-ttu-id="ca23f-107">Definição</span><span class="sxs-lookup"><span data-stu-id="ca23f-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="ca23f-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="ca23f-108">Required.</span></span> <span data-ttu-id="ca23f-109">O nome do arquivo de recurso para inserir no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="ca23f-109">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="ca23f-110">Por padrão, `filename` é público no assembly.</span><span class="sxs-lookup"><span data-stu-id="ca23f-110">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="ca23f-111">Coloque o nome do arquivo entre aspas ("") se ele contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="ca23f-111">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="ca23f-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ca23f-112">Optional.</span></span> <span data-ttu-id="ca23f-113">O nome lógico do recurso; o nome usado para carregá-lo.</span><span class="sxs-lookup"><span data-stu-id="ca23f-113">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="ca23f-114">O padrão é o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="ca23f-114">The default is the name of the file.</span></span> <span data-ttu-id="ca23f-115">Opcionalmente, você pode especificar se o recurso é público ou privado no manifesto do assembly, assim como acontece com o seguinte: `-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="ca23f-115">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca23f-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca23f-116">Remarks</span></span>  
 <span data-ttu-id="ca23f-117">Use `-linkresource` para vincular um recurso a um assembly sem colocar o arquivo de recurso no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="ca23f-117">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="ca23f-118">Se `filename` é um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arquivo de recurso criado, por exemplo, pelo [Resgen.exe (gerador de arquivo de recurso)](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ou no ambiente de desenvolvimento, ele pode ser acessado com membros no <xref:System.Resources> namespace (veja <xref:System.Resources.ResourceManager> para obter mais informações).</span><span class="sxs-lookup"><span data-stu-id="ca23f-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="ca23f-119">Para acessar todos os outros recursos em tempo de execução, use um dos seguintes métodos: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, ou <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="ca23f-119">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="ca23f-120">A forma abreviada de `-resource` é `-res`.</span><span class="sxs-lookup"><span data-stu-id="ca23f-120">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="ca23f-121">Para obter informações sobre como definir `-resource` no IDE do Visual Studio, consulte [Gerenciando recursos de aplicativo (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="ca23f-121">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca23f-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ca23f-122">Example</span></span>  
 <span data-ttu-id="ca23f-123">O seguinte código compila `In.vb` e o arquivo de recurso anexa `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="ca23f-123">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca23f-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca23f-124">See Also</span></span>  
 [<span data-ttu-id="ca23f-125">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ca23f-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ca23f-126">-win32resource</span><span class="sxs-lookup"><span data-stu-id="ca23f-126">-win32resource</span></span>](../../../visual-basic/reference/command-line-compiler/win32resource.md)  
 [<span data-ttu-id="ca23f-127">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca23f-127">-linkresource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/linkresource.md)  
 [<span data-ttu-id="ca23f-128">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca23f-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="ca23f-129">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="ca23f-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
