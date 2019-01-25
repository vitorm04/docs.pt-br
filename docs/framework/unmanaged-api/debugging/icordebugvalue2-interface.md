---
title: Interface ICorDebugValue2
ms.date: 03/30/2017
api_name:
- ICorDebugValue2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2
helpviewer_keywords:
- ICorDebugValue2 interface [.NET Framework debugging]
ms.assetid: 3ff2ad2a-da5a-461b-8627-1a8eba49df9c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c4d4f5d85fb076748b3f8aae498f024804fb0b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492358"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="96ac7-102">Interface ICorDebugValue2</span><span class="sxs-lookup"><span data-stu-id="96ac7-102">ICorDebugValue2 Interface</span></span>
<span data-ttu-id="96ac7-103">Estende a interface "ICorDebugValue" para fornecer suporte para objetos de "ICorDebugType".</span><span class="sxs-lookup"><span data-stu-id="96ac7-103">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="96ac7-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="96ac7-104">Methods</span></span>  
  
|<span data-ttu-id="96ac7-105">Método</span><span class="sxs-lookup"><span data-stu-id="96ac7-105">Method</span></span>|<span data-ttu-id="96ac7-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="96ac7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="96ac7-107">Método GetExactType</span><span class="sxs-lookup"><span data-stu-id="96ac7-107">GetExactType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="96ac7-108">Obtém um ponteiro de interface para um `ICorDebugType` objeto que representa o <xref:System.Type> desse valor.</span><span class="sxs-lookup"><span data-stu-id="96ac7-108">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96ac7-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="96ac7-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96ac7-110">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="96ac7-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96ac7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96ac7-111">Requirements</span></span>  
 <span data-ttu-id="96ac7-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96ac7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96ac7-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96ac7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96ac7-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96ac7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96ac7-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96ac7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96ac7-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96ac7-116">See also</span></span>
- [<span data-ttu-id="96ac7-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="96ac7-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

- [<span data-ttu-id="96ac7-118">Interface ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="96ac7-118">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
