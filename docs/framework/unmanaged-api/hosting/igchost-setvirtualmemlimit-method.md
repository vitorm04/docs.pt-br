---
title: Método IGCHost::SetVirtualMemLimit
ms.date: 03/30/2017
api_name:
- IGCHost.SetVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetVirtualMemLimit
helpviewer_keywords:
- IGCHost::SetVirtualMemLimit method [.NET Framework hosting]
- SetVirtualMemLimit method [.NET Framework hosting]
ms.assetid: c7e7c2d0-e58c-4650-b40c-47b2be2cda45
topic_type:
- apiref
ms.openlocfilehash: 93ed63b4abacce1d8943434965aacf67190631b6
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805195"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="250ce-102">Método IGCHost::SetVirtualMemLimit</span><span class="sxs-lookup"><span data-stu-id="250ce-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="250ce-103">Define o tamanho máximo da memória virtual do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="250ce-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="250ce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="250ce-104">Syntax</span></span>  
  
```cpp  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="250ce-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="250ce-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="250ce-106">no O tamanho máximo, em megabytes, da memória virtual do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="250ce-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="250ce-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="250ce-107">Remarks</span></span>  
 <span data-ttu-id="250ce-108">O tamanho máximo da memória virtual do tempo de execução pode ser alterado dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="250ce-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="250ce-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="250ce-109">Requirements</span></span>  
 <span data-ttu-id="250ce-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="250ce-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="250ce-111">**Cabeçalho:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="250ce-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="250ce-112">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="250ce-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="250ce-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="250ce-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="250ce-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="250ce-114">See also</span></span>

- [<span data-ttu-id="250ce-115">Interface IGCHost</span><span class="sxs-lookup"><span data-stu-id="250ce-115">IGCHost Interface</span></span>](igchost-interface.md)
