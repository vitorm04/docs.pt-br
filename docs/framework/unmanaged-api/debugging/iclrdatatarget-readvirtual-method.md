---
title: Método ICLRDataTarget::ReadVirtual
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.ReadVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::ReadVirtual
helpviewer_keywords:
- ReadVirtual method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::ReadVirtual method [.NET Framework debugging]
ms.assetid: da3769eb-1828-4aa1-b9ed-db4842136a43
topic_type:
- apiref
ms.openlocfilehash: 0332fae46d6a65cfb7cc0b929cc2fd0d97e1790e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179152"
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="d6f91-102">Método ICLRDataTarget::ReadVirtual</span><span class="sxs-lookup"><span data-stu-id="d6f91-102">ICLRDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="d6f91-103">Lê dados do endereço de memória virtual especificado no buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="d6f91-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6f91-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6f91-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6f91-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="d6f91-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="d6f91-106">[em] Um CLRDATA_ADDRESS que armazena o endereço de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="d6f91-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="d6f91-107">[fora] Um ponteiro para um buffer que recebe os dados.</span><span class="sxs-lookup"><span data-stu-id="d6f91-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="d6f91-108">[em] O comprimento do tampão.</span><span class="sxs-lookup"><span data-stu-id="d6f91-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="d6f91-109">[fora] Um ponteiro para o número de bytes devolvido.</span><span class="sxs-lookup"><span data-stu-id="d6f91-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6f91-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d6f91-110">Requirements</span></span>  
 <span data-ttu-id="d6f91-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6f91-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6f91-112">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="d6f91-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d6f91-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6f91-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6f91-114">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6f91-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6f91-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="d6f91-115">See also</span></span>

- [<span data-ttu-id="d6f91-116">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="d6f91-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
