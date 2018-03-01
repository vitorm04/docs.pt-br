---
title: Interface ICorDebugMetaDataLocator
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugMetaDataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator
helpviewer_keywords:
- ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: 287f5ecd-863f-4090-a615-077859f0257b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dead97961713f2d19147e242a6161aa9477905a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="ad9b2-102">Interface ICorDebugMetaDataLocator</span><span class="sxs-lookup"><span data-stu-id="ad9b2-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="ad9b2-103">Fornece informações de metadados ao depurador.</span><span class="sxs-lookup"><span data-stu-id="ad9b2-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ad9b2-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ad9b2-104">Methods</span></span>  
  
|<span data-ttu-id="ad9b2-105">Método</span><span class="sxs-lookup"><span data-stu-id="ad9b2-105">Method</span></span>|<span data-ttu-id="ad9b2-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad9b2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ad9b2-107">Método GetMetaData</span><span class="sxs-lookup"><span data-stu-id="ad9b2-107">GetMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="ad9b2-108">Solicita que o depurador para retornar o caminho completo para um módulo cujos metadados é necessária para concluir uma operação solicitado do depurador.</span><span class="sxs-lookup"><span data-stu-id="ad9b2-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad9b2-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ad9b2-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad9b2-110">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="ad9b2-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad9b2-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad9b2-111">Requirements</span></span>  
 <span data-ttu-id="ad9b2-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad9b2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad9b2-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad9b2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad9b2-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad9b2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad9b2-115">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad9b2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad9b2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad9b2-116">See Also</span></span>  
 [<span data-ttu-id="ad9b2-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ad9b2-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ad9b2-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="ad9b2-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
