---
title: Método ICLRDataTarget::WriteVirtual
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.WriteVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::WriteVirtual
helpviewer_keywords:
- ICLRDataTarget::WriteVirtual method [.NET Framework debugging]
- WriteVirtual method [.NET Framework debugging]
ms.assetid: d627e8b7-a605-40ac-b9bb-da9a3f1b66d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a0ad4b7e907412aced911d7869ffce81eb867448
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738511"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="504a2-102">Método ICLRDataTarget::WriteVirtual</span><span class="sxs-lookup"><span data-stu-id="504a2-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="504a2-103">Grava dados de buffer especificado para o endereço da memória virtual especificado.</span><span class="sxs-lookup"><span data-stu-id="504a2-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="504a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="504a2-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="504a2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="504a2-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="504a2-106">[in] Um CLRDATA_ADDRESS que armazena o endereço de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="504a2-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="504a2-107">[in] Um ponteiro para um buffer que armazena os dados a serem gravados.</span><span class="sxs-lookup"><span data-stu-id="504a2-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="504a2-108">[in] O número de bytes a serem gravados.</span><span class="sxs-lookup"><span data-stu-id="504a2-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="504a2-109">[out] Um ponteiro para o número real de bytes que foram gravados.</span><span class="sxs-lookup"><span data-stu-id="504a2-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="504a2-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="504a2-110">Requirements</span></span>  
 <span data-ttu-id="504a2-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="504a2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="504a2-112">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="504a2-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="504a2-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="504a2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="504a2-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="504a2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="504a2-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="504a2-115">See also</span></span>

- [<span data-ttu-id="504a2-116">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="504a2-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
