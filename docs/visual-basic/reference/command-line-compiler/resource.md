---
title: /Resource (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2278902f96f7b6349e91a9803f58c3caa89f4f33
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="resource-visual-basic"></a><span data-ttu-id="a3334-102">/resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3334-102">/resource (Visual Basic)</span></span>
<span data-ttu-id="a3334-103">Insere um recurso gerenciado em um assembly.</span><span class="sxs-lookup"><span data-stu-id="a3334-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3334-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3334-104">Syntax</span></span>  
  
```  
/resource:filename[,identifier[,public|private]]  
' -or-  
/res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a3334-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a3334-105">Arguments</span></span>  
  
|<span data-ttu-id="a3334-106">Termo</span><span class="sxs-lookup"><span data-stu-id="a3334-106">Term</span></span>|<span data-ttu-id="a3334-107">Definição</span><span class="sxs-lookup"><span data-stu-id="a3334-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="a3334-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a3334-108">Required.</span></span> <span data-ttu-id="a3334-109">O nome do arquivo de recurso incorporado no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="a3334-109">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="a3334-110">Por padrão, `filename` é público no assembly.</span><span class="sxs-lookup"><span data-stu-id="a3334-110">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="a3334-111">Coloque o nome do arquivo entre aspas ("") se ele contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="a3334-111">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="a3334-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a3334-112">Optional.</span></span> <span data-ttu-id="a3334-113">O nome lógico para o recurso. o nome usado para carregá-lo.</span><span class="sxs-lookup"><span data-stu-id="a3334-113">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="a3334-114">O padrão é o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="a3334-114">The default is the name of the file.</span></span> <span data-ttu-id="a3334-115">Opcionalmente, você pode especificar se o recurso é pública ou privada no manifesto do assembly, assim como acontece com o seguinte: `/res:``filename.res`,`myname.res`,`public`</span><span class="sxs-lookup"><span data-stu-id="a3334-115">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `/res:``filename.res`,`myname.res`,`public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3334-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="a3334-116">Remarks</span></span>  
 <span data-ttu-id="a3334-117">Use `/linkresource` para vincular um recurso a um assembly sem colocar o arquivo de recurso no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="a3334-117">Use `/linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="a3334-118">Se `filename` é um [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] arquivo de recurso criado, por exemplo, pelo [Resgen.exe (gerador de arquivo)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ou no ambiente de desenvolvimento, ele pode ser acessado com membros de <xref:System.Resources>namespace (consulte <xref:System.Resources.ResourceManager>para obter mais informações).</xref:System.Resources.ResourceManager> </xref:System.Resources></span><span class="sxs-lookup"><span data-stu-id="a3334-118">If `filename` is a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="a3334-119">Para acessar todos os outros recursos em tempo de execução, use um dos seguintes métodos: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, ou <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</xref:System.Reflection.Assembly.GetManifestResourceStream%2A> </xref:System.Reflection.Assembly.GetManifestResourceNames%2A> </xref:System.Reflection.Assembly.GetManifestResourceInfo%2A></span><span class="sxs-lookup"><span data-stu-id="a3334-119">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="a3334-120">A forma abreviada do `/resource` é `/res`.</span><span class="sxs-lookup"><span data-stu-id="a3334-120">The short form of `/resource` is `/res`.</span></span>  
  
 <span data-ttu-id="a3334-121">Para obter informações sobre como definir `/resource` no IDE do Visual Studio, consulte [recursos de gerenciamento de aplicativo (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="a3334-121">For information about how to set `/resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3334-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a3334-122">Example</span></span>  
 <span data-ttu-id="a3334-123">O seguinte código compila `In.vb` e anexa arquivos de recurso `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="a3334-123">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```  
vbc /res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3334-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3334-124">See Also</span></span>  
 <span data-ttu-id="a3334-125">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="a3334-125">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="a3334-126"> [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) </span><span class="sxs-lookup"><span data-stu-id="a3334-126"> [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) </span></span>  
<span data-ttu-id="a3334-127"> [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) </span><span class="sxs-lookup"><span data-stu-id="a3334-127"> [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) </span></span>  
<span data-ttu-id="a3334-128"> [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="a3334-128"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="a3334-129"> [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="a3334-129"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
