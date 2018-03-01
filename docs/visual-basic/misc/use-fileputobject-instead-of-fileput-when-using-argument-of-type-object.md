---
title: Usar &#39; FilePutObject &#39; em vez de &#39; FilePut &#39; Quando usar argumento do tipo &#39; objeto &#39;
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5612c2bd4dc08f767643d2cd865a2ba1a8210c15
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a><span data-ttu-id="42778-102">Usar &#39; FilePutObject &#39; em vez de &#39; FilePut &#39; Quando usar argumento do tipo &#39; objeto &#39;</span><span class="sxs-lookup"><span data-stu-id="42778-102">Use &#39;FilePutObject&#39; instead of &#39;FilePut&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="42778-103">O `FilePut` método inclui um argumento do tipo `Object`.</span><span class="sxs-lookup"><span data-stu-id="42778-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="42778-104">`FilePutObject`deve ser usado no lugar de `FilePut` para evitar ambiguidades.</span><span class="sxs-lookup"><span data-stu-id="42778-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="42778-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="42778-105">To correct this error</span></span>  
  
-   <span data-ttu-id="42778-106">Substitua `FilePut` por `FilePutObject`.</span><span class="sxs-lookup"><span data-stu-id="42778-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="42778-107">Conversão de `Object` argumento para um tipo mais específico.</span><span class="sxs-lookup"><span data-stu-id="42778-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="42778-108">Usar a funcionalidade disponível a `My.Computer.FileSystem` objeto.</span><span class="sxs-lookup"><span data-stu-id="42778-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42778-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42778-109">See Also</span></span>  
   
 [<span data-ttu-id="42778-110">FileSystem</span><span class="sxs-lookup"><span data-stu-id="42778-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [<span data-ttu-id="42778-111">WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="42778-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
