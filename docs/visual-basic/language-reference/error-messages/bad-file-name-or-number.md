---
title: Nome ou número de arquivo inválido
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 7a16e951030731bdcbb48b5fbb1a0d1881d5e1ec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619388"
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="2b6a2-102">Nome ou número de arquivo inválido</span><span class="sxs-lookup"><span data-stu-id="2b6a2-102">Bad file name or number</span></span>
<span data-ttu-id="2b6a2-103">Ocorreu um erro ao tentar acessar o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="2b6a2-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="2b6a2-104">Entre as causas possíveis desse erro são:</span><span class="sxs-lookup"><span data-stu-id="2b6a2-104">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="2b6a2-105">Uma declaração se refere a um arquivo com um nome de arquivo ou um número que não foi especificado no `FileOpen` instrução ou que foi especificado em um `FileOpen` instrução, mas foi subsequentemente fechado.</span><span class="sxs-lookup"><span data-stu-id="2b6a2-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
- <span data-ttu-id="2b6a2-106">Uma declaração se refere a um arquivo com um número que está fora do intervalo de números de arquivos.</span><span class="sxs-lookup"><span data-stu-id="2b6a2-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
- <span data-ttu-id="2b6a2-107">Uma declaração se refere a um nome de arquivo ou um número que não é válido.</span><span class="sxs-lookup"><span data-stu-id="2b6a2-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2b6a2-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="2b6a2-108">To correct this error</span></span>  
  
1. <span data-ttu-id="2b6a2-109">Verifique se o nome do arquivo é especificado em um `FileOpen` instrução.</span><span class="sxs-lookup"><span data-stu-id="2b6a2-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="2b6a2-110">Observe que, se você chamou o `FileClose` instrução sem argumentos, você talvez tenha fechado todos os arquivos abertos.</span><span class="sxs-lookup"><span data-stu-id="2b6a2-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2. <span data-ttu-id="2b6a2-111">Se seu código está gerando números de arquivo de forma algorítmica, verifique se que os números são válidos.</span><span class="sxs-lookup"><span data-stu-id="2b6a2-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3. <span data-ttu-id="2b6a2-112">Verifique os nomes de arquivo para certificar-se de que eles estão em conformidade com as convenções do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="2b6a2-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b6a2-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b6a2-113">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [<span data-ttu-id="2b6a2-114">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2b6a2-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
