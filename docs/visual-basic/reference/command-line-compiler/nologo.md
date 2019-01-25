---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 1b9cedc3e45795a66c203d4c86bb071045a1d3f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550468"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="e97cc-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e97cc-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="e97cc-103">Suprime a exibição da faixa de direitos autorais e mensagens informativas durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="e97cc-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e97cc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e97cc-104">Syntax</span></span>  
  
```  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="e97cc-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="e97cc-105">Remarks</span></span>  
 <span data-ttu-id="e97cc-106">Se você especificar `-nologo`, o compilador não exibirá uma faixa de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="e97cc-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="e97cc-107">Por padrão, `-nologo` não está em vigor.</span><span class="sxs-lookup"><span data-stu-id="e97cc-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e97cc-108">O `-nologo` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="e97cc-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e97cc-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e97cc-109">Example</span></span>  
 <span data-ttu-id="e97cc-110">O seguinte código compila `T2.vb` e não exibirá uma faixa de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="e97cc-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e97cc-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e97cc-111">See also</span></span>
- [<span data-ttu-id="e97cc-112">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e97cc-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e97cc-113">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="e97cc-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
