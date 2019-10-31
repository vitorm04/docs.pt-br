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
ms.openlocfilehash: cbe2aa48a8b67b0b6e88f7b5267bc70848fe3cec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140321"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="920da-102">Interface ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="920da-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="920da-103">Uma subclasse da interface [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) que fornece métodos para atravessar uma coleção de objetos [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) que existem atualmente dentro de um processo.</span><span class="sxs-lookup"><span data-stu-id="920da-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="920da-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="920da-104">Methods</span></span>  
  
|<span data-ttu-id="920da-105">Método</span><span class="sxs-lookup"><span data-stu-id="920da-105">Method</span></span>|<span data-ttu-id="920da-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="920da-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="920da-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="920da-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="920da-108">Obtém o número especificado de instâncias de `ICorPublishAppDomain` da coleção, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="920da-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="920da-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="920da-109">Remarks</span></span>  
 <span data-ttu-id="920da-110">A interface `ICorPublishAppDomainEnum` implementa os métodos da interface abstrata, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="920da-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="920da-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="920da-111">Requirements</span></span>  
 <span data-ttu-id="920da-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="920da-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="920da-113">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="920da-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="920da-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="920da-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="920da-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="920da-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="920da-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="920da-116">See also</span></span>

- [<span data-ttu-id="920da-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="920da-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="920da-118">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="920da-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
