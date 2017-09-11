---
title: /linkresource (Visual Basic) | Documentos do Microsoft
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
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8d4d2d2fdacef0c830414790efa544a96c35fd3c
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="linkresource-visual-basic"></a><span data-ttu-id="3f6a9-102">/linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f6a9-102">/linkresource (Visual Basic)</span></span>
<span data-ttu-id="3f6a9-103">Cria um link a um recurso gerenciado.</span><span class="sxs-lookup"><span data-stu-id="3f6a9-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f6a9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3f6a9-104">Syntax</span></span>  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3f6a9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3f6a9-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="3f6a9-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="3f6a9-106">Required.</span></span> <span data-ttu-id="3f6a9-107">O arquivo de recurso para vincular ao assembly.</span><span class="sxs-lookup"><span data-stu-id="3f6a9-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="3f6a9-108">Se o nome do arquivo contém um espaço, coloque o nome entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="3f6a9-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="3f6a9-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3f6a9-109">Optional.</span></span> <span data-ttu-id="3f6a9-110">O nome lógico para o recurso.</span><span class="sxs-lookup"><span data-stu-id="3f6a9-110">The logical name for the resource.</span></span> <span data-ttu-id="3f6a9-111">O nome que é usado para carregar o recurso.</span><span class="sxs-lookup"><span data-stu-id="3f6a9-111">The name that is used to load the resource.</span></span> <span data-ttu-id="3f6a9-112">O padrão é o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="3f6a9-112">The default is the name of the file.</span></span> <span data-ttu-id="3f6a9-113">Opcionalmente, você pode especificar se o arquivo é pública ou privada no manifesto do assembly, por exemplo: `/linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="3f6a9-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `/linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="3f6a9-114">Por padrão, `filename` é público no assembly.</span><span class="sxs-lookup"><span data-stu-id="3f6a9-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f6a9-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="3f6a9-115">Remarks</span></span>  
 <span data-ttu-id="3f6a9-116">O `/linkresource` opção não insere o arquivo de recurso no arquivo de saída; use o `/resource` como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="3f6a9-116">The `/linkresource` option does not embed the resource file in the output file; use the `/resource` option to do this.</span></span>  
  
 <span data-ttu-id="3f6a9-117">O `/linkresource` opção requer um do `/target` diferente de opções `/target:module`.</span><span class="sxs-lookup"><span data-stu-id="3f6a9-117">The `/linkresource` option requires one of the `/target` options other than `/target:module`.</span></span>  
  
 <span data-ttu-id="3f6a9-118">Se `filename` é um [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] arquivo de recurso criado, por exemplo, pelo [Resgen.exe (gerador de arquivo)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ou no ambiente de desenvolvimento, ele pode ser acessado com membros de <xref:System.Resources>namespace.</xref:System.Resources></span><span class="sxs-lookup"><span data-stu-id="3f6a9-118">If `filename` is a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="3f6a9-119">(Para obter mais informações, consulte <xref:System.Resources.ResourceManager>.)</xref:System.Resources.ResourceManager> Para acessar todos os outros recursos em tempo de execução, use os métodos que começam com `GetManifestResource` na <xref:System.Reflection.Assembly>classe.</xref:System.Reflection.Assembly></span><span class="sxs-lookup"><span data-stu-id="3f6a9-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="3f6a9-120">O nome do arquivo pode ser qualquer formato de arquivo.</span><span class="sxs-lookup"><span data-stu-id="3f6a9-120">The file name can be any file format.</span></span> <span data-ttu-id="3f6a9-121">Por exemplo, você talvez queira fazer uma parte DLL nativa do assembly, para que possa ser instalado no cache de assembly global e acessado a partir do código gerenciado no assembly.</span><span class="sxs-lookup"><span data-stu-id="3f6a9-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="3f6a9-122">A forma abreviada do `/linkresource` é `/linkres`.</span><span class="sxs-lookup"><span data-stu-id="3f6a9-122">The short form of `/linkresource` is `/linkres`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f6a9-123">O `/linkresource` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente quando você compilar na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="3f6a9-123">The `/linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f6a9-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3f6a9-124">Example</span></span>  
 <span data-ttu-id="3f6a9-125">O seguinte código compila `In.vb` e links para o arquivo de recurso `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="3f6a9-125">The following code compiles `In.vb` and links to resource file `Rf.resource`.</span></span>  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f6a9-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f6a9-126">See Also</span></span>  
 <span data-ttu-id="3f6a9-127">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="3f6a9-127">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="3f6a9-128"> [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="3f6a9-128"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="3f6a9-129"> [/Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) </span><span class="sxs-lookup"><span data-stu-id="3f6a9-129"> [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) </span></span>  
<span data-ttu-id="3f6a9-130"> [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="3f6a9-130"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
