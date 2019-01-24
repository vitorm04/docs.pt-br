---
title: Método ICorDebugMutableDataTarget::WriteVirtual
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c0f07e02ee92fda772a44fe235c3dcb414882bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495949"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a><span data-ttu-id="94b45-102">Método ICorDebugMutableDataTarget::WriteVirtual</span><span class="sxs-lookup"><span data-stu-id="94b45-102">ICorDebugMutableDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="94b45-103">Grava a memória no espaço de endereço do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="94b45-103">Writes memory into the target process address space.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94b45-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94b45-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94b45-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="94b45-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="94b45-106">[in] O endereço no qual gravar o conteúdo de `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="94b45-106">[in] The address at which to write the contents of `pBuffer`.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="94b45-107">[in] Um ponteiro para uma matriz de bytes que contém os bytes a serem gravados.</span><span class="sxs-lookup"><span data-stu-id="94b45-107">[in] A pointer to a byte array that contains the bytes to be written.</span></span>  
  
 `address`  
 <span data-ttu-id="94b45-108">[in] O número de bytes em `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="94b45-108">[in] The number of bytes in `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94b45-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="94b45-109">Return Value</span></span>  
 <span data-ttu-id="94b45-110">`S_OK` no êxito ou qualquer outro `HRESULT` em caso de falha.</span><span class="sxs-lookup"><span data-stu-id="94b45-110">`S_OK` on success, or any other `HRESULT` on failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94b45-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="94b45-111">Remarks</span></span>  
 <span data-ttu-id="94b45-112">Se qualquer não podem ser gravados, a chamada de método falhará sem alterar quaisquer bytes no espaço de endereço de destino.</span><span class="sxs-lookup"><span data-stu-id="94b45-112">If any bytes cannot be written, the method call fails without changing any bytes in the target address space.</span></span> <span data-ttu-id="94b45-113">(Caso contrário, o destino seria em um estado inconsistente que torna mais depurações não confiável.)</span><span class="sxs-lookup"><span data-stu-id="94b45-113">(Otherwise, the target would be in an inconsistent state that makes further debugging unreliable.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94b45-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="94b45-114">Requirements</span></span>  
 <span data-ttu-id="94b45-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94b45-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94b45-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94b45-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94b45-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94b45-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94b45-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94b45-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94b45-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94b45-119">See also</span></span>
- [<span data-ttu-id="94b45-120">Interface ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="94b45-120">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="94b45-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="94b45-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
