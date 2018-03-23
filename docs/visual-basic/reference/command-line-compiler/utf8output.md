---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 97f90b39046aebe0cd15c7e033d8e588045491f7
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="88e9e-102">-utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88e9e-102">-utf8output (Visual Basic)</span></span>
<span data-ttu-id="88e9e-103">Exibe a saída do compilador usando a codificação UTF-8.</span><span class="sxs-lookup"><span data-stu-id="88e9e-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88e9e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88e9e-104">Syntax</span></span>  
  
```  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="88e9e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="88e9e-105">Arguments</span></span>  
 <span data-ttu-id="88e9e-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="88e9e-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="88e9e-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="88e9e-107">Optional.</span></span> <span data-ttu-id="88e9e-108">O padrão para essa opção é `-utf8output-`, que significa a saída do compilador não usa a codificação UTF-8.</span><span class="sxs-lookup"><span data-stu-id="88e9e-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="88e9e-109">Especificando `-utf8output` é o mesmo que especificar `-utf8output+`.</span><span class="sxs-lookup"><span data-stu-id="88e9e-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88e9e-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="88e9e-110">Remarks</span></span>  
 <span data-ttu-id="88e9e-111">Em algumas configurações internacionais, saída do compilador não pode ser exibida corretamente no console do.</span><span class="sxs-lookup"><span data-stu-id="88e9e-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="88e9e-112">Em tais situações, use `-utf8output` e redirecionar a saída do compilador para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="88e9e-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88e9e-113">O `-utf8output` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="88e9e-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88e9e-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="88e9e-114">Example</span></span>  
 <span data-ttu-id="88e9e-115">O código a seguir compila `In.vb` e direciona o compilador para exibir saída usando a codificação UTF-8.</span><span class="sxs-lookup"><span data-stu-id="88e9e-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="88e9e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88e9e-116">See Also</span></span>  
 [<span data-ttu-id="88e9e-117">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="88e9e-117">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="88e9e-118">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="88e9e-118">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
