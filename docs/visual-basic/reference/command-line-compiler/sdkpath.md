---
title: /sdkpath | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- sdkpath
- /sdkpath
dev_langs:
- VB
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
caps.latest.revision: 15
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
ms.openlocfilehash: 2e32bb403347063edcf0d47fd4a7511a0da1f340
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="sdkpath"></a><span data-ttu-id="6c96b-102">/sdkpath</span><span class="sxs-lookup"><span data-stu-id="6c96b-102">/sdkpath</span></span>
<span data-ttu-id="6c96b-103">Especifica o local de mscorlib. dll e Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="6c96b-103">Specifies the location of Mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c96b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c96b-104">Syntax</span></span>  
  
```  
/sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="6c96b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6c96b-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="6c96b-106">O diretório que contém as versões de mscorlib. dll e Microsoft.VisualBasic.dll para usar para a compilação.</span><span class="sxs-lookup"><span data-stu-id="6c96b-106">The directory containing the versions of Mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="6c96b-107">Esse caminho não é verificado até que ele seja carregado.</span><span class="sxs-lookup"><span data-stu-id="6c96b-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="6c96b-108">Coloque o nome do diretório entre aspas ("") se ele contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="6c96b-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c96b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c96b-109">Remarks</span></span>  
 <span data-ttu-id="6c96b-110">Essa opção informa o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador para carregar os arquivos de mscorlib. dll e Microsoft.VisualBasic.dll de um local não padrão.</span><span class="sxs-lookup"><span data-stu-id="6c96b-110">This option tells the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler to load the Mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="6c96b-111">O `/sdkpath` opção foi projetada para ser usado com [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span><span class="sxs-lookup"><span data-stu-id="6c96b-111">The `/sdkpath` option was designed to be used with [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="6c96b-112">O [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] usa versões diferentes desses oferece suporte a bibliotecas para evitar o uso de tipos e recursos de linguagem não encontrados nos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="6c96b-112">The [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c96b-113">O `/sdkpath` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="6c96b-113">The `/sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="6c96b-114">O `/sdkpath` opção é definida quando um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] dispositivo projeto é carregado.</span><span class="sxs-lookup"><span data-stu-id="6c96b-114">The `/sdkpath` option is set when a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] device project is loaded.</span></span>  
  
 <span data-ttu-id="6c96b-115">Você pode especificar que o compilador deve compilar sem uma referência à biblioteca de tempo de execução do Visual Basic usando o `/vbruntime` opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="6c96b-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `/vbruntime` compiler option.</span></span> <span data-ttu-id="6c96b-116">Para obter mais informações, consulte [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span><span class="sxs-lookup"><span data-stu-id="6c96b-116">For more information, see [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c96b-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6c96b-117">Example</span></span>  
 <span data-ttu-id="6c96b-118">O seguinte código compila `Myfile.vb` com o [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)], usar as versões de mscorlib. dll e Microsoft.VisualBasic.dll encontrado no diretório de instalação padrão do [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] na unidade C.</span><span class="sxs-lookup"><span data-stu-id="6c96b-118">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] on the C drive.</span></span> <span data-ttu-id="6c96b-119">Normalmente, você poderia usar a versão mais recente do [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c96b-119">Typically, you would use the most recent version of the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].</span></span>  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c96b-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c96b-120">See Also</span></span>  
 <span data-ttu-id="6c96b-121">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="6c96b-121">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="6c96b-122"> [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="6c96b-122"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="6c96b-123"> [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md) </span><span class="sxs-lookup"><span data-stu-id="6c96b-123"> [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md) </span></span>  
<span data-ttu-id="6c96b-124"> [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)</span><span class="sxs-lookup"><span data-stu-id="6c96b-124"> [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)</span></span>
