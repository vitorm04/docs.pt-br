---
title: Use 'FilePutObject' em vez de 'FilePut' quando usar argumento do tipo 'Object'
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 3d793151905c61ee12eccdfdb5e9567a4924bb35
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022513"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a><span data-ttu-id="22b13-102">Use 'FilePutObject' em vez de 'FilePut' quando usar argumento do tipo 'Object'</span><span class="sxs-lookup"><span data-stu-id="22b13-102">Use 'FilePutObject' instead of 'FilePut' when using argument of type 'Object'</span></span>
<span data-ttu-id="22b13-103">O `FilePut` método inclui um argumento do tipo `Object`.</span><span class="sxs-lookup"><span data-stu-id="22b13-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="22b13-104">`FilePutObject` deve ser usado no lugar de `FilePut` para evitar ambiguidades.</span><span class="sxs-lookup"><span data-stu-id="22b13-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="22b13-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="22b13-105">To correct this error</span></span>  
  
- <span data-ttu-id="22b13-106">Substitua `FilePut` por `FilePutObject`.</span><span class="sxs-lookup"><span data-stu-id="22b13-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
- <span data-ttu-id="22b13-107">Conversão de `Object` argumento para um tipo mais específico.</span><span class="sxs-lookup"><span data-stu-id="22b13-107">Cast the `Object` argument to a more specific type.</span></span>  
  
- <span data-ttu-id="22b13-108">Use a funcionalidade disponível no `My.Computer.FileSystem` objeto.</span><span class="sxs-lookup"><span data-stu-id="22b13-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22b13-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22b13-109">See also</span></span>

- [<span data-ttu-id="22b13-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="22b13-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [<span data-ttu-id="22b13-111">My.Computer.FileSystem.WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="22b13-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
