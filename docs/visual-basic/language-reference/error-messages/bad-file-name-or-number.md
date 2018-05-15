---
title: Nome ou número de arquivo inválido
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 903be68e71ad590b4b669545afd077175534ef4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="d8593-102">Nome ou número de arquivo inválido</span><span class="sxs-lookup"><span data-stu-id="d8593-102">Bad file name or number</span></span>
<span data-ttu-id="d8593-103">Ocorreu um erro ao tentar acessar o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="d8593-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="d8593-104">Entre as causas possíveis desse erro são:</span><span class="sxs-lookup"><span data-stu-id="d8593-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="d8593-105">Uma declaração se refere a um arquivo com um nome de arquivo ou um número que não foi especificado no `FileOpen` instrução ou que foi especificado em um `FileOpen` instrução, mas foi subsequentemente fechado.</span><span class="sxs-lookup"><span data-stu-id="d8593-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
-   <span data-ttu-id="d8593-106">Uma instrução refere-se a um arquivo com um número que está fora do intervalo de números de arquivos.</span><span class="sxs-lookup"><span data-stu-id="d8593-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
-   <span data-ttu-id="d8593-107">Uma instrução faz referência a um nome de arquivo ou um número que não é válido.</span><span class="sxs-lookup"><span data-stu-id="d8593-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d8593-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d8593-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="d8593-109">Verifique se o nome do arquivo especificado em um `FileOpen` instrução.</span><span class="sxs-lookup"><span data-stu-id="d8593-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="d8593-110">Observe que, se você chamou o `FileClose` instrução sem argumentos, você talvez tenha fechado todos os arquivos abertos.</span><span class="sxs-lookup"><span data-stu-id="d8593-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2.  <span data-ttu-id="d8593-111">Se seu código está gerando números de arquivos de maneira algorítmica, verifique se que os números são válidos.</span><span class="sxs-lookup"><span data-stu-id="d8593-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3.  <span data-ttu-id="d8593-112">Verifique os nomes de arquivo para garantir que estejam em conformidade com as convenções do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="d8593-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8593-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8593-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>  
 [<span data-ttu-id="d8593-114">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d8593-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
