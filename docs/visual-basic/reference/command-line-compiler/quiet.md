---
title: /quiet | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /quiet
- quiet
dev_langs:
- VB
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
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
ms.openlocfilehash: bc21be8982fea52bf25d0bedeec2b78eee1e705f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="quiet"></a><span data-ttu-id="3792a-102">/quiet</span><span class="sxs-lookup"><span data-stu-id="3792a-102">/quiet</span></span>
<span data-ttu-id="3792a-103">Impede que o compilador de mostrar código para erros relacionados à sintaxe e avisos.</span><span class="sxs-lookup"><span data-stu-id="3792a-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3792a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3792a-104">Syntax</span></span>  
  
```  
/quiet  
```  
  
## <a name="remarks"></a><span data-ttu-id="3792a-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="3792a-105">Remarks</span></span>  
 <span data-ttu-id="3792a-106">Por padrão, `/quiet` não está em vigor.</span><span class="sxs-lookup"><span data-stu-id="3792a-106">By default, `/quiet` is not in effect.</span></span> <span data-ttu-id="3792a-107">Quando o compilador reporta um erro de sintaxe ou aviso, ele também produz a linha do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="3792a-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="3792a-108">Para aplicações que analisam a saída do compilador, pode ser mais conveniente para o compilador apenas o texto do diagnóstico de saída.</span><span class="sxs-lookup"><span data-stu-id="3792a-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>  
  
 <span data-ttu-id="3792a-109">No exemplo a seguir, `Module1` gera um erro que inclui código-fonte quando compilado sem `/quiet`.</span><span class="sxs-lookup"><span data-stu-id="3792a-109">In the following example, `Module1` outputs an error that includes source code when compiled without `/quiet`.</span></span>  
  
```  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="3792a-110">Saída:</span><span class="sxs-lookup"><span data-stu-id="3792a-110">Output:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
 `x`  
  
 `~`  
  
 <span data-ttu-id="3792a-111">Compilado com `/quiet`, o compilador gera o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3792a-111">Compiled with `/quiet`, the compiler outputs only the following:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  <span data-ttu-id="3792a-112">O `/quiet` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="3792a-112">The `/quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3792a-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3792a-113">Example</span></span>  
 <span data-ttu-id="3792a-114">O seguinte código compila `T2.vb` e não mostra código para diagnósticos de compilador relacionados com a sintaxe:</span><span class="sxs-lookup"><span data-stu-id="3792a-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>  
  
```  
vbc /quiet t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3792a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3792a-115">See Also</span></span>  
 <span data-ttu-id="3792a-116">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="3792a-116">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="3792a-117"> [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="3792a-117"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
