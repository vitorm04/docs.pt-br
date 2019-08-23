---
title: Interface ICorDebugInternalFrame
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame
helpviewer_keywords:
- ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9764cdcd07a09f5192a8f43b9baa5be40305c40b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910165"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="5b362-102">Interface ICorDebugInternalFrame</span><span class="sxs-lookup"><span data-stu-id="5b362-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="5b362-103">Representa um quadro interno de tempo de execução na pilha.</span><span class="sxs-lookup"><span data-stu-id="5b362-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="5b362-104">Essa interface é uma subclasse da interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="5b362-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5b362-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="5b362-105">Methods</span></span>  
  
|<span data-ttu-id="5b362-106">Método</span><span class="sxs-lookup"><span data-stu-id="5b362-106">Method</span></span>|<span data-ttu-id="5b362-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b362-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5b362-108">Método GetFrameType</span><span class="sxs-lookup"><span data-stu-id="5b362-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="5b362-109">Obtém o tipo deste quadro interno.</span><span class="sxs-lookup"><span data-stu-id="5b362-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b362-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="5b362-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b362-111">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="5b362-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b362-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5b362-112">Requirements</span></span>  
 <span data-ttu-id="5b362-113">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b362-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b362-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b362-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b362-115">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b362-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b362-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b362-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b362-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b362-117">See also</span></span>

- [<span data-ttu-id="5b362-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5b362-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
