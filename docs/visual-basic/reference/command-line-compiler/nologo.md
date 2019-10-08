---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: bb64a468f67745b80b47b42c4fac18852279035d
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005427"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="513a3-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="513a3-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="513a3-103">Suprime a exibição da faixa de direitos autorais e as mensagens informativas durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="513a3-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="513a3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="513a3-104">Syntax</span></span>  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="513a3-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="513a3-105">Remarks</span></span>  
 <span data-ttu-id="513a3-106">Se você especificar `-nologo`, o compilador não exibirá uma faixa de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="513a3-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="513a3-107">Por padrão, `-nologo` não está em vigor.</span><span class="sxs-lookup"><span data-stu-id="513a3-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="513a3-108">A opção `-nologo` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="513a3-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="513a3-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="513a3-109">Example</span></span>  
 <span data-ttu-id="513a3-110">O código a seguir compila `T2.vb` e não exibe uma faixa de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="513a3-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="513a3-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="513a3-111">See also</span></span>

- [<span data-ttu-id="513a3-112">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="513a3-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="513a3-113">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="513a3-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
