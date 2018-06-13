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
ms.openlocfilehash: 48c2a394126aca3a10b38ab2ba2df945f53e45d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438266"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="fd309-102">Método ICorConfiguration::SetGCHostControl</span><span class="sxs-lookup"><span data-stu-id="fd309-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="fd309-103">Define a interface de retorno de chamada a ser usado pelo coletor de lixo para solicitar o host para alterar os limites de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="fd309-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd309-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fd309-104">Syntax</span></span>  
  
```  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd309-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fd309-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="fd309-106">[in] Um ponteiro para um [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) objeto que permite que o coletor de lixo solicitar o host para alterar os limites de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="fd309-106">[in] A pointer to an [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd309-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fd309-107">Requirements</span></span>  
 <span data-ttu-id="fd309-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd309-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd309-109">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fd309-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd309-110">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="fd309-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd309-111">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd309-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd309-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd309-112">See Also</span></span>  
 [<span data-ttu-id="fd309-113">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="fd309-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
