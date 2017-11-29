---
title: Interface ICorPublishProcessEnum
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcessEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcessEnum
helpviewer_keywords: ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 66e31911289d1ef8b590a0b7e7896adfa4998adc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="68dd3-102">Interface ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="68dd3-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="68dd3-103">Uma subclasse do [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface que fornece métodos para atravessar uma coleção de [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objetos.</span><span class="sxs-lookup"><span data-stu-id="68dd3-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="68dd3-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="68dd3-104">Methods</span></span>  
  
|<span data-ttu-id="68dd3-105">Método</span><span class="sxs-lookup"><span data-stu-id="68dd3-105">Method</span></span>|<span data-ttu-id="68dd3-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="68dd3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="68dd3-107">Próximo método</span><span class="sxs-lookup"><span data-stu-id="68dd3-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="68dd3-108">Obtém o número especificado de `ICorPublishProcess` instâncias da coleção, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="68dd3-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68dd3-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="68dd3-109">Remarks</span></span>  
 <span data-ttu-id="68dd3-110">O `ICorPublishProcessEnum` interface implementa os métodos da interface abstrata, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="68dd3-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="68dd3-111">Um `ICorPublishProcessEnum` instância é criada pelo [Icorpublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="68dd3-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="68dd3-112">A passagem do conjunto de `ICorPublishProcess` objetos é com base nos critérios de filtro fornecidos no momento em que o `ICorPublishProcessEnum` instância foi criada.</span><span class="sxs-lookup"><span data-stu-id="68dd3-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68dd3-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="68dd3-113">Requirements</span></span>  
 <span data-ttu-id="68dd3-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68dd3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68dd3-115">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="68dd3-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="68dd3-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68dd3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68dd3-117">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68dd3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68dd3-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68dd3-118">See Also</span></span>  
 [<span data-ttu-id="68dd3-119">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="68dd3-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="68dd3-120">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="68dd3-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
