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
ms.openlocfilehash: 8b1e918edf641d38dd6b91d790bcaff8020293a0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493260"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="15cf7-102">Função GetCLRIdentityManager</span><span class="sxs-lookup"><span data-stu-id="15cf7-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="15cf7-103">Obtém um ponteiro para uma interface que permite que o Common Language Runtime (CLR) gerencie identidades.</span><span class="sxs-lookup"><span data-stu-id="15cf7-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="15cf7-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="15cf7-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15cf7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="15cf7-105">Syntax</span></span>  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15cf7-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="15cf7-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="15cf7-107">no Um `REFIID` (um identificador de interface) que especifica qual interface deve ser obtida.</span><span class="sxs-lookup"><span data-stu-id="15cf7-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="15cf7-108">Esse valor deve ser IID_ICLRAssemblyIdentityManager ou IID_ICLRHostBindingPolicyManager.</span><span class="sxs-lookup"><span data-stu-id="15cf7-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="15cf7-109">fora Um ponteiro para o endereço de um objeto [ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md) ou [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="15cf7-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15cf7-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="15cf7-110">Remarks</span></span>  
 <span data-ttu-id="15cf7-111">Chame a função [GetRealProcAddress](getrealprocaddress-function.md) para obter um ponteiro para a `GetCLRIdentityManager` função.</span><span class="sxs-lookup"><span data-stu-id="15cf7-111">Call the [GetRealProcAddress](getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15cf7-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="15cf7-112">Requirements</span></span>  
 <span data-ttu-id="15cf7-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15cf7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15cf7-114">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="15cf7-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15cf7-115">**Biblioteca:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="15cf7-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="15cf7-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15cf7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15cf7-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="15cf7-117">See also</span></span>

- [<span data-ttu-id="15cf7-118">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="15cf7-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
