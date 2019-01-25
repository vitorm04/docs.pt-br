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
ms.openlocfilehash: b10ec088f087c45b8a75805e326bc543bb64b3d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665078"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="47113-102">Método ICorRuntimeHost::GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="47113-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="47113-103">Obtém um objeto que permite que o host especificar a configuração de retorno de chamada do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="47113-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47113-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47113-104">Syntax</span></span>  
  
```  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47113-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="47113-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="47113-106">[out] Um ponteiro para o endereço de um [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) objeto que pode ser usado para configurar o CLR.</span><span class="sxs-lookup"><span data-stu-id="47113-106">[out] A pointer to the address of an [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47113-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="47113-107">Remarks</span></span>  
 <span data-ttu-id="47113-108">O CLR deve ser configurado antes da inicialização; Caso contrário, o `GetConfiguration` método retorna um HRESULT indicando um erro.</span><span class="sxs-lookup"><span data-stu-id="47113-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47113-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="47113-109">Requirements</span></span>  
 <span data-ttu-id="47113-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47113-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47113-111">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="47113-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="47113-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="47113-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47113-113">**Versões do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="47113-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47113-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47113-114">See also</span></span>
- [<span data-ttu-id="47113-115">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="47113-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
