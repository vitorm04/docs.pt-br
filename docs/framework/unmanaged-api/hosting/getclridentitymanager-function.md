---
title: Função GetCLRIdentityManager
ms.date: 03/30/2017
api_name:
- GetCLRIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetCLRIdentityManager
helpviewer_keywords:
- GetCLRIdentityManager function [.NET Framework hosting]
ms.assetid: 66eeca30-adb4-45f4-aff5-347564c95724
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a0672196ebaea5c91139851b89a7476ff6363b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="9246c-102">Função GetCLRIdentityManager</span><span class="sxs-lookup"><span data-stu-id="9246c-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="9246c-103">Obtém um ponteiro para uma interface que permite que o common language runtime (CLR) para gerenciar identidades.</span><span class="sxs-lookup"><span data-stu-id="9246c-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="9246c-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9246c-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9246c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9246c-105">Syntax</span></span>  
  
```  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9246c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9246c-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="9246c-107">[in] Um `REFIID` (um identificador de interface) que especifica qual interface para obter.</span><span class="sxs-lookup"><span data-stu-id="9246c-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="9246c-108">Esse valor deve ser IID_ICLRAssemblyIdentityManager ou IID_ICLRHostBindingPolicyManager.</span><span class="sxs-lookup"><span data-stu-id="9246c-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="9246c-109">[out] Um ponteiro para o endereço de um [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) ou um [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="9246c-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9246c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="9246c-110">Remarks</span></span>  
 <span data-ttu-id="9246c-111">Chamar o [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) função para obter um ponteiro para o `GetCLRIdentityManager` função.</span><span class="sxs-lookup"><span data-stu-id="9246c-111">Call the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9246c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9246c-112">Requirements</span></span>  
 <span data-ttu-id="9246c-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9246c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9246c-114">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9246c-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9246c-115">**Biblioteca:** arquivo MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="9246c-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="9246c-116">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9246c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9246c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9246c-117">See Also</span></span>  
 [<span data-ttu-id="9246c-118">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="9246c-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
