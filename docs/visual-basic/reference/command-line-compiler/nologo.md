---
title: /nologo (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c2c7e7a111a3763d7463f67c2d984955da33bbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="nologo-visual-basic"></a><span data-ttu-id="135c5-102">/nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="135c5-102">/nologo (Visual Basic)</span></span>
<span data-ttu-id="135c5-103">Suprime a exibição da faixa de direitos autorais e mensagens informativas durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="135c5-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="135c5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="135c5-104">Syntax</span></span>  
  
```  
/nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="135c5-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="135c5-105">Remarks</span></span>  
 <span data-ttu-id="135c5-106">Se você especificar `/nologo`, o compilador não exibirá uma faixa de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="135c5-106">If you specify `/nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="135c5-107">Por padrão, `/nologo` não está em vigor.</span><span class="sxs-lookup"><span data-stu-id="135c5-107">By default, `/nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="135c5-108">O `/nologo` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="135c5-108">The `/nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="135c5-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="135c5-109">Example</span></span>  
 <span data-ttu-id="135c5-110">O código a seguir compila `T2.vb` e não exibe uma faixa de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="135c5-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```  
vbc /nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="135c5-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="135c5-111">See Also</span></span>  
 [<span data-ttu-id="135c5-112">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="135c5-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="135c5-113">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="135c5-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
