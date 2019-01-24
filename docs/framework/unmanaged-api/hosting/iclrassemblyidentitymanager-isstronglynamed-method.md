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
ms.openlocfilehash: a958e38857d2407930cb8c03a08eabdf6574cda9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563880"
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="26aa5-102">Método ICLRAssemblyIdentityManager::IsStronglyNamed</span><span class="sxs-lookup"><span data-stu-id="26aa5-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>
<span data-ttu-id="26aa5-103">Obtém um valor que indica se o assembly especificado forte.</span><span class="sxs-lookup"><span data-stu-id="26aa5-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26aa5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26aa5-104">Syntax</span></span>  
  
```  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26aa5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="26aa5-105">Parameters</span></span>  
 `pwzAssemblyIdentity`  
 <span data-ttu-id="26aa5-106">[in] Os dados de identidade do assembly canônicos opacas do assembly a ser avaliada.</span><span class="sxs-lookup"><span data-stu-id="26aa5-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="26aa5-107">[out] `true`, se o assembly referenciado pela `pwzAssemblyIdentity` parâmetro é fortemente nomeado; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="26aa5-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26aa5-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="26aa5-108">Return Value</span></span>  
  
|<span data-ttu-id="26aa5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="26aa5-109">HRESULT</span></span>|<span data-ttu-id="26aa5-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="26aa5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="26aa5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="26aa5-111">S_OK</span></span>|<span data-ttu-id="26aa5-112">O método é retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="26aa5-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="26aa5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="26aa5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="26aa5-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="26aa5-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="26aa5-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="26aa5-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="26aa5-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="26aa5-116">The call timed out.</span></span>|  
|<span data-ttu-id="26aa5-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="26aa5-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="26aa5-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="26aa5-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="26aa5-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="26aa5-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="26aa5-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="26aa5-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="26aa5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="26aa5-121">E_FAIL</span></span>|<span data-ttu-id="26aa5-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="26aa5-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="26aa5-123">Se um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="26aa5-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="26aa5-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="26aa5-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="26aa5-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26aa5-125">Requirements</span></span>  
 <span data-ttu-id="26aa5-126">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26aa5-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26aa5-127">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="26aa5-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26aa5-128">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="26aa5-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26aa5-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26aa5-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26aa5-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26aa5-130">See also</span></span>
- [<span data-ttu-id="26aa5-131">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="26aa5-131">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
