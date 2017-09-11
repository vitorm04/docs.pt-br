---
title: /win32icon | Documentos do Microsoft
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
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
caps.latest.revision: 13
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
ms.openlocfilehash: f7d451026438be722d6cb7eecfffe397ccff82ae
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="win32icon"></a><span data-ttu-id="d081d-102">/win32icon</span><span class="sxs-lookup"><span data-stu-id="d081d-102">/win32icon</span></span>
<span data-ttu-id="d081d-103">Insere um arquivo. ico no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="d081d-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="d081d-104">Esse arquivo. ico representa o arquivo de saída na **File Explorer**.</span><span class="sxs-lookup"><span data-stu-id="d081d-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d081d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d081d-105">Syntax</span></span>  
  
```  
/win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="d081d-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="d081d-106">Arguments</span></span>  
  
|<span data-ttu-id="d081d-107">Termo</span><span class="sxs-lookup"><span data-stu-id="d081d-107">Term</span></span>|<span data-ttu-id="d081d-108">Definição</span><span class="sxs-lookup"><span data-stu-id="d081d-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="d081d-109">O arquivo. ico para adicionar ao seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="d081d-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="d081d-110">Coloque o nome do arquivo entre aspas ("") se ele contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="d081d-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d081d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d081d-111">Remarks</span></span>  
 <span data-ttu-id="d081d-112">Você pode criar um arquivo. ico com o compilador de recursos do Microsoft Windows (RC).</span><span class="sxs-lookup"><span data-stu-id="d081d-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="d081d-113">O compilador de recurso é chamado quando você compila um programa do Visual C++; é criado um arquivo. ico no arquivo. rc.</span><span class="sxs-lookup"><span data-stu-id="d081d-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="d081d-114">O `/win32icon` e `/win32resource` são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="d081d-114">The `/win32icon` and `/win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="d081d-115">Consulte [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) a referência de um [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] arquivo de recurso, ou [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) para anexar um [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="d081d-115">See [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] resource file, or [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] resource file.</span></span> <span data-ttu-id="d081d-116">Consulte [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) para importar um arquivo. res.</span><span class="sxs-lookup"><span data-stu-id="d081d-116">See [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="d081d-117">Definir /win32icon no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d081d-117">To set /win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="d081d-118">1.  Tenha um projeto selecionado no **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="d081d-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d081d-119">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="d081d-119">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="d081d-120">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="d081d-120">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="d081d-121">2.  Clique o **aplicativo** guia.</span><span class="sxs-lookup"><span data-stu-id="d081d-121">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="d081d-122">3.  Modificar o valor de **ícone** caixa.</span><span class="sxs-lookup"><span data-stu-id="d081d-122">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d081d-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d081d-123">Example</span></span>  
 <span data-ttu-id="d081d-124">O seguinte código compila `In.vb` e anexa um arquivo. ico, `Rf.ico`.</span><span class="sxs-lookup"><span data-stu-id="d081d-124">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```  
vbc /win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d081d-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d081d-125">See Also</span></span>  
 <span data-ttu-id="d081d-126">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="d081d-126">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="d081d-127"> [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="d081d-127"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
