---
title: /verbose | Documentos do Microsoft
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
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
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
ms.openlocfilehash: 62285a727217aa897a83a9e746588c80a2c519c0
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="verbose"></a><span data-ttu-id="83f5f-102">/verbose</span><span class="sxs-lookup"><span data-stu-id="83f5f-102">/verbose</span></span>
<span data-ttu-id="83f5f-103">Faz com que o compilador gerar mensagens de status e de erro detalhadas.</span><span class="sxs-lookup"><span data-stu-id="83f5f-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83f5f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83f5f-104">Syntax</span></span>  
  
```  
/verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="83f5f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="83f5f-105">Arguments</span></span>  
 <span data-ttu-id="83f5f-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="83f5f-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="83f5f-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="83f5f-107">Optional.</span></span> <span data-ttu-id="83f5f-108">Especificando `/verbose` é o mesmo que especificar `/verbose+`, que faz com que o compilador emita mensagens detalhadas.</span><span class="sxs-lookup"><span data-stu-id="83f5f-108">Specifying `/verbose` is the same as specifying `/verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="83f5f-109">O padrão para essa opção é `/verbose-`.</span><span class="sxs-lookup"><span data-stu-id="83f5f-109">The default for this option is `/verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83f5f-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="83f5f-110">Remarks</span></span>  
 <span data-ttu-id="83f5f-111">O `/verbose` opção exibe informações sobre o número total de erros emitido pelo compilador, relata que assemblies estão sendo carregados por um módulo e exibe os arquivos que estão sendo compilados no momento.</span><span class="sxs-lookup"><span data-stu-id="83f5f-111">The `/verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83f5f-112">O `/verbose` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="83f5f-112">The `/verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83f5f-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="83f5f-113">Example</span></span>  
 <span data-ttu-id="83f5f-114">O seguinte código compila `In.vb` e direciona o compilador para exibir informações de status detalhadas.</span><span class="sxs-lookup"><span data-stu-id="83f5f-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```  
vbc /verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="83f5f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83f5f-115">See Also</span></span>  
 <span data-ttu-id="83f5f-116">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="83f5f-116">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="83f5f-117"> [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="83f5f-117"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
