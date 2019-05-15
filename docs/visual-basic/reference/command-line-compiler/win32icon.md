---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: dc48a8f79aa04892c514917da00b8fd6489695b1
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593091"
---
# <a name="-win32icon"></a><span data-ttu-id="86ffb-102">-win32icon</span><span class="sxs-lookup"><span data-stu-id="86ffb-102">-win32icon</span></span>
<span data-ttu-id="86ffb-103">Insere um arquivo. ico no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="86ffb-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="86ffb-104">Esse arquivo. ico representa o arquivo de saída no **Explorador de arquivos**.</span><span class="sxs-lookup"><span data-stu-id="86ffb-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86ffb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86ffb-105">Syntax</span></span>  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="86ffb-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="86ffb-106">Arguments</span></span>  
  
|<span data-ttu-id="86ffb-107">Termo</span><span class="sxs-lookup"><span data-stu-id="86ffb-107">Term</span></span>|<span data-ttu-id="86ffb-108">Definição</span><span class="sxs-lookup"><span data-stu-id="86ffb-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="86ffb-109">O arquivo. ico para adicionar ao seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="86ffb-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="86ffb-110">Coloque o nome do arquivo entre aspas ("") se ele contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="86ffb-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86ffb-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="86ffb-111">Remarks</span></span>  
 <span data-ttu-id="86ffb-112">Você pode criar um arquivo. ico com o compilador de recurso do Microsoft Windows (RC).</span><span class="sxs-lookup"><span data-stu-id="86ffb-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="86ffb-113">O compilador de recurso é invocado quando você compila um programa do Visual C++; um arquivo. ico é criado a partir do arquivo. rc.</span><span class="sxs-lookup"><span data-stu-id="86ffb-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="86ffb-114">O `-win32icon` e `-win32resource` são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="86ffb-114">The `-win32icon` and `-win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="86ffb-115">Ver [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) para fazer referência a um arquivo de recurso do .NET Framework, ou [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) para anexar um arquivo de recurso do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="86ffb-115">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a .NET Framework resource file.</span></span> <span data-ttu-id="86ffb-116">Ver [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) para importar um arquivo. res.</span><span class="sxs-lookup"><span data-stu-id="86ffb-116">See [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="86ffb-117">Para definir - win32icon no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="86ffb-117">To set -win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="86ffb-118">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="86ffb-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="86ffb-119">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="86ffb-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="86ffb-120">2.  Clique na guia **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="86ffb-120">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="86ffb-121">3.  Modificar o valor de **ícone** caixa.</span><span class="sxs-lookup"><span data-stu-id="86ffb-121">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="86ffb-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="86ffb-122">Example</span></span>  
 <span data-ttu-id="86ffb-123">O seguinte código compila `In.vb` e anexa um arquivo. ico, `Rf.ico`.</span><span class="sxs-lookup"><span data-stu-id="86ffb-123">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="86ffb-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86ffb-124">See also</span></span>

- [<span data-ttu-id="86ffb-125">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="86ffb-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="86ffb-126">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="86ffb-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
