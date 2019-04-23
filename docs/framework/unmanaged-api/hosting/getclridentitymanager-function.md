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
ms.openlocfilehash: 84f71266d84cc98c2a5deb4aa8639e36808315a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130176"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="1035a-102">Função GetCLRIdentityManager</span><span class="sxs-lookup"><span data-stu-id="1035a-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="1035a-103">Obtém um ponteiro para uma interface que permite que o common language runtime (CLR) para gerenciar identidades.</span><span class="sxs-lookup"><span data-stu-id="1035a-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="1035a-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1035a-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1035a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1035a-105">Syntax</span></span>  
  
```  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1035a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1035a-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="1035a-107">[in] Um `REFIID` (um identificador de interface) que especifica qual interface para obter.</span><span class="sxs-lookup"><span data-stu-id="1035a-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="1035a-108">Esse valor deve ser IID_ICLRAssemblyIdentityManager ou IID_ICLRHostBindingPolicyManager.</span><span class="sxs-lookup"><span data-stu-id="1035a-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="1035a-109">[out] Um ponteiro para o endereço de um uma [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) ou um [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="1035a-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1035a-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="1035a-110">Remarks</span></span>  
 <span data-ttu-id="1035a-111">Chame o [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) função para obter um ponteiro para o `GetCLRIdentityManager` função.</span><span class="sxs-lookup"><span data-stu-id="1035a-111">Call the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1035a-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1035a-112">Requirements</span></span>  
 <span data-ttu-id="1035a-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1035a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1035a-114">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1035a-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1035a-115">**Biblioteca:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="1035a-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="1035a-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1035a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1035a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1035a-117">See also</span></span>

- [<span data-ttu-id="1035a-118">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="1035a-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
