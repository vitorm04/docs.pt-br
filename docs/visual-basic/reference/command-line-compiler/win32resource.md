---
title: -win32resource
ms.date: 03/13/2018
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
ms.openlocfilehash: 4ecac4ffe665d724d625aaeb7cc1e008eb13ca54
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50186077"
---
# <a name="-win32resource"></a><span data-ttu-id="d272a-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="d272a-102">-win32resource</span></span>
<span data-ttu-id="d272a-103">Insere um arquivo de recurso Win32 no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="d272a-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d272a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d272a-104">Syntax</span></span>  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="d272a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d272a-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="d272a-106">O nome do arquivo de recurso para adicionar ao seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="d272a-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="d272a-107">Coloque o nome do arquivo entre aspas ("") se ele contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="d272a-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d272a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="d272a-108">Remarks</span></span>  
 <span data-ttu-id="d272a-109">Você pode criar um arquivo de recurso do Win32 com o compilador de recurso do Microsoft Windows (RC).</span><span class="sxs-lookup"><span data-stu-id="d272a-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="d272a-110">Um recurso do Win32 pode conter a versão ou informações de bitmap (ícone) que ajudam a identificar seu aplicativo no **Explorador de arquivos**.</span><span class="sxs-lookup"><span data-stu-id="d272a-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="d272a-111">Se você não especificar `-win32resource`, o compilador gera informações de versão com base na versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="d272a-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="d272a-112">O `-win32resource` e `-win32icon` são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="d272a-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="d272a-113">Ver [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) a referência de uma [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arquivo de recurso, ou [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) anexar um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="d272a-113">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d272a-114">O `-win32resource` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="d272a-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d272a-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d272a-115">Example</span></span>  
 <span data-ttu-id="d272a-116">O seguinte código compila `In.vb` e anexa um arquivo de recurso do Win32, `Rf.res`:</span><span class="sxs-lookup"><span data-stu-id="d272a-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d272a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d272a-117">See Also</span></span>  
 [<span data-ttu-id="d272a-118">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d272a-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="d272a-119">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="d272a-119">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
