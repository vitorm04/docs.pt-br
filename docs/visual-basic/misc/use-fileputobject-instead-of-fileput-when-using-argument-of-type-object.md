---
title: Usar &#39; FilePutObject &#39; em vez de &#39; FilePut &#39; Quando usar argumento do tipo &#39; objeto &#39;
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cba4af206e2dbf767fdb883ec81229a67842c57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a><span data-ttu-id="a0900-102">Usar &#39; FilePutObject &#39; em vez de &#39; FilePut &#39; Quando usar argumento do tipo &#39; objeto &#39;</span><span class="sxs-lookup"><span data-stu-id="a0900-102">Use &#39;FilePutObject&#39; instead of &#39;FilePut&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="a0900-103">O `FilePut` método inclui um argumento do tipo `Object`.</span><span class="sxs-lookup"><span data-stu-id="a0900-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="a0900-104">`FilePutObject`deve ser usado no lugar de `FilePut` para evitar ambiguidades.</span><span class="sxs-lookup"><span data-stu-id="a0900-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a0900-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="a0900-105">To correct this error</span></span>  
  
-   <span data-ttu-id="a0900-106">Substitua `FilePut` por `FilePutObject`.</span><span class="sxs-lookup"><span data-stu-id="a0900-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="a0900-107">Conversão de `Object` argumento para um tipo mais específico.</span><span class="sxs-lookup"><span data-stu-id="a0900-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="a0900-108">Usar a funcionalidade disponível a `My.Computer.FileSystem` objeto.</span><span class="sxs-lookup"><span data-stu-id="a0900-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0900-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0900-109">See Also</span></span>  
 [<span data-ttu-id="a0900-110">NÃO está em compilação: Função FilePutObject</span><span class="sxs-lookup"><span data-stu-id="a0900-110">NOT IN BUILD: FilePutObject Function</span></span>](http://msdn.microsoft.com/en-us/a0f52a1c-5ecc-4945-b18c-03147af61d6b)  
 [<span data-ttu-id="a0900-111">Objeto My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="a0900-111">My.Computer.FileSystem Object</span></span>](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)  
 [<span data-ttu-id="a0900-112">Método WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="a0900-112">My.Computer.FileSystem.WriteAllBytes Method</span></span>](http://msdn.microsoft.com/en-us/b1a24dc1-eac8-4e22-8ffa-cc3bacbaf826)
