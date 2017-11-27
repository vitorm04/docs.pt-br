---
title: /sdkpath
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- sdkpath
- /sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 876922385124db3e8db12c93c75194da83d2526c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="sdkpath"></a><span data-ttu-id="f3627-102">/sdkpath</span><span class="sxs-lookup"><span data-stu-id="f3627-102">/sdkpath</span></span>
<span data-ttu-id="f3627-103">Especifica o local de mscorlib. dll e Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="f3627-103">Specifies the location of Mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3627-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3627-104">Syntax</span></span>  
  
```  
/sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="f3627-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f3627-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="f3627-106">O diretório que contém as versões de mscorlib. dll e Microsoft.VisualBasic.dll para usar para a compilação.</span><span class="sxs-lookup"><span data-stu-id="f3627-106">The directory containing the versions of Mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="f3627-107">Esse caminho não é verificado até que ele seja carregado.</span><span class="sxs-lookup"><span data-stu-id="f3627-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="f3627-108">Coloque o nome do diretório entre aspas ("") se ele contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="f3627-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3627-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f3627-109">Remarks</span></span>  
 <span data-ttu-id="f3627-110">Essa opção informa o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador para carregar os arquivos de mscorlib. dll e Microsoft.VisualBasic.dll de um local diferente do padrão.</span><span class="sxs-lookup"><span data-stu-id="f3627-110">This option tells the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler to load the Mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="f3627-111">O `/sdkpath` opção foi projetada para ser usado com [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span><span class="sxs-lookup"><span data-stu-id="f3627-111">The `/sdkpath` option was designed to be used with [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="f3627-112">O [!INCLUDE[Compact](~/includes/compact-md.md)] usa diferentes versões desses oferece suporte a bibliotecas para evitar o uso de tipos e recursos de idioma não encontrados nos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="f3627-112">The [!INCLUDE[Compact](~/includes/compact-md.md)] uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3627-113">O `/sdkpath` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="f3627-113">The `/sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="f3627-114">O `/sdkpath` opção é definida quando um [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dispositivo projeto é carregado.</span><span class="sxs-lookup"><span data-stu-id="f3627-114">The `/sdkpath` option is set when a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] device project is loaded.</span></span>  
  
 <span data-ttu-id="f3627-115">Você pode especificar que o compilador deve compilar sem uma referência à biblioteca de tempo de execução do Visual Basic, usando o `/vbruntime` opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="f3627-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `/vbruntime` compiler option.</span></span> <span data-ttu-id="f3627-116">Para obter mais informações, consulte [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span><span class="sxs-lookup"><span data-stu-id="f3627-116">For more information, see [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3627-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f3627-117">Example</span></span>  
 <span data-ttu-id="f3627-118">O código a seguir compila `Myfile.vb` com o [!INCLUDE[Compact](~/includes/compact-md.md)], usando as versões de mscorlib. dll e Microsoft.VisualBasic.dll encontrado no diretório de instalação padrão do [!INCLUDE[Compact](~/includes/compact-md.md)] na unidade C.</span><span class="sxs-lookup"><span data-stu-id="f3627-118">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="f3627-119">Normalmente, você poderia usar a versão mais recente do [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f3627-119">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3627-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3627-120">See Also</span></span>  
 [<span data-ttu-id="f3627-121">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f3627-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="f3627-122">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="f3627-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="f3627-123">/netcf</span><span class="sxs-lookup"><span data-stu-id="f3627-123">/netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [<span data-ttu-id="f3627-124">/vbruntime</span><span class="sxs-lookup"><span data-stu-id="f3627-124">/vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
