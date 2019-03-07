---
title: Método ICLRDataTarget2::AllocVirtual
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.AllocVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1e63b6a015bd1ffa86d8fd04b0154dbade85a35
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465914"
---
# <a name="iclrdatatarget2allocvirtual-method"></a><span data-ttu-id="7b4d7-102">Método ICLRDataTarget2::AllocVirtual</span><span class="sxs-lookup"><span data-stu-id="7b4d7-102">ICLRDataTarget2::AllocVirtual Method</span></span>
<span data-ttu-id="7b4d7-103">Chamado pelo common language runtime (CLR) dados serviço de acesso para alocar memória no espaço de endereço desse processo de destino.</span><span class="sxs-lookup"><span data-stu-id="7b4d7-103">Called by the common language runtime (CLR) data access services to allocate memory in the address space of this target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b4d7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b4d7-104">Syntax</span></span>  
  
```  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b4d7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7b4d7-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="7b4d7-106">[in] Um `CLRDATA_ADDRESS` valor que especifica o endereço inicial solicitado da memória a ser alocado.</span><span class="sxs-lookup"><span data-stu-id="7b4d7-106">[in] A `CLRDATA_ADDRESS` value that specifies the requested starting address of the memory to be allocated.</span></span>  
  
 `size`  
 <span data-ttu-id="7b4d7-107">[in] O tamanho, em bytes, da memória a ser alocado.</span><span class="sxs-lookup"><span data-stu-id="7b4d7-107">[in] The size, in bytes, of the memory to be allocated.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="7b4d7-108">[in] Sinalizadores que controlam a alocação de memória.</span><span class="sxs-lookup"><span data-stu-id="7b4d7-108">[in] Flags that control the allocation of memory.</span></span> <span data-ttu-id="7b4d7-109">Consulte o Win32 `VirtualAlloc` função.</span><span class="sxs-lookup"><span data-stu-id="7b4d7-109">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `protectFlags`  
 <span data-ttu-id="7b4d7-110">[in] Os atributos de proteção para a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="7b4d7-110">[in] The protection attributes for the allocated memory.</span></span> <span data-ttu-id="7b4d7-111">Consulte o Win32 `VirtualAlloc` função.</span><span class="sxs-lookup"><span data-stu-id="7b4d7-111">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `virt`  
 <span data-ttu-id="7b4d7-112">[out] Um ponteiro para um `CLRDATA_ADDRESS` valor que especifica o endereço inicial real da memória alocada.</span><span class="sxs-lookup"><span data-stu-id="7b4d7-112">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the actual starting address of the allocated memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b4d7-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="7b4d7-113">Remarks</span></span>  
 <span data-ttu-id="7b4d7-114">O `AllocVirtual` método serve como um wrapper de lógico do Win32 `VirtualAlloc` função.</span><span class="sxs-lookup"><span data-stu-id="7b4d7-114">The `AllocVirtual` method serves as a logical wrapper for the Win32 `VirtualAlloc` function.</span></span>  
  
 <span data-ttu-id="7b4d7-115">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="7b4d7-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b4d7-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7b4d7-116">Requirements</span></span>  
 <span data-ttu-id="7b4d7-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b4d7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b4d7-118">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="7b4d7-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7b4d7-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b4d7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b4d7-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b4d7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b4d7-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b4d7-121">See also</span></span>
- [<span data-ttu-id="7b4d7-122">Interface ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="7b4d7-122">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="7b4d7-123">Método FreeVirtual</span><span class="sxs-lookup"><span data-stu-id="7b4d7-123">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)
