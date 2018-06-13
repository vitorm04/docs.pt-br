---
title: Interface ICorPublishProcessEnum
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd71a2bd4a52da8fa77592363e2eb7c8f5101fd3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423979"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="a0e8c-102">Interface ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="a0e8c-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="a0e8c-103">Uma subclasse do [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface que fornece métodos para atravessar uma coleção de [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objetos.</span><span class="sxs-lookup"><span data-stu-id="a0e8c-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a0e8c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a0e8c-104">Methods</span></span>  
  
|<span data-ttu-id="a0e8c-105">Método</span><span class="sxs-lookup"><span data-stu-id="a0e8c-105">Method</span></span>|<span data-ttu-id="a0e8c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0e8c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a0e8c-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="a0e8c-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="a0e8c-108">Obtém o número especificado de `ICorPublishProcess` instâncias da coleção, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="a0e8c-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0e8c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a0e8c-109">Remarks</span></span>  
 <span data-ttu-id="a0e8c-110">O `ICorPublishProcessEnum` interface implementa os métodos da interface abstrata, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a0e8c-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="a0e8c-111">Um `ICorPublishProcessEnum` instância é criada pelo [Icorpublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="a0e8c-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="a0e8c-112">A passagem do conjunto de `ICorPublishProcess` objetos é com base nos critérios de filtro fornecidos no momento em que o `ICorPublishProcessEnum` instância foi criada.</span><span class="sxs-lookup"><span data-stu-id="a0e8c-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0e8c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a0e8c-113">Requirements</span></span>  
 <span data-ttu-id="a0e8c-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0e8c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0e8c-115">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="a0e8c-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a0e8c-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0e8c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0e8c-117">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0e8c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0e8c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0e8c-118">See Also</span></span>  
 [<span data-ttu-id="a0e8c-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a0e8c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a0e8c-120">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="a0e8c-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
