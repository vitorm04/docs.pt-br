---
title: -utf8output
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 0a16cdc535de5ed0619bf080bb4637449b11cfef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403051"
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="75e12-102">-utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75e12-102">-utf8output (Visual Basic)</span></span>
<span data-ttu-id="75e12-103">Exibe a saída do compilador usando a codificação UTF-8.</span><span class="sxs-lookup"><span data-stu-id="75e12-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75e12-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="75e12-104">Syntax</span></span>  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="75e12-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="75e12-105">Arguments</span></span>  
 <span data-ttu-id="75e12-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="75e12-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="75e12-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="75e12-107">Optional.</span></span> <span data-ttu-id="75e12-108">O padrão para essa opção é `-utf8output-` , que significa que a saída do compilador não usa a codificação UTF-8.</span><span class="sxs-lookup"><span data-stu-id="75e12-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="75e12-109">Especificar `-utf8output` é o mesmo que especificar `-utf8output+` .</span><span class="sxs-lookup"><span data-stu-id="75e12-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75e12-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="75e12-110">Remarks</span></span>  
 <span data-ttu-id="75e12-111">Em algumas configurações internacionais, a saída do compilador não pode ser exibida corretamente no console do.</span><span class="sxs-lookup"><span data-stu-id="75e12-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="75e12-112">Nessas situações, use `-utf8output` e redirecione a saída do compilador para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="75e12-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75e12-113">A `-utf8output` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ela está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="75e12-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75e12-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="75e12-114">Example</span></span>  
 <span data-ttu-id="75e12-115">O código a seguir compila `In.vb` e direciona o compilador para exibir a saída usando a codificação UTF-8.</span><span class="sxs-lookup"><span data-stu-id="75e12-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="75e12-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="75e12-116">See also</span></span>

- [<span data-ttu-id="75e12-117">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="75e12-117">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="75e12-118">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="75e12-118">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
