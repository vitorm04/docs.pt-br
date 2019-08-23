---
title: Interface ICorDebugRegisterSet2
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2
helpviewer_keywords:
- ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95e8ad1ddce57252b7af3c7d72e8f8eb7bdb76b0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935085"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="94f6b-102">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="94f6b-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="94f6b-103">Estende os recursos da interface [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) para plataformas de hardware que têm mais de 64 registros.</span><span class="sxs-lookup"><span data-stu-id="94f6b-103">Extends the capabilities of the [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="94f6b-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="94f6b-104">Methods</span></span>  
  
|<span data-ttu-id="94f6b-105">Método</span><span class="sxs-lookup"><span data-stu-id="94f6b-105">Method</span></span>|<span data-ttu-id="94f6b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="94f6b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="94f6b-107">Método GetRegisters</span><span class="sxs-lookup"><span data-stu-id="94f6b-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="94f6b-108">Obtém o valor de cada registro (no computador que está executando o código) que é especificado pela máscara de bits.</span><span class="sxs-lookup"><span data-stu-id="94f6b-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="94f6b-109">Método GetRegistersAvailable</span><span class="sxs-lookup"><span data-stu-id="94f6b-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="94f6b-110">Obtém uma matriz de bytes que fornece um bitmap dos registros disponíveis.</span><span class="sxs-lookup"><span data-stu-id="94f6b-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="94f6b-111">Método SetRegisters</span><span class="sxs-lookup"><span data-stu-id="94f6b-111">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="94f6b-112">Não implementado na versão .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="94f6b-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94f6b-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="94f6b-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94f6b-114">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="94f6b-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94f6b-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="94f6b-115">Requirements</span></span>  
 <span data-ttu-id="94f6b-116">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94f6b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94f6b-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94f6b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94f6b-118">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94f6b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94f6b-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94f6b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94f6b-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94f6b-120">See also</span></span>

- [<span data-ttu-id="94f6b-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="94f6b-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="94f6b-122">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="94f6b-122">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
