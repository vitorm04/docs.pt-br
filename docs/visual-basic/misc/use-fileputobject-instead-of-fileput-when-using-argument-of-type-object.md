---
title: Use &#39;FilePutObject&#39; em vez de &#39;FilePut&#39; quando usar argumento do tipo &#39;objeto&#39;
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 529352d98c175981c20861205ce04c8a2ebcdca9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641122"
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a><span data-ttu-id="5e843-102">Use &#39;FilePutObject&#39; em vez de &#39;FilePut&#39; quando usar argumento do tipo &#39;objeto&#39;</span><span class="sxs-lookup"><span data-stu-id="5e843-102">Use &#39;FilePutObject&#39; instead of &#39;FilePut&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="5e843-103">O `FilePut` método inclui um argumento do tipo `Object`.</span><span class="sxs-lookup"><span data-stu-id="5e843-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="5e843-104">`FilePutObject` deve ser usado no lugar de `FilePut` para evitar ambiguidades.</span><span class="sxs-lookup"><span data-stu-id="5e843-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5e843-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="5e843-105">To correct this error</span></span>  
  
-   <span data-ttu-id="5e843-106">Substitua `FilePut` por `FilePutObject`.</span><span class="sxs-lookup"><span data-stu-id="5e843-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="5e843-107">Conversão de `Object` argumento para um tipo mais específico.</span><span class="sxs-lookup"><span data-stu-id="5e843-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="5e843-108">Usar a funcionalidade disponível a `My.Computer.FileSystem` objeto.</span><span class="sxs-lookup"><span data-stu-id="5e843-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e843-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e843-109">See Also</span></span>  
   
 [<span data-ttu-id="5e843-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="5e843-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [<span data-ttu-id="5e843-111">WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="5e843-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
