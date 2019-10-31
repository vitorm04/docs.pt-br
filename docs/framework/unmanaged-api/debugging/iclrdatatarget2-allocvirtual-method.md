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
ms.openlocfilehash: 7640f7fafd0bf52a302ac0da1e5df39b5da22d68
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091155"
---
# <a name="iclrdatatarget2allocvirtual-method"></a><span data-ttu-id="e5f17-102">Método ICLRDataTarget2::AllocVirtual</span><span class="sxs-lookup"><span data-stu-id="e5f17-102">ICLRDataTarget2::AllocVirtual Method</span></span>
<span data-ttu-id="e5f17-103">Chamado pelos serviços de acesso a dados do Common Language Runtime (CLR) para alocar memória no espaço de endereço desse processo de destino.</span><span class="sxs-lookup"><span data-stu-id="e5f17-103">Called by the common language runtime (CLR) data access services to allocate memory in the address space of this target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5f17-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5f17-104">Syntax</span></span>  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5f17-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e5f17-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="e5f17-106">no Um valor `CLRDATA_ADDRESS` que especifica o endereço inicial solicitado da memória a ser alocada.</span><span class="sxs-lookup"><span data-stu-id="e5f17-106">[in] A `CLRDATA_ADDRESS` value that specifies the requested starting address of the memory to be allocated.</span></span>  
  
 `size`  
 <span data-ttu-id="e5f17-107">no O tamanho, em bytes, da memória a ser alocada.</span><span class="sxs-lookup"><span data-stu-id="e5f17-107">[in] The size, in bytes, of the memory to be allocated.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="e5f17-108">no Sinalizadores que controlam a alocação de memória.</span><span class="sxs-lookup"><span data-stu-id="e5f17-108">[in] Flags that control the allocation of memory.</span></span> <span data-ttu-id="e5f17-109">Consulte a função de `VirtualAlloc` do Win32.</span><span class="sxs-lookup"><span data-stu-id="e5f17-109">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `protectFlags`  
 <span data-ttu-id="e5f17-110">no Os atributos de proteção para a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="e5f17-110">[in] The protection attributes for the allocated memory.</span></span> <span data-ttu-id="e5f17-111">Consulte a função de `VirtualAlloc` do Win32.</span><span class="sxs-lookup"><span data-stu-id="e5f17-111">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `virt`  
 <span data-ttu-id="e5f17-112">fora Um ponteiro para um valor `CLRDATA_ADDRESS` que especifica o endereço inicial real da memória alocada.</span><span class="sxs-lookup"><span data-stu-id="e5f17-112">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the actual starting address of the allocated memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5f17-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="e5f17-113">Remarks</span></span>  
 <span data-ttu-id="e5f17-114">O método `AllocVirtual` serve como um wrapper lógico para a função de `VirtualAlloc` do Win32.</span><span class="sxs-lookup"><span data-stu-id="e5f17-114">The `AllocVirtual` method serves as a logical wrapper for the Win32 `VirtualAlloc` function.</span></span>  
  
 <span data-ttu-id="e5f17-115">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="e5f17-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5f17-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e5f17-116">Requirements</span></span>  
 <span data-ttu-id="e5f17-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5f17-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5f17-118">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="e5f17-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e5f17-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5f17-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5f17-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5f17-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5f17-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5f17-121">See also</span></span>

- [<span data-ttu-id="e5f17-122">Interface ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="e5f17-122">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="e5f17-123">Método FreeVirtual</span><span class="sxs-lookup"><span data-stu-id="e5f17-123">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)
