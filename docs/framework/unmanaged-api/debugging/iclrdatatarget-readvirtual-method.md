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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c9080a588b96c5b89c280a0fb407952bd580f26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="81360-102">Método ICLRDataTarget::ReadVirtual</span><span class="sxs-lookup"><span data-stu-id="81360-102">ICLRDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="81360-103">Lê dados do endereço de memória virtual especificado no buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="81360-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81360-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81360-104">Syntax</span></span>  
  
```  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81360-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="81360-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="81360-106">[in] Um CLRDATA_ADDRESS que armazena o endereço de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="81360-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="81360-107">[out] Um ponteiro para um buffer que recebe os dados.</span><span class="sxs-lookup"><span data-stu-id="81360-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="81360-108">[in] O comprimento do buffer.</span><span class="sxs-lookup"><span data-stu-id="81360-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="81360-109">[out] Um ponteiro para o número de bytes retornados.</span><span class="sxs-lookup"><span data-stu-id="81360-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81360-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81360-110">Requirements</span></span>  
 <span data-ttu-id="81360-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81360-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81360-112">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="81360-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="81360-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81360-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81360-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81360-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81360-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81360-115">See Also</span></span>  
 [<span data-ttu-id="81360-116">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="81360-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
