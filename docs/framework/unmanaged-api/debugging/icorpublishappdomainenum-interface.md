---
title: Interface ICorPublishAppDomainEnum
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum
helpviewer_keywords:
- ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f6d4af7c01f91dff77d6ba715ef845f523c7fb6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993545"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="9edb4-102">Interface ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="9edb4-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="9edb4-103">Uma subclasse do [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface que fornece métodos para percorrer uma coleção de [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objetos que existem atualmente dentro de um processo.</span><span class="sxs-lookup"><span data-stu-id="9edb4-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9edb4-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9edb4-104">Methods</span></span>  
  
|<span data-ttu-id="9edb4-105">Método</span><span class="sxs-lookup"><span data-stu-id="9edb4-105">Method</span></span>|<span data-ttu-id="9edb4-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9edb4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9edb4-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="9edb4-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="9edb4-108">Obtém o número especificado de `ICorPublishAppDomain` instâncias da coleção, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="9edb4-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9edb4-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="9edb4-109">Remarks</span></span>  
 <span data-ttu-id="9edb4-110">O `ICorPublishAppDomainEnum` interface implementa os métodos da interface abstrata [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="9edb4-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9edb4-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9edb4-111">Requirements</span></span>  
 <span data-ttu-id="9edb4-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9edb4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9edb4-113">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="9edb4-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="9edb4-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9edb4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9edb4-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9edb4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9edb4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9edb4-116">See also</span></span>

- [<span data-ttu-id="9edb4-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9edb4-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9edb4-118">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="9edb4-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
