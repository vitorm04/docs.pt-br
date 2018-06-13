---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 011c9499eaa728588e6181e33a96dd75b4a7b84b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648535"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="75c89-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75c89-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="75c89-103">Suprime a exibição da faixa de direitos autorais e mensagens informativas durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="75c89-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75c89-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="75c89-104">Syntax</span></span>  
  
```  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="75c89-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="75c89-105">Remarks</span></span>  
 <span data-ttu-id="75c89-106">Se você especificar `-nologo`, o compilador não exibirá uma faixa de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="75c89-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="75c89-107">Por padrão, `-nologo` não está em vigor.</span><span class="sxs-lookup"><span data-stu-id="75c89-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75c89-108">O `-nologo` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="75c89-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75c89-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="75c89-109">Example</span></span>  
 <span data-ttu-id="75c89-110">O código a seguir compila `T2.vb` e não exibe uma faixa de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="75c89-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="75c89-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75c89-111">See Also</span></span>  
 [<span data-ttu-id="75c89-112">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="75c89-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="75c89-113">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="75c89-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
