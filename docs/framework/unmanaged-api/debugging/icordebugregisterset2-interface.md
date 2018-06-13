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
ms.openlocfilehash: 6f4947a9b6c0e3fd87ee474111f143d273c1d7b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422784"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="897c9-102">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="897c9-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="897c9-103">Estende os recursos do [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface para plataformas de hardware que tem mais de 64 registros.</span><span class="sxs-lookup"><span data-stu-id="897c9-103">Extends the capabilities of the [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="897c9-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="897c9-104">Methods</span></span>  
  
|<span data-ttu-id="897c9-105">Método</span><span class="sxs-lookup"><span data-stu-id="897c9-105">Method</span></span>|<span data-ttu-id="897c9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="897c9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="897c9-107">Método GetRegisters</span><span class="sxs-lookup"><span data-stu-id="897c9-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="897c9-108">Obtém o valor de cada registro (no computador que está executando código) que é especificado pela máscara de bits.</span><span class="sxs-lookup"><span data-stu-id="897c9-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="897c9-109">Método GetRegistersAvailable</span><span class="sxs-lookup"><span data-stu-id="897c9-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="897c9-110">Obtém uma matriz de bytes que fornece um bitmap de registros disponíveis.</span><span class="sxs-lookup"><span data-stu-id="897c9-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="897c9-111">Método SetRegisters</span><span class="sxs-lookup"><span data-stu-id="897c9-111">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="897c9-112">Não implementado no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="897c9-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="897c9-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="897c9-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="897c9-114">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="897c9-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="897c9-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="897c9-115">Requirements</span></span>  
 <span data-ttu-id="897c9-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="897c9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="897c9-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="897c9-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="897c9-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="897c9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="897c9-119">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="897c9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="897c9-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="897c9-120">See Also</span></span>  
 [<span data-ttu-id="897c9-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="897c9-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="897c9-122">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="897c9-122">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
