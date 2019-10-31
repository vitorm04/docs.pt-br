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
ms.openlocfilehash: 0c26a2df3f73af5ebd1f8b735d7662bb23ba4228
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134161"
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="569b9-102">Método ICLRDataTarget::ReadVirtual</span><span class="sxs-lookup"><span data-stu-id="569b9-102">ICLRDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="569b9-103">Lê dados do endereço de memória virtual especificado no buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="569b9-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="569b9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="569b9-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="569b9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="569b9-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="569b9-106">no Um CLRDATA_ADDRESS que armazena o endereço de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="569b9-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="569b9-107">fora Um ponteiro para um buffer que recebe os dados.</span><span class="sxs-lookup"><span data-stu-id="569b9-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="569b9-108">no O comprimento do buffer.</span><span class="sxs-lookup"><span data-stu-id="569b9-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="569b9-109">fora Um ponteiro para o número de bytes retornados.</span><span class="sxs-lookup"><span data-stu-id="569b9-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="569b9-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="569b9-110">Requirements</span></span>  
 <span data-ttu-id="569b9-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="569b9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="569b9-112">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="569b9-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="569b9-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="569b9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="569b9-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="569b9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="569b9-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="569b9-115">See also</span></span>

- [<span data-ttu-id="569b9-116">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="569b9-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
