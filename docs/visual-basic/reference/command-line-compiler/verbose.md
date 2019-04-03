---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: f6d896fb0d41a8fa3ed613d29bc3fca2bd14cc5e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832783"
---
# <a name="-verbose"></a><span data-ttu-id="d1fbe-102">-verbose</span><span class="sxs-lookup"><span data-stu-id="d1fbe-102">-verbose</span></span>
<span data-ttu-id="d1fbe-103">Faz com que o compilador a produzir mensagens de status e de erro detalhadas.</span><span class="sxs-lookup"><span data-stu-id="d1fbe-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1fbe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1fbe-104">Syntax</span></span>  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d1fbe-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d1fbe-105">Arguments</span></span>  
 <span data-ttu-id="d1fbe-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="d1fbe-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="d1fbe-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d1fbe-107">Optional.</span></span> <span data-ttu-id="d1fbe-108">Especificando `-verbose` é o mesmo que especificar `-verbose+`, que faz com que o compilador emita mensagens detalhadas.</span><span class="sxs-lookup"><span data-stu-id="d1fbe-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="d1fbe-109">O padrão para essa opção é `-verbose-`.</span><span class="sxs-lookup"><span data-stu-id="d1fbe-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1fbe-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="d1fbe-110">Remarks</span></span>  
 <span data-ttu-id="d1fbe-111">O `-verbose` opção exibe informações sobre o número total de erros emitida pelo compilador, informa quais assemblies são carregados por um módulo e exibe quais arquivos estão sendo compilados no momento.</span><span class="sxs-lookup"><span data-stu-id="d1fbe-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1fbe-112">O `-verbose` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="d1fbe-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1fbe-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d1fbe-113">Example</span></span>  
 <span data-ttu-id="d1fbe-114">O seguinte código compila `In.vb` e direciona o compilador para exibir informações de status detalhado.</span><span class="sxs-lookup"><span data-stu-id="d1fbe-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1fbe-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1fbe-115">See also</span></span>

- [<span data-ttu-id="d1fbe-116">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d1fbe-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d1fbe-117">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="d1fbe-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
