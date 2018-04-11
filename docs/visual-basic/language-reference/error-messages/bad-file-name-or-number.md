---
title: Nome ou número de arquivo inválido
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3d7c8bae3df0e75a1c4f9afacdff681a553503d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="7425a-102">Nome ou número de arquivo inválido</span><span class="sxs-lookup"><span data-stu-id="7425a-102">Bad file name or number</span></span>
<span data-ttu-id="7425a-103">Ocorreu um erro ao tentar acessar o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="7425a-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="7425a-104">Entre as causas possíveis desse erro são:</span><span class="sxs-lookup"><span data-stu-id="7425a-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="7425a-105">Uma declaração se refere a um arquivo com um nome de arquivo ou um número que não foi especificado no `FileOpen` instrução ou que foi especificado em um `FileOpen` instrução, mas foi subsequentemente fechado.</span><span class="sxs-lookup"><span data-stu-id="7425a-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
-   <span data-ttu-id="7425a-106">Uma instrução refere-se a um arquivo com um número que está fora do intervalo de números de arquivos.</span><span class="sxs-lookup"><span data-stu-id="7425a-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
-   <span data-ttu-id="7425a-107">Uma instrução faz referência a um nome de arquivo ou um número que não é válido.</span><span class="sxs-lookup"><span data-stu-id="7425a-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7425a-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7425a-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="7425a-109">Verifique se o nome do arquivo especificado em um `FileOpen` instrução.</span><span class="sxs-lookup"><span data-stu-id="7425a-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="7425a-110">Observe que, se você chamou o `FileClose` instrução sem argumentos, você talvez tenha fechado todos os arquivos abertos.</span><span class="sxs-lookup"><span data-stu-id="7425a-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2.  <span data-ttu-id="7425a-111">Se seu código está gerando números de arquivos de maneira algorítmica, verifique se que os números são válidos.</span><span class="sxs-lookup"><span data-stu-id="7425a-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3.  <span data-ttu-id="7425a-112">Verifique os nomes de arquivo para garantir que estejam em conformidade com as convenções do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="7425a-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7425a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7425a-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>  
 [<span data-ttu-id="7425a-114">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7425a-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
