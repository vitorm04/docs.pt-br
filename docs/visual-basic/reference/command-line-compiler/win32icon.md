---
title: /win32icon
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65149c617220966bc3bb6897d757a71cd60167d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="win32icon"></a><span data-ttu-id="35c32-102">/win32icon</span><span class="sxs-lookup"><span data-stu-id="35c32-102">/win32icon</span></span>
<span data-ttu-id="35c32-103">Insere um arquivo. ico no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="35c32-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="35c32-104">Esse arquivo. ico representa o arquivo de saída em **Explorador de arquivos**.</span><span class="sxs-lookup"><span data-stu-id="35c32-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35c32-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35c32-105">Syntax</span></span>  
  
```  
/win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="35c32-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="35c32-106">Arguments</span></span>  
  
|<span data-ttu-id="35c32-107">Termo</span><span class="sxs-lookup"><span data-stu-id="35c32-107">Term</span></span>|<span data-ttu-id="35c32-108">Definição</span><span class="sxs-lookup"><span data-stu-id="35c32-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="35c32-109">O arquivo. ico para adicionar ao seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="35c32-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="35c32-110">Coloque o nome do arquivo entre aspas ("") se ele contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="35c32-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35c32-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="35c32-111">Remarks</span></span>  
 <span data-ttu-id="35c32-112">Você pode criar um arquivo. ico com o compilador de recurso do Microsoft Windows (RC).</span><span class="sxs-lookup"><span data-stu-id="35c32-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="35c32-113">O compilador de recurso é chamado quando você compila um programa do Visual C++; é criado um arquivo. ico do arquivo. rc.</span><span class="sxs-lookup"><span data-stu-id="35c32-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="35c32-114">O `/win32icon` e `/win32resource` são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="35c32-114">The `/win32icon` and `/win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="35c32-115">Consulte [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) a referência de um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arquivo de recurso, ou [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) para anexar um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="35c32-115">See [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span> <span data-ttu-id="35c32-116">Consulte [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) para importar um arquivo. res.</span><span class="sxs-lookup"><span data-stu-id="35c32-116">See [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="35c32-117">Para definir /win32icon no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="35c32-117">To set /win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="35c32-118">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="35c32-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="35c32-119">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="35c32-119">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="35c32-120">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="35c32-120">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="35c32-121">2.  Clique na guia **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="35c32-121">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="35c32-122">3.  Modificar o valor de **ícone** caixa.</span><span class="sxs-lookup"><span data-stu-id="35c32-122">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="35c32-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35c32-123">Example</span></span>  
 <span data-ttu-id="35c32-124">O código a seguir compila `In.vb` e anexa um arquivo. ico, `Rf.ico`.</span><span class="sxs-lookup"><span data-stu-id="35c32-124">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```  
vbc /win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="35c32-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35c32-125">See Also</span></span>  
 [<span data-ttu-id="35c32-126">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="35c32-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="35c32-127">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="35c32-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
