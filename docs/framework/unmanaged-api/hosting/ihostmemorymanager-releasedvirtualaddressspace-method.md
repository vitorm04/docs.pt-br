---
title: Método IHostMemoryManager::ReleasedVirtualAddressSpace
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.ReleasedVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::ReleasedVirtualAddressSpace
helpviewer_keywords:
- ReleasedVirtualAddressSpace method [.NET Framework hosting]
- IHostMemoryManager::ReleasedVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: d1876601-6ab9-48e1-8ebd-184af1d0cd76
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0acbf4163e98b1171510260c4fac72c3d6f6fb1d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189281"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="17ce2-102">Método IHostMemoryManager::ReleasedVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="17ce2-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="17ce2-103">Notifica o host que o common language runtime (CLR) foi concluída usando a memória especificada.</span><span class="sxs-lookup"><span data-stu-id="17ce2-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17ce2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17ce2-104">Syntax</span></span>  
  
```  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17ce2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="17ce2-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="17ce2-106">[in] Ponteiro para o endereço inicial da memória para ser liberado.</span><span class="sxs-lookup"><span data-stu-id="17ce2-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17ce2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="17ce2-107">Remarks</span></span>  
 <span data-ttu-id="17ce2-108">O `ReleasedVirtualAddressSpace` é um método de retorno de chamada de método e deve ser implementado pelo gravador do aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="17ce2-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="17ce2-109">Ele é chamado pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="17ce2-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17ce2-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="17ce2-110">Requirements</span></span>  
 <span data-ttu-id="17ce2-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17ce2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17ce2-112">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="17ce2-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17ce2-113">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="17ce2-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17ce2-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17ce2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17ce2-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17ce2-115">See also</span></span>

- [<span data-ttu-id="17ce2-116">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="17ce2-116">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
