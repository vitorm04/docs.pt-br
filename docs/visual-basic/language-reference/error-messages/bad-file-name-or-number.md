---
title: Nome ou número de arquivo inválido
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: d57a9e78e6ae179d3050e5a92399ca731fa16ba7
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874896"
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="b269f-102">Nome ou número de arquivo inválido</span><span class="sxs-lookup"><span data-stu-id="b269f-102">Bad file name or number</span></span>

<span data-ttu-id="b269f-103">Ocorreu um erro ao tentar acessar o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="b269f-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="b269f-104">Entre as possíveis causas desse erro estão:</span><span class="sxs-lookup"><span data-stu-id="b269f-104">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="b269f-105">Uma instrução refere-se a um arquivo com um nome de arquivo ou número que não foi especificado na `FileOpen` instrução ou que foi especificado em uma `FileOpen` instrução, mas foi fechado posteriormente.</span><span class="sxs-lookup"><span data-stu-id="b269f-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
- <span data-ttu-id="b269f-106">Uma instrução refere-se a um arquivo com um número que está fora do intervalo de números de arquivo.</span><span class="sxs-lookup"><span data-stu-id="b269f-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
- <span data-ttu-id="b269f-107">Uma instrução refere-se a um nome de arquivo ou número que não é válido.</span><span class="sxs-lookup"><span data-stu-id="b269f-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b269f-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b269f-108">To correct this error</span></span>  
  
1. <span data-ttu-id="b269f-109">Verifique se o nome do arquivo está especificado em uma `FileOpen` instrução.</span><span class="sxs-lookup"><span data-stu-id="b269f-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="b269f-110">Observe que, se você chamou a `FileClose` instrução sem argumentos, você pode ter fechado inadvertidamente todos os arquivos abertos.</span><span class="sxs-lookup"><span data-stu-id="b269f-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2. <span data-ttu-id="b269f-111">Se o seu código estiver gerando números de arquivo forma algorítmica, verifique se os números são válidos.</span><span class="sxs-lookup"><span data-stu-id="b269f-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3. <span data-ttu-id="b269f-112">Verifique os nomes dos arquivos para garantir que eles estejam em conformidade com as convenções do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="b269f-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b269f-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="b269f-113">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [<span data-ttu-id="b269f-114">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b269f-114">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
