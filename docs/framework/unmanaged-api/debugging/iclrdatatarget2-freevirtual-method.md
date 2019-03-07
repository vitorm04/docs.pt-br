---
title: Método ICLRDataTarget2::FreeVirtual
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.FreeVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8d2f6a716c65596c781015bad0dea52705611a0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487142"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="81c9e-102">Método ICLRDataTarget2::FreeVirtual</span><span class="sxs-lookup"><span data-stu-id="81c9e-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="81c9e-103">Chamado pelo serviço common language runtime (CLR) data access para liberar memória que foi alocado anteriormente no espaço de endereço do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="81c9e-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81c9e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81c9e-104">Syntax</span></span>  
  
```  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81c9e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="81c9e-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="81c9e-106">[in] Um `CLRDATA_ADDRESS` valor que especifica o endereço inicial da memória a ser liberado.</span><span class="sxs-lookup"><span data-stu-id="81c9e-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="81c9e-107">[in] O tamanho, em bytes, da memória a ser liberado.</span><span class="sxs-lookup"><span data-stu-id="81c9e-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="81c9e-108">[in] Sinalizadores que controlam a liberação de memória.</span><span class="sxs-lookup"><span data-stu-id="81c9e-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="81c9e-109">Consulte o Win32 `VirtualFree` função.</span><span class="sxs-lookup"><span data-stu-id="81c9e-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81c9e-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="81c9e-110">Remarks</span></span>  
 <span data-ttu-id="81c9e-111">O `FreeVirtual` método serve como um wrapper de lógico do Win32 `VirtualFree` função.</span><span class="sxs-lookup"><span data-stu-id="81c9e-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="81c9e-112">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="81c9e-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81c9e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81c9e-113">Requirements</span></span>  
 <span data-ttu-id="81c9e-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81c9e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81c9e-115">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="81c9e-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="81c9e-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81c9e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81c9e-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81c9e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81c9e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81c9e-118">See also</span></span>
- [<span data-ttu-id="81c9e-119">Interface ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="81c9e-119">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="81c9e-120">Método AllocVirtual</span><span class="sxs-lookup"><span data-stu-id="81c9e-120">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
