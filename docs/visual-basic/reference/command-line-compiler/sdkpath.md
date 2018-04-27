---
title: -sdkpath
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
ms.openlocfilehash: 5a25755bcbb8d42124cde531f641a611202ae5a1
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="-sdkpath"></a><span data-ttu-id="fa288-102">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="fa288-102">-sdkpath</span></span>
<span data-ttu-id="fa288-103">Especifica o local de mscorlib. dll e Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="fa288-103">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa288-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fa288-104">Syntax</span></span>  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="fa288-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fa288-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="fa288-106">O diretório que contém as versões de mscorlib. dll e Microsoft.VisualBasic.dll a ser usado para compilação.</span><span class="sxs-lookup"><span data-stu-id="fa288-106">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="fa288-107">Esse caminho não é verificado até que ele seja carregado.</span><span class="sxs-lookup"><span data-stu-id="fa288-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="fa288-108">Coloque o nome do diretório entre aspas ("") se ele contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="fa288-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa288-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="fa288-109">Remarks</span></span>  
 <span data-ttu-id="fa288-110">Essa opção informa ao compilador do Visual Basic para carregar o mscorlib.dll e Microsoft.VisualBasic.dll arquivos de um local diferente do padrão.</span><span class="sxs-lookup"><span data-stu-id="fa288-110">This option tells the Visual Basic compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="fa288-111">O `-sdkpath` opção foi projetada para ser usado com [- netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span><span class="sxs-lookup"><span data-stu-id="fa288-111">The `-sdkpath` option was designed to be used with [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="fa288-112">O [!INCLUDE[Compact](~/includes/compact-md.md)] usa diferentes versões desses oferece suporte a bibliotecas para evitar o uso de tipos e recursos de idioma não encontrados nos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="fa288-112">The [!INCLUDE[Compact](~/includes/compact-md.md)] uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa288-113">O `-sdkpath` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="fa288-113">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="fa288-114">O `-sdkpath` opção é definida quando um projeto de dispositivo do Visual Basic é carregado.</span><span class="sxs-lookup"><span data-stu-id="fa288-114">The `-sdkpath` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="fa288-115">Você pode especificar que o compilador deve compilar sem uma referência à biblioteca de tempo de execução do Visual Basic, usando o `-vbruntime` opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="fa288-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="fa288-116">Para obter mais informações, consulte [- vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span><span class="sxs-lookup"><span data-stu-id="fa288-116">For more information, see [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa288-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fa288-117">Example</span></span>  
 <span data-ttu-id="fa288-118">O código a seguir compila `Myfile.vb` com o [!INCLUDE[Compact](~/includes/compact-md.md)], usando as versões de mscorlib. dll e Microsoft.VisualBasic.dll encontrado no diretório de instalação padrão do [!INCLUDE[Compact](~/includes/compact-md.md)] na unidade C.</span><span class="sxs-lookup"><span data-stu-id="fa288-118">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="fa288-119">Normalmente, você poderia usar a versão mais recente do [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fa288-119">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa288-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa288-120">See Also</span></span>  
 [<span data-ttu-id="fa288-121">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fa288-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="fa288-122">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="fa288-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="fa288-123">-netcf</span><span class="sxs-lookup"><span data-stu-id="fa288-123">-netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [<span data-ttu-id="fa288-124">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="fa288-124">-vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
