---
title: Usar &#39; FileGetObject &#39; em vez de &#39; FileGet &#39; Quando usar argumento do tipo &#39; objeto &#39;
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 090b8088-895a-482a-9362-606596bac304
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 996e8a50f90c738bbc64c200125a785c0e9bcd58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a><span data-ttu-id="75945-102">Usar &#39; FileGetObject &#39; em vez de &#39; FileGet &#39; Quando usar argumento do tipo &#39; objeto &#39;</span><span class="sxs-lookup"><span data-stu-id="75945-102">Use &#39;FileGetObject&#39; instead of &#39;FileGet&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="75945-103">O `FileGet` método inclui um argumento do tipo `Object`.</span><span class="sxs-lookup"><span data-stu-id="75945-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="75945-104">`FileGetObject`deve ser usado no lugar de `FileGet` para evitar ambiguidades.</span><span class="sxs-lookup"><span data-stu-id="75945-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="75945-105">Observe que a funcionalidade oferecida pelo `My.Computer.Filesystem` oferece maior facilidade de uso e desempenho que o `FileGet` ou `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="75945-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="75945-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="75945-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="75945-107">Substitua `FileGet` por `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="75945-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="75945-108">Conversão de `Object` argumento para um tipo mais específico.</span><span class="sxs-lookup"><span data-stu-id="75945-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75945-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75945-109">See Also</span></span>  
 [<span data-ttu-id="75945-110">NÃO está em compilação: Função FileGetObject</span><span class="sxs-lookup"><span data-stu-id="75945-110">NOT IN BUILD: FileGetObject Function</span></span>](http://msdn.microsoft.com/en-us/3eda786b-d1ee-4b44-9dd7-0ea6bff072c0)  
 [<span data-ttu-id="75945-111">Objeto My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="75945-111">My.Computer.FileSystem Object</span></span>](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)
