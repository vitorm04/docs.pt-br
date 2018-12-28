---
title: Use 'FileGetObject' em vez de 'FileGet' quando usar argumento do tipo 'Object'
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: ddbe187ed1210d238448a5ff3feaee18beea1def
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2018
ms.locfileid: "53768005"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a><span data-ttu-id="330d7-102">Use 'FileGetObject' em vez de 'FileGet' quando usar argumento do tipo 'Object'</span><span class="sxs-lookup"><span data-stu-id="330d7-102">Use 'FileGetObject' instead of 'FileGet' when using argument of type 'Object'</span></span>
<span data-ttu-id="330d7-103">O `FileGet` método inclui um argumento do tipo `Object`.</span><span class="sxs-lookup"><span data-stu-id="330d7-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="330d7-104">`FileGetObject` deve ser usado no lugar de `FileGet` para evitar ambiguidades.</span><span class="sxs-lookup"><span data-stu-id="330d7-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="330d7-105">Observe que a funcionalidade oferecida pelo `My.Computer.Filesystem` oferece maior facilidade de uso e desempenho que o `FileGet` ou `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="330d7-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="330d7-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="330d7-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="330d7-107">Substitua `FileGet` por `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="330d7-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="330d7-108">Conversão de `Object` argumento para um tipo mais específico.</span><span class="sxs-lookup"><span data-stu-id="330d7-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="330d7-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="330d7-109">See Also</span></span>  
   
 [<span data-ttu-id="330d7-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="330d7-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
