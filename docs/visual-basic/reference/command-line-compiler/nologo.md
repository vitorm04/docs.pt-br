---
title: /nologo (Visual Basic) | Documentos do Microsoft
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
- -nologo compiler option [Visual Basic]
- banners, suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
caps.latest.revision: 16
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
ms.openlocfilehash: fe03c36f46717248269c9aaec13b40569161b0e0
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="nologo-visual-basic"></a><span data-ttu-id="9801d-102">/nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9801d-102">/nologo (Visual Basic)</span></span>
<span data-ttu-id="9801d-103">Suprime a exibição da faixa de direitos autorais e mensagens informativas durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="9801d-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9801d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9801d-104">Syntax</span></span>  
  
```  
/nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="9801d-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="9801d-105">Remarks</span></span>  
 <span data-ttu-id="9801d-106">Se você especificar `/nologo`, o compilador não exibirá uma faixa de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="9801d-106">If you specify `/nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="9801d-107">Por padrão, `/nologo` não está em vigor.</span><span class="sxs-lookup"><span data-stu-id="9801d-107">By default, `/nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9801d-108">O `/nologo` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="9801d-108">The `/nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9801d-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9801d-109">Example</span></span>  
 <span data-ttu-id="9801d-110">O seguinte código compila `T2.vb` e não exibe uma faixa de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="9801d-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```  
vbc /nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9801d-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9801d-111">See Also</span></span>  
 <span data-ttu-id="9801d-112">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="9801d-112">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="9801d-113"> [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="9801d-113"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
