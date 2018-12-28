---
title: Use 'FilePutObject' em vez de 'FilePut' quando usar argumento do tipo 'Object'
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: df7d7c54992984bcb1684e41f60ae8361a3aed03
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2018
ms.locfileid: "53774219"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a><span data-ttu-id="22ac0-102">Use 'FilePutObject' em vez de 'FilePut' quando usar argumento do tipo 'Object'</span><span class="sxs-lookup"><span data-stu-id="22ac0-102">Use 'FilePutObject' instead of 'FilePut' when using argument of type 'Object'</span></span>
<span data-ttu-id="22ac0-103">O `FilePut` método inclui um argumento do tipo `Object`.</span><span class="sxs-lookup"><span data-stu-id="22ac0-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="22ac0-104">`FilePutObject` deve ser usado no lugar de `FilePut` para evitar ambiguidades.</span><span class="sxs-lookup"><span data-stu-id="22ac0-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="22ac0-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="22ac0-105">To correct this error</span></span>  
  
-   <span data-ttu-id="22ac0-106">Substitua `FilePut` por `FilePutObject`.</span><span class="sxs-lookup"><span data-stu-id="22ac0-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="22ac0-107">Conversão de `Object` argumento para um tipo mais específico.</span><span class="sxs-lookup"><span data-stu-id="22ac0-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="22ac0-108">Use a funcionalidade disponível no `My.Computer.FileSystem` objeto.</span><span class="sxs-lookup"><span data-stu-id="22ac0-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22ac0-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22ac0-109">See Also</span></span>  
   
 [<span data-ttu-id="22ac0-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="22ac0-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [<span data-ttu-id="22ac0-111">WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="22ac0-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
