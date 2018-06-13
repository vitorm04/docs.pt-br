---
title: Método ICorRuntimeHost::GetConfiguration
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c51ddae6aa62552bac9990b57a173c28f73bae5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436826"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="ed86a-102">Método ICorRuntimeHost::GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="ed86a-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="ed86a-103">Obtém um objeto que permite que o host especificar a configuração de retorno de chamada do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ed86a-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed86a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed86a-104">Syntax</span></span>  
  
```  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed86a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ed86a-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="ed86a-106">[out] Um ponteiro para o endereço de um [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) objeto que pode ser usado para configurar o CLR.</span><span class="sxs-lookup"><span data-stu-id="ed86a-106">[out] A pointer to the address of an [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed86a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ed86a-107">Remarks</span></span>  
 <span data-ttu-id="ed86a-108">O CLR deve ser configurado antes de sua inicialização; Caso contrário, o `GetConfiguration` método retorna um HRESULT indicando um erro.</span><span class="sxs-lookup"><span data-stu-id="ed86a-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed86a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ed86a-109">Requirements</span></span>  
 <span data-ttu-id="ed86a-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed86a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed86a-111">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ed86a-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ed86a-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ed86a-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed86a-113">**Versões do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="ed86a-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed86a-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed86a-114">See Also</span></span>  
 [<span data-ttu-id="ed86a-115">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="ed86a-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
