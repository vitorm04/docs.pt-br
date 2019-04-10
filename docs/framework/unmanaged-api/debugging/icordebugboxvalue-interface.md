---
title: Interface ICorDebugBoxValue
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue
helpviewer_keywords:
- ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3d3ae7e2-97d4-46de-a2c3-cb78f3490f9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a9a647a9c77a3c1f82ae3691e2a5e5b2f544cad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221958"
---
# <a name="icordebugboxvalue-interface"></a><span data-ttu-id="44e71-102">Interface ICorDebugBoxValue</span><span class="sxs-lookup"><span data-stu-id="44e71-102">ICorDebugBoxValue Interface</span></span>

<span data-ttu-id="44e71-103">Uma subclasse de "ICorDebugHeapValue" que representa um objeto de classe de valor Demarcado.</span><span class="sxs-lookup"><span data-stu-id="44e71-103">A subclass of "ICorDebugHeapValue" that represents a boxed value class object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="44e71-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="44e71-104">Methods</span></span>  
  
|<span data-ttu-id="44e71-105">Método</span><span class="sxs-lookup"><span data-stu-id="44e71-105">Method</span></span>|<span data-ttu-id="44e71-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="44e71-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="44e71-107">Método GetObject</span><span class="sxs-lookup"><span data-stu-id="44e71-107">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-getobject-method.md)|<span data-ttu-id="44e71-108">Obtém um ponteiro de interface para a instância de "ICorDebugObjectValue" demarcada.</span><span class="sxs-lookup"><span data-stu-id="44e71-108">Gets an interface pointer to the boxed "ICorDebugObjectValue" instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44e71-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="44e71-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44e71-110">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="44e71-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44e71-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="44e71-111">Requirements</span></span>  
 <span data-ttu-id="44e71-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44e71-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44e71-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44e71-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44e71-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44e71-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="44e71-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="44e71-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="44e71-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44e71-116">See also</span></span>

- [<span data-ttu-id="44e71-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="44e71-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
