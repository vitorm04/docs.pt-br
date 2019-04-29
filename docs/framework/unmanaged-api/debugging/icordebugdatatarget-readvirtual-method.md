---
title: Método ICorDebugDataTarget::ReadVirtual
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.ReadVirtual Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4749bfee22e58ad7c3ca29ec992da88493ca2c5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763835"
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="67dca-102">Método ICorDebugDataTarget::ReadVirtual</span><span class="sxs-lookup"><span data-stu-id="67dca-102">ICorDebugDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="67dca-103">Obtém um bloco de memória contígua, iniciando no endereço especificado e retorna-o no buffer fornecido.</span><span class="sxs-lookup"><span data-stu-id="67dca-103">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67dca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="67dca-104">Syntax</span></span>  
  
```  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67dca-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="67dca-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="67dca-106">[in] O endereço inicial de memória solicitada.</span><span class="sxs-lookup"><span data-stu-id="67dca-106">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="67dca-107">[out] O buffer onde a memória será armazenada.</span><span class="sxs-lookup"><span data-stu-id="67dca-107">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="67dca-108">[in] O número de bytes para obter o endereço de destino.</span><span class="sxs-lookup"><span data-stu-id="67dca-108">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="67dca-109">[out] O número de bytes realmente lidos do endereço de destino.</span><span class="sxs-lookup"><span data-stu-id="67dca-109">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="67dca-110">Isso pode ser menos de `bytesRequested`.</span><span class="sxs-lookup"><span data-stu-id="67dca-110">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67dca-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="67dca-111">Remarks</span></span>  
 <span data-ttu-id="67dca-112">Se o primeiro byte (no endereço inicial especificado) pode ser lidos, a chamada deve retornar êxito (para dar suporte à leitura eficiente de estruturas de dados com autodescritivos comprimento, como cadeias de caracteres terminada em nulo).</span><span class="sxs-lookup"><span data-stu-id="67dca-112">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67dca-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="67dca-113">Requirements</span></span>  
 <span data-ttu-id="67dca-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67dca-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67dca-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67dca-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67dca-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67dca-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67dca-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67dca-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67dca-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67dca-118">See also</span></span>

- [<span data-ttu-id="67dca-119">Interface ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="67dca-119">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="67dca-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="67dca-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="67dca-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="67dca-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
