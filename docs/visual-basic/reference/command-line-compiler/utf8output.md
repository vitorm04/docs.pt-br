---
title: /utf8output (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
caps.latest.revision: 11
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
ms.openlocfilehash: 45361fb1dca34f2cdc849184d0e316b27d9545b6
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="utf8output-visual-basic"></a><span data-ttu-id="ff481-102">/utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff481-102">/utf8output (Visual Basic)</span></span>
<span data-ttu-id="ff481-103">Exibe a saída do compilador usando a codificação UTF-8.</span><span class="sxs-lookup"><span data-stu-id="ff481-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff481-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ff481-104">Syntax</span></span>  
  
```  
/utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ff481-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ff481-105">Arguments</span></span>  
 <span data-ttu-id="ff481-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="ff481-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="ff481-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ff481-107">Optional.</span></span> <span data-ttu-id="ff481-108">O padrão para essa opção é `/utf8output-`, que significa saída do compilador não usa a codificação UTF-8.</span><span class="sxs-lookup"><span data-stu-id="ff481-108">The default for this option is `/utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="ff481-109">Especificando `/utf8output` é o mesmo que especificar `/utf8output+`.</span><span class="sxs-lookup"><span data-stu-id="ff481-109">Specifying `/utf8output` is the same as specifying `/utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff481-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="ff481-110">Remarks</span></span>  
 <span data-ttu-id="ff481-111">Em algumas configurações internacionais, saída do compilador não pode ser exibida corretamente no console.</span><span class="sxs-lookup"><span data-stu-id="ff481-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="ff481-112">Em tais situações, use `/utf8output` e redirecionar a saída do compilador para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="ff481-112">In such situations, use `/utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff481-113">O `/utf8output` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ff481-113">The `/utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff481-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ff481-114">Example</span></span>  
 <span data-ttu-id="ff481-115">O seguinte código compila `In.vb` e direciona o compilador para exibir saída usando a codificação UTF-8.</span><span class="sxs-lookup"><span data-stu-id="ff481-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```  
vbc /utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff481-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff481-116">See Also</span></span>  
 <span data-ttu-id="ff481-117">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="ff481-117">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="ff481-118"> [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="ff481-118"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
