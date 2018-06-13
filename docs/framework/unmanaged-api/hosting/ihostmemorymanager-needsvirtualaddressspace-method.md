---
title: Método IHostMemoryManager::NeedsVirtualAddressSpace
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.NeedsVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87c97a678fce4c25a113670a4668515a898e5251
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438412"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="de7d6-102">Método IHostMemoryManager::NeedsVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="de7d6-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="de7d6-103">Notifica o host que o common language runtime (CLR) vai tentar usar a memória especificada.</span><span class="sxs-lookup"><span data-stu-id="de7d6-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de7d6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de7d6-104">Syntax</span></span>  
  
```  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de7d6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="de7d6-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="de7d6-106">[in] O endereço inicial da memória.</span><span class="sxs-lookup"><span data-stu-id="de7d6-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="de7d6-107">[in] O tamanho, em bytes, da memória.</span><span class="sxs-lookup"><span data-stu-id="de7d6-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de7d6-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="de7d6-108">Remarks</span></span>  
 <span data-ttu-id="de7d6-109">O `NeedsVirtualAddressSpace` é um método de retorno de chamada de método e deve ser implementado pelo gerador de aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="de7d6-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="de7d6-110">Ele é chamado pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="de7d6-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="de7d6-111">Se o host não quer que o CLR para usar a memória especificada, ela pode retornar um HRESULT E_OUTOFMEMORY.</span><span class="sxs-lookup"><span data-stu-id="de7d6-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de7d6-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="de7d6-112">Requirements</span></span>  
 <span data-ttu-id="de7d6-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de7d6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de7d6-114">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="de7d6-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="de7d6-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="de7d6-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de7d6-116">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de7d6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de7d6-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de7d6-117">See Also</span></span>  
 [<span data-ttu-id="de7d6-118">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="de7d6-118">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
