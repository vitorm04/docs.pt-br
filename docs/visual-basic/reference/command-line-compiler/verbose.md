---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 8c5bc1d2ce331b8fe9461f91d64fbeab5a070b59
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004978"
---
# <a name="-verbose"></a><span data-ttu-id="c9f6a-102">-verbose</span><span class="sxs-lookup"><span data-stu-id="c9f6a-102">-verbose</span></span>
<span data-ttu-id="c9f6a-103">Faz com que o compilador produza mensagens de erro e status detalhados.</span><span class="sxs-lookup"><span data-stu-id="c9f6a-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9f6a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9f6a-104">Syntax</span></span>  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c9f6a-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="c9f6a-105">Arguments</span></span>  
 <span data-ttu-id="c9f6a-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="c9f6a-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="c9f6a-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="c9f6a-107">Optional.</span></span> <span data-ttu-id="c9f6a-108">Especificar `-verbose` é o mesmo que especificar `-verbose+`, o que faz com que o compilador emita mensagens detalhadas.</span><span class="sxs-lookup"><span data-stu-id="c9f6a-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="c9f6a-109">O padrão para essa opção é `-verbose-`.</span><span class="sxs-lookup"><span data-stu-id="c9f6a-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9f6a-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9f6a-110">Remarks</span></span>  
 <span data-ttu-id="c9f6a-111">A opção `-verbose` exibe informações sobre o número total de erros emitidos pelo compilador, relata quais assemblies estão sendo carregados por um módulo e exibe quais arquivos estão sendo compilados no momento.</span><span class="sxs-lookup"><span data-stu-id="c9f6a-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9f6a-112">A opção `-verbose` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="c9f6a-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9f6a-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9f6a-113">Example</span></span>  
 <span data-ttu-id="c9f6a-114">O código a seguir compila `In.vb` e direciona o compilador para exibir informações detalhadas de status.</span><span class="sxs-lookup"><span data-stu-id="c9f6a-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9f6a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9f6a-115">See also</span></span>

- [<span data-ttu-id="c9f6a-116">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c9f6a-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="c9f6a-117">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9f6a-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
