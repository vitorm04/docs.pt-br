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
ms.openlocfilehash: 20b73549d30fe210e4d44902d2f459ea9c682360
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860484"
---
# <a name="iclrdatatarget2allocvirtual-method"></a><span data-ttu-id="da4e0-102">Método ICLRDataTarget2::AllocVirtual</span><span class="sxs-lookup"><span data-stu-id="da4e0-102">ICLRDataTarget2::AllocVirtual Method</span></span>
<span data-ttu-id="da4e0-103">Chamado pelos serviços de acesso a dados do Common Language Runtime (CLR) para alocar memória no espaço de endereço desse processo de destino.</span><span class="sxs-lookup"><span data-stu-id="da4e0-103">Called by the common language runtime (CLR) data access services to allocate memory in the address space of this target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da4e0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da4e0-104">Syntax</span></span>  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da4e0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="da4e0-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="da4e0-106">no Um `CLRDATA_ADDRESS` valor que especifica o endereço inicial solicitado da memória a ser alocada.</span><span class="sxs-lookup"><span data-stu-id="da4e0-106">[in] A `CLRDATA_ADDRESS` value that specifies the requested starting address of the memory to be allocated.</span></span>  
  
 `size`  
 <span data-ttu-id="da4e0-107">no O tamanho, em bytes, da memória a ser alocada.</span><span class="sxs-lookup"><span data-stu-id="da4e0-107">[in] The size, in bytes, of the memory to be allocated.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="da4e0-108">no Sinalizadores que controlam a alocação de memória.</span><span class="sxs-lookup"><span data-stu-id="da4e0-108">[in] Flags that control the allocation of memory.</span></span> <span data-ttu-id="da4e0-109">Consulte a função `VirtualAlloc` do Win32.</span><span class="sxs-lookup"><span data-stu-id="da4e0-109">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `protectFlags`  
 <span data-ttu-id="da4e0-110">no Os atributos de proteção para a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="da4e0-110">[in] The protection attributes for the allocated memory.</span></span> <span data-ttu-id="da4e0-111">Consulte a função `VirtualAlloc` do Win32.</span><span class="sxs-lookup"><span data-stu-id="da4e0-111">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `virt`  
 <span data-ttu-id="da4e0-112">fora Um ponteiro para um `CLRDATA_ADDRESS` valor que especifica o endereço inicial real da memória alocada.</span><span class="sxs-lookup"><span data-stu-id="da4e0-112">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the actual starting address of the allocated memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da4e0-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="da4e0-113">Remarks</span></span>  
 <span data-ttu-id="da4e0-114">O `AllocVirtual` método serve como um wrapper lógico para a função `VirtualAlloc` do Win32.</span><span class="sxs-lookup"><span data-stu-id="da4e0-114">The `AllocVirtual` method serves as a logical wrapper for the Win32 `VirtualAlloc` function.</span></span>  
  
 <span data-ttu-id="da4e0-115">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="da4e0-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da4e0-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da4e0-116">Requirements</span></span>  
 <span data-ttu-id="da4e0-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da4e0-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da4e0-118">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="da4e0-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="da4e0-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da4e0-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da4e0-120">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da4e0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da4e0-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="da4e0-121">See also</span></span>

- [<span data-ttu-id="da4e0-122">Interface ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="da4e0-122">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="da4e0-123">Método FreeVirtual</span><span class="sxs-lookup"><span data-stu-id="da4e0-123">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)
