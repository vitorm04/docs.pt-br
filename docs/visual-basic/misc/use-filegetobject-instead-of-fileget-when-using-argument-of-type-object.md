---
title: Use &#39;FileGetObject&#39; em vez de &#39;FileGet&#39; quando usar argumento do tipo &#39;objeto&#39;
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 2edb80f6df95774e0ea5a7b51e57925845d7ba75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a><span data-ttu-id="c1980-102">Use &#39;FileGetObject&#39; em vez de &#39;FileGet&#39; quando usar argumento do tipo &#39;objeto&#39;</span><span class="sxs-lookup"><span data-stu-id="c1980-102">Use &#39;FileGetObject&#39; instead of &#39;FileGet&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="c1980-103">O `FileGet` método inclui um argumento do tipo `Object`.</span><span class="sxs-lookup"><span data-stu-id="c1980-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="c1980-104">`FileGetObject` deve ser usado no lugar de `FileGet` para evitar ambiguidades.</span><span class="sxs-lookup"><span data-stu-id="c1980-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="c1980-105">Observe que a funcionalidade oferecida pelo `My.Computer.Filesystem` oferece maior facilidade de uso e desempenho que o `FileGet` ou `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="c1980-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c1980-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="c1980-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="c1980-107">Substitua `FileGet` por `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="c1980-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="c1980-108">Conversão de `Object` argumento para um tipo mais específico.</span><span class="sxs-lookup"><span data-stu-id="c1980-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1980-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1980-109">See Also</span></span>  
   
 [<span data-ttu-id="c1980-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="c1980-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
