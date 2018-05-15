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
ms.openlocfilehash: e55bc18c7a41e235d1ba6274067c45c26dc7262a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="4979f-102">Método ICLRDataTarget::WriteVirtual</span><span class="sxs-lookup"><span data-stu-id="4979f-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="4979f-103">Grava dados de buffer especificado para o endereço de memória virtual especificado.</span><span class="sxs-lookup"><span data-stu-id="4979f-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4979f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4979f-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4979f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4979f-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="4979f-106">[in] Um CLRDATA_ADDRESS que armazena o endereço de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="4979f-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="4979f-107">[in] Um ponteiro para um buffer que armazena os dados a serem gravados.</span><span class="sxs-lookup"><span data-stu-id="4979f-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="4979f-108">[in] O número de bytes a serem gravados.</span><span class="sxs-lookup"><span data-stu-id="4979f-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="4979f-109">[out] Um ponteiro para o número real de bytes que foram gravados.</span><span class="sxs-lookup"><span data-stu-id="4979f-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4979f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4979f-110">Requirements</span></span>  
 <span data-ttu-id="4979f-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4979f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4979f-112">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="4979f-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4979f-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4979f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4979f-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4979f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4979f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4979f-115">See Also</span></span>  
 [<span data-ttu-id="4979f-116">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="4979f-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
