---
title: "Método ICorDebugDataTarget::ReadVirtual"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget.ReadVirtual Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9b9f0399c05155a9925624e5c9d6bcb6a52f024
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="2a71c-102">Método ICorDebugDataTarget::ReadVirtual</span><span class="sxs-lookup"><span data-stu-id="2a71c-102">ICorDebugDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="2a71c-103">Obtém um bloco de memória contígua, iniciando no endereço especificado e o retorna no buffer fornecido.</span><span class="sxs-lookup"><span data-stu-id="2a71c-103">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a71c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a71c-104">Syntax</span></span>  
  
```  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a71c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2a71c-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="2a71c-106">[in] O endereço inicial de memória solicitada.</span><span class="sxs-lookup"><span data-stu-id="2a71c-106">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="2a71c-107">[out] O buffer em que a memória será armazenada.</span><span class="sxs-lookup"><span data-stu-id="2a71c-107">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="2a71c-108">[in] O número de bytes a ser obtido o endereço de destino.</span><span class="sxs-lookup"><span data-stu-id="2a71c-108">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="2a71c-109">[out] O número de bytes realmente lidos do endereço de destino.</span><span class="sxs-lookup"><span data-stu-id="2a71c-109">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="2a71c-110">Isso pode ser menos de `bytesRequested`.</span><span class="sxs-lookup"><span data-stu-id="2a71c-110">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a71c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a71c-111">Remarks</span></span>  
 <span data-ttu-id="2a71c-112">Se o primeiro byte (no endereço inicial especificada) pode ser lidos, a chamada deve retornar êxito (para dar suporte a leitura eficiente de estruturas de dados com autodescritivos comprimento, como cadeias de caracteres terminada em nulo).</span><span class="sxs-lookup"><span data-stu-id="2a71c-112">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a71c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2a71c-113">Requirements</span></span>  
 <span data-ttu-id="2a71c-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a71c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a71c-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a71c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a71c-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a71c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a71c-117">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a71c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a71c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a71c-118">See Also</span></span>  
 [<span data-ttu-id="2a71c-119">Interface ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="2a71c-119">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="2a71c-120">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="2a71c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2a71c-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="2a71c-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
