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
ms.openlocfilehash: 87549118742da797ef0dd1b08ae9e72c466f7841
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139571"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="e25ae-102">Método ICorRuntimeHost::GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="e25ae-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="e25ae-103">Obtém um objeto que permite ao host especificar a configuração de retorno de chamada do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="e25ae-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e25ae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e25ae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e25ae-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e25ae-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="e25ae-106">fora Um ponteiro para o endereço de um objeto [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) que pode ser usado para configurar o CLR.</span><span class="sxs-lookup"><span data-stu-id="e25ae-106">[out] A pointer to the address of an [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e25ae-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e25ae-107">Remarks</span></span>  
 <span data-ttu-id="e25ae-108">O CLR deve ser configurado antes de sua inicialização; caso contrário, o método `GetConfiguration` retornará um HRESULT indicando um erro.</span><span class="sxs-lookup"><span data-stu-id="e25ae-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e25ae-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e25ae-109">Requirements</span></span>  
 <span data-ttu-id="e25ae-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e25ae-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e25ae-111">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e25ae-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e25ae-112">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e25ae-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e25ae-113">**Versões do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="e25ae-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e25ae-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e25ae-114">See also</span></span>

- [<span data-ttu-id="e25ae-115">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="e25ae-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
