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
ms.openlocfilehash: 36a18d92f05db55957bba55de84490c0da1a1f86
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976506"
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="6046b-102">Método ICorDebugDataTarget::ReadVirtual</span><span class="sxs-lookup"><span data-stu-id="6046b-102">ICorDebugDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="6046b-103">Obtém um bloco de memória contígua a partir do endereço especificado e a retorna no buffer fornecido.</span><span class="sxs-lookup"><span data-stu-id="6046b-103">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6046b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6046b-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6046b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6046b-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="6046b-106">no O endereço inicial da memória solicitada.</span><span class="sxs-lookup"><span data-stu-id="6046b-106">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="6046b-107">fora O buffer em que a memória será armazenada.</span><span class="sxs-lookup"><span data-stu-id="6046b-107">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="6046b-108">no O número de bytes a serem obtidos do endereço de destino.</span><span class="sxs-lookup"><span data-stu-id="6046b-108">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="6046b-109">fora O número de bytes realmente lidos do endereço de destino.</span><span class="sxs-lookup"><span data-stu-id="6046b-109">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="6046b-110">Isso pode ser menor que `bytesRequested`.</span><span class="sxs-lookup"><span data-stu-id="6046b-110">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6046b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="6046b-111">Remarks</span></span>  
 <span data-ttu-id="6046b-112">Se o primeiro byte (no endereço inicial especificado) puder ser lido, a chamada deverá retornar êxito (para dar suporte à leitura eficiente de estruturas de dados com comprimento autodescritivo, como cadeias de caracteres terminadas em nulo).</span><span class="sxs-lookup"><span data-stu-id="6046b-112">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6046b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6046b-113">Requirements</span></span>  
 <span data-ttu-id="6046b-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6046b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6046b-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6046b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6046b-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6046b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6046b-117">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6046b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6046b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6046b-118">See also</span></span>

- [<span data-ttu-id="6046b-119">Interface ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="6046b-119">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="6046b-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6046b-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6046b-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="6046b-121">Debugging</span></span>](index.md)
