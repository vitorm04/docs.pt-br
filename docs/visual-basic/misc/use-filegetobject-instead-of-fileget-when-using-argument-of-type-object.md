---
title: Use 'FileGetObject' em vez de 'FileGet' quando usar argumento do tipo 'Object'
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 60eaabc686070aced908116728f06d4e82b5cecb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723388"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a><span data-ttu-id="520b1-102">Use 'FileGetObject' em vez de 'FileGet' quando usar argumento do tipo 'Object'</span><span class="sxs-lookup"><span data-stu-id="520b1-102">Use 'FileGetObject' instead of 'FileGet' when using argument of type 'Object'</span></span>
<span data-ttu-id="520b1-103">O `FileGet` método inclui um argumento do tipo `Object`.</span><span class="sxs-lookup"><span data-stu-id="520b1-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="520b1-104">`FileGetObject` deve ser usado no lugar de `FileGet` para evitar ambiguidades.</span><span class="sxs-lookup"><span data-stu-id="520b1-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="520b1-105">Observe que a funcionalidade oferecida pelo `My.Computer.Filesystem` oferece maior facilidade de uso e desempenho que o `FileGet` ou `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="520b1-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="520b1-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="520b1-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="520b1-107">Substitua `FileGet` por `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="520b1-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="520b1-108">Conversão de `Object` argumento para um tipo mais específico.</span><span class="sxs-lookup"><span data-stu-id="520b1-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="520b1-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="520b1-109">See also</span></span>

- [<span data-ttu-id="520b1-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="520b1-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
