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
ms.openlocfilehash: c084a3fcbbc02504124a511c6e136be32f408d21
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73112320"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="165bf-102">Método ICLRDataTarget2::FreeVirtual</span><span class="sxs-lookup"><span data-stu-id="165bf-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="165bf-103">Chamado pelos serviços de acesso a dados do Common Language Runtime (CLR) para liberar memória que foi alocada anteriormente no espaço de endereço do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="165bf-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="165bf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="165bf-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="165bf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="165bf-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="165bf-106">no Um valor `CLRDATA_ADDRESS` que especifica o endereço inicial da memória a ser liberada.</span><span class="sxs-lookup"><span data-stu-id="165bf-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="165bf-107">no O tamanho, em bytes, da memória a ser liberada.</span><span class="sxs-lookup"><span data-stu-id="165bf-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="165bf-108">no Sinalizadores que controlam a liberação de memória.</span><span class="sxs-lookup"><span data-stu-id="165bf-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="165bf-109">Consulte a função de `VirtualFree` do Win32.</span><span class="sxs-lookup"><span data-stu-id="165bf-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="165bf-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="165bf-110">Remarks</span></span>  
 <span data-ttu-id="165bf-111">O método `FreeVirtual` serve como um wrapper lógico para a função de `VirtualFree` do Win32.</span><span class="sxs-lookup"><span data-stu-id="165bf-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="165bf-112">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="165bf-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="165bf-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="165bf-113">Requirements</span></span>  
 <span data-ttu-id="165bf-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="165bf-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="165bf-115">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="165bf-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="165bf-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="165bf-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="165bf-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="165bf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="165bf-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="165bf-118">See also</span></span>

- [<span data-ttu-id="165bf-119">Interface ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="165bf-119">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="165bf-120">Método AllocVirtual</span><span class="sxs-lookup"><span data-stu-id="165bf-120">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
