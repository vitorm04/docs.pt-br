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
ms.openlocfilehash: e18172ecf2d4300ae42cc42ecdb1783744cac105
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490425"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="686f7-102">Função GetCLRIdentityManager</span><span class="sxs-lookup"><span data-stu-id="686f7-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="686f7-103">Obtém um ponteiro para uma interface que permite que o common language runtime (CLR) para gerenciar identidades.</span><span class="sxs-lookup"><span data-stu-id="686f7-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="686f7-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="686f7-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="686f7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="686f7-105">Syntax</span></span>  
  
```  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="686f7-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="686f7-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="686f7-107">[in] Um `REFIID` (um identificador de interface) que especifica qual interface para obter.</span><span class="sxs-lookup"><span data-stu-id="686f7-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="686f7-108">Esse valor deve ser IID_ICLRAssemblyIdentityManager ou IID_ICLRHostBindingPolicyManager.</span><span class="sxs-lookup"><span data-stu-id="686f7-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="686f7-109">[out] Um ponteiro para o endereço de um uma [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) ou um [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="686f7-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="686f7-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="686f7-110">Remarks</span></span>  
 <span data-ttu-id="686f7-111">Chame o [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) função para obter um ponteiro para o `GetCLRIdentityManager` função.</span><span class="sxs-lookup"><span data-stu-id="686f7-111">Call the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="686f7-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="686f7-112">Requirements</span></span>  
 <span data-ttu-id="686f7-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="686f7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="686f7-114">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="686f7-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="686f7-115">**Biblioteca:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="686f7-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="686f7-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="686f7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="686f7-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="686f7-117">See also</span></span>

- [<span data-ttu-id="686f7-118">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="686f7-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
