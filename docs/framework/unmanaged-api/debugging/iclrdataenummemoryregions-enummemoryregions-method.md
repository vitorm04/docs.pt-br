---
title: Método ICLRDataEnumMemoryRegions::EnumMemoryRegions
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type:
- apiref
ms.openlocfilehash: e6cdc924df126e56d2e7c8c9cb8762ee88712fcc
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860694"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="15563-102">Método ICLRDataEnumMemoryRegions::EnumMemoryRegions</span><span class="sxs-lookup"><span data-stu-id="15563-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="15563-103">Enumera áreas especificadas de memória.</span><span class="sxs-lookup"><span data-stu-id="15563-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15563-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="15563-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15563-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="15563-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="15563-106">no Um ponteiro para uma instância de [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) que é chamada por esse método para cada região de memória que está sendo enumerada para notificar o depurador do resultado.</span><span class="sxs-lookup"><span data-stu-id="15563-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="15563-107">A enumeração de regiões de memória continua mesmo que o retorno de chamada indique uma falha.</span><span class="sxs-lookup"><span data-stu-id="15563-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="15563-108">no Não usado.</span><span class="sxs-lookup"><span data-stu-id="15563-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="15563-109">no Um valor da enumeração [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) que especifica as regiões de memória a serem enumeradas.</span><span class="sxs-lookup"><span data-stu-id="15563-109">[in] A value of the [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15563-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="15563-110">Remarks</span></span>  
 <span data-ttu-id="15563-111">Esse método usa a instância [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) especificada para notificar o chamador de resultados.</span><span class="sxs-lookup"><span data-stu-id="15563-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15563-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="15563-112">Requirements</span></span>  
 <span data-ttu-id="15563-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15563-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15563-114">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="15563-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="15563-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15563-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15563-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15563-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15563-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="15563-117">See also</span></span>

- [<span data-ttu-id="15563-118">Interface ICLRDataEnumMemoryRegions</span><span class="sxs-lookup"><span data-stu-id="15563-118">ICLRDataEnumMemoryRegions Interface</span></span>](iclrdataenummemoryregions-interface.md)
