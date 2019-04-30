---
title: Método ICLRAssemblyIdentityManager::IsStronglyNamed
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.IsStronglyNamed
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::IsStronglyNamed
helpviewer_keywords:
- IsStronglyNamed method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::IsStronglyNamed method [.NET Framework hosting]
ms.assetid: 954bd386-2076-4d00-9d46-38c728aa9cab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 166583f690fc7ed80f80cf2cf5cd5b0348708cc3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970151"
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="5c84e-102">Método ICLRAssemblyIdentityManager::IsStronglyNamed</span><span class="sxs-lookup"><span data-stu-id="5c84e-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>
<span data-ttu-id="5c84e-103">Obtém um valor que indica se o assembly especificado forte.</span><span class="sxs-lookup"><span data-stu-id="5c84e-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c84e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c84e-104">Syntax</span></span>  
  
```  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c84e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5c84e-105">Parameters</span></span>  
 `pwzAssemblyIdentity`  
 <span data-ttu-id="5c84e-106">[in] Os dados de identidade do assembly canônicos opacas do assembly a ser avaliada.</span><span class="sxs-lookup"><span data-stu-id="5c84e-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="5c84e-107">[out] `true`, se o assembly referenciado pela `pwzAssemblyIdentity` parâmetro é fortemente nomeado; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="5c84e-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c84e-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5c84e-108">Return Value</span></span>  
  
|<span data-ttu-id="5c84e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c84e-109">HRESULT</span></span>|<span data-ttu-id="5c84e-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c84e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c84e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c84e-111">S_OK</span></span>|<span data-ttu-id="5c84e-112">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="5c84e-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="5c84e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5c84e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5c84e-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="5c84e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5c84e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5c84e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5c84e-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="5c84e-116">The call timed out.</span></span>|  
|<span data-ttu-id="5c84e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5c84e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5c84e-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="5c84e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5c84e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5c84e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5c84e-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="5c84e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5c84e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5c84e-121">E_FAIL</span></span>|<span data-ttu-id="5c84e-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="5c84e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5c84e-123">Se um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="5c84e-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5c84e-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5c84e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5c84e-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5c84e-125">Requirements</span></span>  
 <span data-ttu-id="5c84e-126">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c84e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c84e-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5c84e-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c84e-128">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5c84e-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c84e-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c84e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c84e-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c84e-130">See also</span></span>

- [<span data-ttu-id="5c84e-131">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="5c84e-131">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
