---
title: -win32resource
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e210d88d32ac7341ab881ca6ff0e44961469a31
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-win32resource"></a><span data-ttu-id="317f6-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="317f6-102">-win32resource</span></span>
<span data-ttu-id="317f6-103">Insere um arquivo de recurso Win32 no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="317f6-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="317f6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="317f6-104">Syntax</span></span>  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="317f6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="317f6-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="317f6-106">O nome do arquivo de recurso para adicionar ao seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="317f6-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="317f6-107">Coloque o nome do arquivo entre aspas ("") se ele contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="317f6-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="317f6-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="317f6-108">Remarks</span></span>  
 <span data-ttu-id="317f6-109">Você pode criar um arquivo de recurso Win32 com o compilador de recurso do Microsoft Windows (RC).</span><span class="sxs-lookup"><span data-stu-id="317f6-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="317f6-110">Um recurso do Win32 pode conter a versão ou informações de bitmap (ícone) que ajudam a identificar seu aplicativo em **Explorador de arquivos**.</span><span class="sxs-lookup"><span data-stu-id="317f6-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="317f6-111">Se você não especificar `-win32resource`, o compilador gera informações de versão com base na versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="317f6-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="317f6-112">O `-win32resource` e `-win32icon` são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="317f6-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="317f6-113">Consulte [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) a referência de um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arquivo de recurso, ou [-recurso (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) para anexar um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="317f6-113">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="317f6-114">O `-win32resource` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="317f6-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="317f6-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="317f6-115">Example</span></span>  
 <span data-ttu-id="317f6-116">O código a seguir compila `In.vb` e anexa um arquivo de recurso Win32, `Rf.res`:</span><span class="sxs-lookup"><span data-stu-id="317f6-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="317f6-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="317f6-117">See Also</span></span>  
 [<span data-ttu-id="317f6-118">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="317f6-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="317f6-119">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="317f6-119">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
