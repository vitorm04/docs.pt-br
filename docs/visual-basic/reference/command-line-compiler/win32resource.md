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
ms.openlocfilehash: 382dcc6571aa06ecdfc32bf43080c4b7a36eb1f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961296"
---
# <a name="-win32resource"></a><span data-ttu-id="c5ffa-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="c5ffa-102">-win32resource</span></span>
<span data-ttu-id="c5ffa-103">Insere um arquivo de recurso do Win32 no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="c5ffa-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5ffa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5ffa-104">Syntax</span></span>  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="c5ffa-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c5ffa-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="c5ffa-106">O nome do arquivo de recurso a ser adicionado ao arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="c5ffa-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="c5ffa-107">Coloque o nome de arquivo entre aspas ("") se ele contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="c5ffa-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5ffa-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="c5ffa-108">Remarks</span></span>  
 <span data-ttu-id="c5ffa-109">Você pode criar um arquivo de recurso do Win32 com o compilador de recursos do Microsoft Windows (RC).</span><span class="sxs-lookup"><span data-stu-id="c5ffa-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="c5ffa-110">Um recurso do Win32 pode conter informações de versão ou bitmap (ícone) que ajudam a identificar seu aplicativo no **Explorador de arquivos**.</span><span class="sxs-lookup"><span data-stu-id="c5ffa-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="c5ffa-111">Se você não especificar `-win32resource`, o compilador gerará informações de versão com base na versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="c5ffa-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="c5ffa-112">As `-win32resource` opções `-win32icon` e são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="c5ffa-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="c5ffa-113">Consulte [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) para fazer referência a um arquivo de recurso .NET Framework ou [-Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) para anexar um arquivo de recurso de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c5ffa-113">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a .NET Framework resource file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5ffa-114">A `-win32resource` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ela está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="c5ffa-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5ffa-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c5ffa-115">Example</span></span>  
 <span data-ttu-id="c5ffa-116">O código a seguir compila `In.vb` e anexa um arquivo de recurso do Win32,: `Rf.res`</span><span class="sxs-lookup"><span data-stu-id="c5ffa-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5ffa-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5ffa-117">See also</span></span>

- [<span data-ttu-id="c5ffa-118">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c5ffa-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="c5ffa-119">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="c5ffa-119">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
