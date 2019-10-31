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
ms.openlocfilehash: 47beba867cd2246c98cb02c3a563b948c15f5154
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131322"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="fd519-102">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="fd519-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="fd519-103">Estende os recursos da interface [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) para plataformas de hardware que têm mais de 64 registros.</span><span class="sxs-lookup"><span data-stu-id="fd519-103">Extends the capabilities of the [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fd519-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="fd519-104">Methods</span></span>  
  
|<span data-ttu-id="fd519-105">Método</span><span class="sxs-lookup"><span data-stu-id="fd519-105">Method</span></span>|<span data-ttu-id="fd519-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="fd519-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fd519-107">Método GetRegisters</span><span class="sxs-lookup"><span data-stu-id="fd519-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="fd519-108">Obtém o valor de cada registro (no computador que está executando o código) que é especificado pela máscara de bits.</span><span class="sxs-lookup"><span data-stu-id="fd519-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="fd519-109">Método GetRegistersAvailable</span><span class="sxs-lookup"><span data-stu-id="fd519-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="fd519-110">Obtém uma matriz de bytes que fornece um bitmap dos registros disponíveis.</span><span class="sxs-lookup"><span data-stu-id="fd519-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="fd519-111">Método SetRegisters</span><span class="sxs-lookup"><span data-stu-id="fd519-111">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="fd519-112">Não implementado na versão .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="fd519-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd519-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="fd519-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd519-114">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="fd519-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd519-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fd519-115">Requirements</span></span>  
 <span data-ttu-id="fd519-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd519-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd519-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd519-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd519-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd519-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd519-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd519-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd519-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd519-120">See also</span></span>

- [<span data-ttu-id="fd519-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="fd519-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="fd519-122">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="fd519-122">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
