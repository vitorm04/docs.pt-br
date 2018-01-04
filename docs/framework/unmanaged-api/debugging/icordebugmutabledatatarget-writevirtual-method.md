---
title: "Método ICorDebugMutableDataTarget::WriteVirtual"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 303c5737ebd241b8f2f756de0ed5426787de3bd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a><span data-ttu-id="ba721-102">Método ICorDebugMutableDataTarget::WriteVirtual</span><span class="sxs-lookup"><span data-stu-id="ba721-102">ICorDebugMutableDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="ba721-103">Grava a memória no espaço de endereço de processo de destino.</span><span class="sxs-lookup"><span data-stu-id="ba721-103">Writes memory into the target process address space.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba721-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba721-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba721-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ba721-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="ba721-106">[in] O endereço no qual gravar o conteúdo de `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="ba721-106">[in] The address at which to write the contents of `pBuffer`.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="ba721-107">[in] Um ponteiro para uma matriz de bytes que contém os bytes a serem gravados.</span><span class="sxs-lookup"><span data-stu-id="ba721-107">[in] A pointer to a byte array that contains the bytes to be written.</span></span>  
  
 `address`  
 <span data-ttu-id="ba721-108">[in] O número de bytes em `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="ba721-108">[in] The number of bytes in `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba721-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ba721-109">Return Value</span></span>  
 <span data-ttu-id="ba721-110">`S_OK`no caso de sucesso, ou qualquer outra `HRESULT` em caso de falha.</span><span class="sxs-lookup"><span data-stu-id="ba721-110">`S_OK` on success, or any other `HRESULT` on failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba721-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="ba721-111">Remarks</span></span>  
 <span data-ttu-id="ba721-112">Se qualquer bytes não podem ser gravados, a chamada de método falhar sem alterar qualquer bytes no espaço de endereço de destino.</span><span class="sxs-lookup"><span data-stu-id="ba721-112">If any bytes cannot be written, the method call fails without changing any bytes in the target address space.</span></span> <span data-ttu-id="ba721-113">(Caso contrário, o destino deve ser em um estado inconsistente que torna mais depuração confiável.)</span><span class="sxs-lookup"><span data-stu-id="ba721-113">(Otherwise, the target would be in an inconsistent state that makes further debugging unreliable.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba721-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ba721-114">Requirements</span></span>  
 <span data-ttu-id="ba721-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba721-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba721-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba721-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba721-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba721-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba721-118">**Versões do .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba721-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba721-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba721-119">See Also</span></span>  
 [<span data-ttu-id="ba721-120">Interface ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="ba721-120">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="ba721-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ba721-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
