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
ms.openlocfilehash: 5096eb1064485c02b599659cc9ae889e7151581c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767692"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="fcc67-102">Método IHostMemoryManager::ReleasedVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="fcc67-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="fcc67-103">Notifica o host que o common language runtime (CLR) foi concluída usando a memória especificada.</span><span class="sxs-lookup"><span data-stu-id="fcc67-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcc67-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fcc67-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcc67-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fcc67-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="fcc67-106">[in] Ponteiro para o endereço inicial da memória para ser liberado.</span><span class="sxs-lookup"><span data-stu-id="fcc67-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcc67-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="fcc67-107">Remarks</span></span>  
 <span data-ttu-id="fcc67-108">O `ReleasedVirtualAddressSpace` é um método de retorno de chamada de método e deve ser implementado pelo gravador do aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="fcc67-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="fcc67-109">Ele é chamado pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="fcc67-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcc67-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fcc67-110">Requirements</span></span>  
 <span data-ttu-id="fcc67-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcc67-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcc67-112">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fcc67-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fcc67-113">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="fcc67-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fcc67-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcc67-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcc67-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fcc67-115">See also</span></span>

- [<span data-ttu-id="fcc67-116">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="fcc67-116">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
