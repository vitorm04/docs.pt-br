---
title: /win32resource | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /win32resource
- win32resource
dev_langs:
- VB
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
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
ms.openlocfilehash: dc6bbb5948a5dd505f0fc4d1c8a86650214d657a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="win32resource"></a><span data-ttu-id="bd3ce-102">/win32resource</span><span class="sxs-lookup"><span data-stu-id="bd3ce-102">/win32resource</span></span>
<span data-ttu-id="bd3ce-103">Insere um arquivo de recurso Win32 no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="bd3ce-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd3ce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd3ce-104">Syntax</span></span>  
  
```  
/win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="bd3ce-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="bd3ce-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="bd3ce-106">O nome do arquivo de recurso para adicionar ao seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="bd3ce-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="bd3ce-107">Coloque o nome do arquivo entre aspas ("") se ele contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="bd3ce-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd3ce-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="bd3ce-108">Remarks</span></span>  
 <span data-ttu-id="bd3ce-109">Você pode criar um arquivo de recurso Win32 com o compilador de recursos do Microsoft Windows (RC).</span><span class="sxs-lookup"><span data-stu-id="bd3ce-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="bd3ce-110">Um recurso do Win32 pode conter a versão ou informações de bitmap (ícone) que ajudam a identificar seu aplicativo em **File Explorer**.</span><span class="sxs-lookup"><span data-stu-id="bd3ce-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="bd3ce-111">Se você não especificar `/win32resource`, o compilador gera informações de versão com base na versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="bd3ce-111">If you do not specify `/win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="bd3ce-112">O `/win32resource` e `/win32icon` são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="bd3ce-112">The `/win32resource` and `/win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="bd3ce-113">Consulte [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) a referência de um [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] arquivo de recurso, ou [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) para anexar um [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="bd3ce-113">See [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] resource file, or [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] resource file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd3ce-114">O `/win32resource` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="bd3ce-114">The `/win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd3ce-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bd3ce-115">Example</span></span>  
 <span data-ttu-id="bd3ce-116">O seguinte código compila `In.vb` e anexa um arquivo de recurso Win32, `Rf.res`:</span><span class="sxs-lookup"><span data-stu-id="bd3ce-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```  
vbc /win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd3ce-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd3ce-117">See Also</span></span>  
 <span data-ttu-id="bd3ce-118">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="bd3ce-118">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="bd3ce-119"> [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="bd3ce-119"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
