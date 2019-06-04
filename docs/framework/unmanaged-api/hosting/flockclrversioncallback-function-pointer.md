---
title: Ponteiro de função FLockClrVersionCallback
ms.date: 03/30/2017
api_name:
- FLockClrVersionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FLockClrVersionCallback
helpviewer_keywords:
- FLockClrVersionCallback function pointer [.NET Framework hosting]
ms.assetid: 98a4762d-9ad2-45bd-9d03-39064a028b44
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef308b624525c3a139c892e6118a24d6adb6e14a
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490454"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="320ec-102">Ponteiro de função FLockClrVersionCallback</span><span class="sxs-lookup"><span data-stu-id="320ec-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="320ec-103">Aponta para uma função que as chamadas de runtime (CLR) de linguagem comum para indicar que a inicialização foi iniciada ou concluída.</span><span class="sxs-lookup"><span data-stu-id="320ec-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="320ec-104">Esse ponteiro de função foi preterido no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="320ec-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="320ec-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="320ec-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="320ec-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="320ec-106">Remarks</span></span>  
 <span data-ttu-id="320ec-107">Essa função é implementada pelo host.</span><span class="sxs-lookup"><span data-stu-id="320ec-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="320ec-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="320ec-108">Requirements</span></span>  
 <span data-ttu-id="320ec-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="320ec-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="320ec-110">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="320ec-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="320ec-111">**Biblioteca:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="320ec-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="320ec-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="320ec-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="320ec-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="320ec-113">See also</span></span>

- [<span data-ttu-id="320ec-114">Função LockClrVersion</span><span class="sxs-lookup"><span data-stu-id="320ec-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [<span data-ttu-id="320ec-115">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="320ec-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
