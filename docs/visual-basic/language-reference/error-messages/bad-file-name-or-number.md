---
title: "Nome de arquivo inválido ou número | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID52
dev_langs:
- VB
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
caps.latest.revision: 10
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
ms.openlocfilehash: 4c4bf6bbed297cff9616a6be9d1cd0212f0d652b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="a688a-102">Nome ou número de arquivo inválido</span><span class="sxs-lookup"><span data-stu-id="a688a-102">Bad file name or number</span></span>
<span data-ttu-id="a688a-103">Ocorreu um erro ao tentar acessar o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="a688a-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="a688a-104">Entre as possíveis causas para esse erro são:</span><span class="sxs-lookup"><span data-stu-id="a688a-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="a688a-105">Uma instrução refere-se a um arquivo com um nome de arquivo ou um número que não foi especificado no `FileOpen` instrução ou que foi especificado em um `FileOpen` instrução, mas foi subsequentemente fechado.</span><span class="sxs-lookup"><span data-stu-id="a688a-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
-   <span data-ttu-id="a688a-106">Uma instrução refere-se a um arquivo com um número que está fora do intervalo de números de arquivos.</span><span class="sxs-lookup"><span data-stu-id="a688a-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
-   <span data-ttu-id="a688a-107">Uma instrução refere-se a um nome de arquivo ou o número não é válido.</span><span class="sxs-lookup"><span data-stu-id="a688a-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a688a-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="a688a-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="a688a-109">Verifique se o nome do arquivo especificado em um `FileOpen` instrução.</span><span class="sxs-lookup"><span data-stu-id="a688a-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="a688a-110">Observe que, se você chamou o `FileClose` instrução sem argumentos, você pode ter fechado todos os arquivos abertos.</span><span class="sxs-lookup"><span data-stu-id="a688a-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2.  <span data-ttu-id="a688a-111">Se seu código está gerando números de arquivo algorítmica, verifique se que os números são válidos.</span><span class="sxs-lookup"><span data-stu-id="a688a-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3.  <span data-ttu-id="a688a-112">Verifique os nomes de arquivo para se certificar de que estejam em conformidade com as convenções do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="a688a-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a688a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a688a-113">See Also</span></span>  
 <span data-ttu-id="a688a-114"><xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A></xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A></span><span class="sxs-lookup"><span data-stu-id="a688a-114"><xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A></span></span>   
<span data-ttu-id="a688a-115"> [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)</span><span class="sxs-lookup"><span data-stu-id="a688a-115"> [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)</span></span>
