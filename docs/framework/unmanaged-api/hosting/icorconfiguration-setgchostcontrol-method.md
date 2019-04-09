---
title: Método ICorConfiguration::SetGCHostControl
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCHostControl
helpviewer_keywords:
- ICorConfiguration::SetGCHostControl method [.NET Framework hosting]
- SetGCHostControl method [.NET Framework hosting]
ms.assetid: bca6bd79-e288-475a-aa46-6bf81541d966
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50a92058e8a394b95c690d19f1bafdddbed8246a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135987"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="0bccc-102">Método ICorConfiguration::SetGCHostControl</span><span class="sxs-lookup"><span data-stu-id="0bccc-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="0bccc-103">Define a interface de retorno de chamada a ser usado pelo coletor de lixo para solicitar o host para alterar os limites de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="0bccc-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bccc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0bccc-104">Syntax</span></span>  
  
```  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bccc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0bccc-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="0bccc-106">[in] Um ponteiro para um [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) objeto que permite que o coletor de lixo solicitar o host para alterar os limites de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="0bccc-106">[in] A pointer to an [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bccc-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0bccc-107">Requirements</span></span>  
 <span data-ttu-id="0bccc-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bccc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bccc-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0bccc-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0bccc-110">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0bccc-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="0bccc-111">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="0bccc-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0bccc-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0bccc-112">See also</span></span>

- [<span data-ttu-id="0bccc-113">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="0bccc-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
