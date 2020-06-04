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
ms.openlocfilehash: bcbc690690993a094bc5360d0c13bddebf8cd615
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414240"
---
# <a name="-win32resource"></a><span data-ttu-id="553c3-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="553c3-102">-win32resource</span></span>
<span data-ttu-id="553c3-103">Insere um arquivo de recurso do Win32 no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="553c3-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="553c3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="553c3-104">Syntax</span></span>  
  
```console  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="553c3-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="553c3-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="553c3-106">O nome do arquivo de recurso a ser adicionado ao arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="553c3-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="553c3-107">Coloque o nome de arquivo entre aspas ("") se ele contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="553c3-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="553c3-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="553c3-108">Remarks</span></span>  
 <span data-ttu-id="553c3-109">Você pode criar um arquivo de recurso do Win32 com o compilador de recursos do Microsoft Windows (RC).</span><span class="sxs-lookup"><span data-stu-id="553c3-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="553c3-110">Um recurso do Win32 pode conter informações de versão ou bitmap (ícone) que ajudam a identificar seu aplicativo no **Explorador de arquivos**.</span><span class="sxs-lookup"><span data-stu-id="553c3-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="553c3-111">Se você não especificar `-win32resource` , o compilador gerará informações de versão com base na versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="553c3-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="553c3-112">As opções `-win32resource` e `-win32icon` são mutualmente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="553c3-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="553c3-113">Consulte [-linkresource (Visual Basic)](linkresource.md) para fazer referência a um arquivo de recurso .NET Framework ou [-Resource (Visual Basic)](resource.md) para anexar um arquivo de recurso de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="553c3-113">See [-linkresource (Visual Basic)](linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](resource.md) to attach a .NET Framework resource file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="553c3-114">A `-win32resource` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ela está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="553c3-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="553c3-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="553c3-115">Example</span></span>  
 <span data-ttu-id="553c3-116">O código a seguir compila `In.vb` e anexa um arquivo de recurso do Win32, `Rf.res` :</span><span class="sxs-lookup"><span data-stu-id="553c3-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="553c3-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="553c3-117">See also</span></span>

- [<span data-ttu-id="553c3-118">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="553c3-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="553c3-119">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="553c3-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
