---
title: -utf8output
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 5cdc60888cd872940afc1b03febd879bb6d87c2e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350832"
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="a2da0-102">-utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2da0-102">-utf8output (Visual Basic)</span></span>
<span data-ttu-id="a2da0-103">Exibe a saída do compilador usando a codificação UTF-8.</span><span class="sxs-lookup"><span data-stu-id="a2da0-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2da0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a2da0-104">Syntax</span></span>  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a2da0-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="a2da0-105">Arguments</span></span>  
 <span data-ttu-id="a2da0-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="a2da0-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="a2da0-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a2da0-107">Optional.</span></span> <span data-ttu-id="a2da0-108">O padrão para essa opção é `-utf8output-`, o que significa que a saída do compilador não usa a codificação UTF-8.</span><span class="sxs-lookup"><span data-stu-id="a2da0-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="a2da0-109">Especificar `-utf8output` é o mesmo que especificar `-utf8output+`.</span><span class="sxs-lookup"><span data-stu-id="a2da0-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2da0-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a2da0-110">Remarks</span></span>  
 <span data-ttu-id="a2da0-111">Em algumas configurações internacionais, a saída do compilador não pode ser exibida corretamente no console do.</span><span class="sxs-lookup"><span data-stu-id="a2da0-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="a2da0-112">Nessas situações, use `-utf8output` e redirecione a saída do compilador para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="a2da0-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2da0-113">A opção `-utf8output` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="a2da0-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2da0-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a2da0-114">Example</span></span>  
 <span data-ttu-id="a2da0-115">O código a seguir compila `In.vb` e direciona o compilador para exibir a saída usando a codificação UTF-8.</span><span class="sxs-lookup"><span data-stu-id="a2da0-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a2da0-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2da0-116">See also</span></span>

- [<span data-ttu-id="a2da0-117">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a2da0-117">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="a2da0-118">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="a2da0-118">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
