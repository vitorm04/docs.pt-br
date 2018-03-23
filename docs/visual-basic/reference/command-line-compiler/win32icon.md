---
title: -win32icon
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95b2e2b4542f2e396a136f6a3d9baeb3e0c037a3
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-win32icon"></a><span data-ttu-id="31a44-102">-win32icon</span><span class="sxs-lookup"><span data-stu-id="31a44-102">-win32icon</span></span>
<span data-ttu-id="31a44-103">Insere um arquivo. ico no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="31a44-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="31a44-104">Esse arquivo. ico representa o arquivo de saída em **Explorador de arquivos**.</span><span class="sxs-lookup"><span data-stu-id="31a44-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31a44-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="31a44-105">Syntax</span></span>  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="31a44-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="31a44-106">Arguments</span></span>  
  
|<span data-ttu-id="31a44-107">Termo</span><span class="sxs-lookup"><span data-stu-id="31a44-107">Term</span></span>|<span data-ttu-id="31a44-108">Definição</span><span class="sxs-lookup"><span data-stu-id="31a44-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="31a44-109">O arquivo. ico para adicionar ao seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="31a44-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="31a44-110">Coloque o nome do arquivo entre aspas ("") se ele contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="31a44-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31a44-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="31a44-111">Remarks</span></span>  
 <span data-ttu-id="31a44-112">Você pode criar um arquivo. ico com o compilador de recurso do Microsoft Windows (RC).</span><span class="sxs-lookup"><span data-stu-id="31a44-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="31a44-113">O compilador de recurso é chamado quando você compila um programa do Visual C++; é criado um arquivo. ico do arquivo. rc.</span><span class="sxs-lookup"><span data-stu-id="31a44-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="31a44-114">O `-win32icon` e `-win32resource` são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="31a44-114">The `-win32icon` and `-win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="31a44-115">Consulte [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) a referência de um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arquivo de recurso, ou [-recurso (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) para anexar um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="31a44-115">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span> <span data-ttu-id="31a44-116">Consulte [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) para importar um arquivo. res.</span><span class="sxs-lookup"><span data-stu-id="31a44-116">See [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="31a44-117">Para definir - win32icon no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="31a44-117">To set -win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="31a44-118">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="31a44-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="31a44-119">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="31a44-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="31a44-120">2.  Clique na guia **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="31a44-120">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="31a44-121">3.  Modificar o valor de **ícone** caixa.</span><span class="sxs-lookup"><span data-stu-id="31a44-121">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="31a44-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="31a44-122">Example</span></span>  
 <span data-ttu-id="31a44-123">O código a seguir compila `In.vb` e anexa um arquivo. ico, `Rf.ico`.</span><span class="sxs-lookup"><span data-stu-id="31a44-123">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="31a44-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31a44-124">See Also</span></span>  
 [<span data-ttu-id="31a44-125">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="31a44-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="31a44-126">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="31a44-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
