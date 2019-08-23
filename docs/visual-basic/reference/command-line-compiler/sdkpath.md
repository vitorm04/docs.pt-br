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
ms.openlocfilehash: 25368d23c398fb3674d5c2d75d4997f917a1c3d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937348"
---
# <a name="-sdkpath"></a><span data-ttu-id="4658b-102">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="4658b-102">-sdkpath</span></span>
<span data-ttu-id="4658b-103">Especifica o local de mscorlib. dll e Microsoft. VisualBasic. dll.</span><span class="sxs-lookup"><span data-stu-id="4658b-103">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4658b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4658b-104">Syntax</span></span>  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="4658b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4658b-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="4658b-106">O diretório que contém as versões de mscorlib. dll e Microsoft. VisualBasic. dll a serem usadas para compilação.</span><span class="sxs-lookup"><span data-stu-id="4658b-106">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="4658b-107">Esse caminho não é verificado até que seja carregado.</span><span class="sxs-lookup"><span data-stu-id="4658b-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="4658b-108">Coloque o nome do diretório entre aspas ("") se ele contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="4658b-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4658b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="4658b-109">Remarks</span></span>  
 <span data-ttu-id="4658b-110">Essa opção informa o compilador de Visual Basic para carregar os arquivos mscorlib. dll e Microsoft. VisualBasic. dll de um local não padrão.</span><span class="sxs-lookup"><span data-stu-id="4658b-110">This option tells the Visual Basic compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="4658b-111">A `-sdkpath` opção foi projetada para ser usada com [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span><span class="sxs-lookup"><span data-stu-id="4658b-111">The `-sdkpath` option was designed to be used with [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="4658b-112">O .NET Compact Framework usa versões diferentes dessas bibliotecas de suporte para evitar o uso de tipos e recursos de idioma não encontrados nos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="4658b-112">The .NET Compact Framework uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4658b-113">A `-sdkpath` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ela está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="4658b-113">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="4658b-114">A `-sdkpath` opção é definida quando um projeto de dispositivo Visual Basic é carregado.</span><span class="sxs-lookup"><span data-stu-id="4658b-114">The `-sdkpath` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="4658b-115">Você pode especificar que o compilador deve compilar sem uma referência para a biblioteca de tempo de execução Visual Basic `-vbruntime` usando a opção do compilador.</span><span class="sxs-lookup"><span data-stu-id="4658b-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="4658b-116">Para obter mais informações, consulte [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span><span class="sxs-lookup"><span data-stu-id="4658b-116">For more information, see [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4658b-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4658b-117">Example</span></span>  
 <span data-ttu-id="4658b-118">O código a seguir é compilado `Myfile.vb` com o .NET Compact Framework, usando as versões de mscorlib. dll e Microsoft. VisualBasic. dll encontrados no diretório de instalação padrão do .NET Compact Framework na unidade C.</span><span class="sxs-lookup"><span data-stu-id="4658b-118">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="4658b-119">Normalmente, você usaria a versão mais recente do .NET Compact Framework.</span><span class="sxs-lookup"><span data-stu-id="4658b-119">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4658b-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4658b-120">See also</span></span>

- [<span data-ttu-id="4658b-121">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4658b-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="4658b-122">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="4658b-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="4658b-123">-netcf</span><span class="sxs-lookup"><span data-stu-id="4658b-123">-netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [<span data-ttu-id="4658b-124">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="4658b-124">-vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
