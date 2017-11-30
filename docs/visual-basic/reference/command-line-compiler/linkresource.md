---
title: /linkresource (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e51f844695985485210a1e4bedfef7ac968326c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="linkresource-visual-basic"></a><span data-ttu-id="9e3f9-102">/linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e3f9-102">/linkresource (Visual Basic)</span></span>
<span data-ttu-id="9e3f9-103">Cria um link a um recurso gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9e3f9-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e3f9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e3f9-104">Syntax</span></span>  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9e3f9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9e3f9-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="9e3f9-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9e3f9-106">Required.</span></span> <span data-ttu-id="9e3f9-107">O arquivo de recurso para vincular ao assembly.</span><span class="sxs-lookup"><span data-stu-id="9e3f9-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="9e3f9-108">Se o nome do arquivo contém um espaço, coloque o nome entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="9e3f9-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="9e3f9-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9e3f9-109">Optional.</span></span> <span data-ttu-id="9e3f9-110">O nome lógico para o recurso.</span><span class="sxs-lookup"><span data-stu-id="9e3f9-110">The logical name for the resource.</span></span> <span data-ttu-id="9e3f9-111">O nome que é usado para carregar o recurso.</span><span class="sxs-lookup"><span data-stu-id="9e3f9-111">The name that is used to load the resource.</span></span> <span data-ttu-id="9e3f9-112">O padrão é o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="9e3f9-112">The default is the name of the file.</span></span> <span data-ttu-id="9e3f9-113">Opcionalmente, você pode especificar se o arquivo é pública ou privada no manifesto do assembly, por exemplo: `/linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="9e3f9-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `/linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="9e3f9-114">Por padrão, `filename` é público no assembly.</span><span class="sxs-lookup"><span data-stu-id="9e3f9-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e3f9-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="9e3f9-115">Remarks</span></span>  
 <span data-ttu-id="9e3f9-116">O `/linkresource` opção não insere o arquivo de recurso no arquivo de saída; use o `/resource` opção para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="9e3f9-116">The `/linkresource` option does not embed the resource file in the output file; use the `/resource` option to do this.</span></span>  
  
 <span data-ttu-id="9e3f9-117">O `/linkresource` opção requer um do `/target` opções diferentes de `/target:module`.</span><span class="sxs-lookup"><span data-stu-id="9e3f9-117">The `/linkresource` option requires one of the `/target` options other than `/target:module`.</span></span>  
  
 <span data-ttu-id="9e3f9-118">Se `filename` é um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arquivo de recursos criado, por exemplo, pelo [Resgen.exe (gerador de arquivo)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ou no ambiente de desenvolvimento, ele pode ser acessado com membros no <xref:System.Resources> namespace.</span><span class="sxs-lookup"><span data-stu-id="9e3f9-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="9e3f9-119">(Para obter mais informações, consulte <xref:System.Resources.ResourceManager>.) Para acessar todos os outros recursos em tempo de execução, use os métodos que começam com `GetManifestResource` no <xref:System.Reflection.Assembly> classe.</span><span class="sxs-lookup"><span data-stu-id="9e3f9-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="9e3f9-120">O nome do arquivo pode ser qualquer formato de arquivo.</span><span class="sxs-lookup"><span data-stu-id="9e3f9-120">The file name can be any file format.</span></span> <span data-ttu-id="9e3f9-121">Por exemplo, crie uma parte DLL nativa do assembly de maneira que possa ser instalada no cache de assembly global e acessado no código gerenciado no assembly.</span><span class="sxs-lookup"><span data-stu-id="9e3f9-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="9e3f9-122">A forma abreviada de `/linkresource` é `/linkres`.</span><span class="sxs-lookup"><span data-stu-id="9e3f9-122">The short form of `/linkresource` is `/linkres`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e3f9-123">O `/linkresource` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível apenas quando você compila na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="9e3f9-123">The `/linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e3f9-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e3f9-124">Example</span></span>  
 <span data-ttu-id="9e3f9-125">O código a seguir compila `In.vb` e links para o arquivo de recurso `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="9e3f9-125">The following code compiles `In.vb` and links to resource file `Rf.resource`.</span></span>  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e3f9-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e3f9-126">See Also</span></span>  
 [<span data-ttu-id="9e3f9-127">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9e3f9-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="9e3f9-128">/Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e3f9-128">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="9e3f9-129">/Resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e3f9-129">/resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)  
 [<span data-ttu-id="9e3f9-130">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e3f9-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
