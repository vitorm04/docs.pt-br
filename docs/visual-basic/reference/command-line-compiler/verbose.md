---
title: /verbose
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5480f828fa1f0b6d71fa649bf44513ce806bb440
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="verbose"></a><span data-ttu-id="eb02c-102">/verbose</span><span class="sxs-lookup"><span data-stu-id="eb02c-102">/verbose</span></span>
<span data-ttu-id="eb02c-103">Faz com que o compilador gerar mensagens de status e de erro detalhadas.</span><span class="sxs-lookup"><span data-stu-id="eb02c-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb02c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb02c-104">Syntax</span></span>  
  
```  
/verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="eb02c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="eb02c-105">Arguments</span></span>  
 <span data-ttu-id="eb02c-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="eb02c-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="eb02c-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="eb02c-107">Optional.</span></span> <span data-ttu-id="eb02c-108">Especificando `/verbose` é o mesmo que especificar `/verbose+`, que faz com que o compilador emitir mensagens detalhadas.</span><span class="sxs-lookup"><span data-stu-id="eb02c-108">Specifying `/verbose` is the same as specifying `/verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="eb02c-109">O padrão para essa opção é `/verbose-`.</span><span class="sxs-lookup"><span data-stu-id="eb02c-109">The default for this option is `/verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb02c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb02c-110">Remarks</span></span>  
 <span data-ttu-id="eb02c-111">O `/verbose` opção exibe informações sobre o número total de erros emitido pelo compilador informa quais assemblies estão sendo carregados por um módulo e exibe os arquivos que são compilados no momento.</span><span class="sxs-lookup"><span data-stu-id="eb02c-111">The `/verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb02c-112">O `/verbose` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="eb02c-112">The `/verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb02c-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eb02c-113">Example</span></span>  
 <span data-ttu-id="eb02c-114">O código a seguir compila `In.vb` e direciona o compilador para exibir informações de status detalhado.</span><span class="sxs-lookup"><span data-stu-id="eb02c-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```  
vbc /verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb02c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb02c-115">See Also</span></span>  
 [<span data-ttu-id="eb02c-116">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb02c-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="eb02c-117">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="eb02c-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
