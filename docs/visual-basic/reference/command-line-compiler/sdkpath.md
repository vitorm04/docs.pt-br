---
title: -sdkpath
ms.date: 07/20/2015
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 162c7d58350c381ec667e8a4cd11c03e83fcdf44
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925679"
---
# <a name="-sdkpath"></a><span data-ttu-id="baee5-102">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="baee5-102">-sdkpath</span></span>
<span data-ttu-id="baee5-103">Especifica o local de mscorlib. dll e VisualBasic.</span><span class="sxs-lookup"><span data-stu-id="baee5-103">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baee5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="baee5-104">Syntax</span></span>  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="baee5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="baee5-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="baee5-106">O diretório que contém as versões de mscorlib. dll e VisualBasic a ser usado para compilação.</span><span class="sxs-lookup"><span data-stu-id="baee5-106">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="baee5-107">Esse caminho não é verificado até que ele seja carregado.</span><span class="sxs-lookup"><span data-stu-id="baee5-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="baee5-108">Coloque o nome do diretório entre aspas ("") se ele contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="baee5-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="baee5-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="baee5-109">Remarks</span></span>  
 <span data-ttu-id="baee5-110">Essa opção informa ao compilador do Visual Basic para carregar o mscorlib. dll e VisualBasic arquivos de um local não padrão.</span><span class="sxs-lookup"><span data-stu-id="baee5-110">This option tells the Visual Basic compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="baee5-111">O `-sdkpath` opção foi projetada para ser usado com [- netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span><span class="sxs-lookup"><span data-stu-id="baee5-111">The `-sdkpath` option was designed to be used with [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="baee5-112">O [!INCLUDE[Compact](~/includes/compact-md.md)] usa diferentes versões deles oferece suporte a bibliotecas para evitar o uso de tipos e recursos de linguagem não encontrados nos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="baee5-112">The [!INCLUDE[Compact](~/includes/compact-md.md)] uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="baee5-113">O `-sdkpath` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="baee5-113">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="baee5-114">O `-sdkpath` opção é definida quando um projeto de dispositivo do Visual Basic é carregado.</span><span class="sxs-lookup"><span data-stu-id="baee5-114">The `-sdkpath` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="baee5-115">Você pode especificar que o compilador deve compilar sem uma referência à biblioteca de tempo de execução do Visual Basic usando o `-vbruntime` opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="baee5-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="baee5-116">Para obter mais informações, consulte [- vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span><span class="sxs-lookup"><span data-stu-id="baee5-116">For more information, see [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="baee5-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="baee5-117">Example</span></span>  
 <span data-ttu-id="baee5-118">O seguinte código compila `Myfile.vb` com o [!INCLUDE[Compact](~/includes/compact-md.md)], usando as versões de mscorlib. dll e VisualBasic encontrado no diretório de instalação padrão do [!INCLUDE[Compact](~/includes/compact-md.md)] na unidade C.</span><span class="sxs-lookup"><span data-stu-id="baee5-118">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="baee5-119">Normalmente, você poderia usar a versão mais recente do [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="baee5-119">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="baee5-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="baee5-120">See Also</span></span>  
 [<span data-ttu-id="baee5-121">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="baee5-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="baee5-122">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="baee5-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="baee5-123">-netcf</span><span class="sxs-lookup"><span data-stu-id="baee5-123">-netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [<span data-ttu-id="baee5-124">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="baee5-124">-vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
