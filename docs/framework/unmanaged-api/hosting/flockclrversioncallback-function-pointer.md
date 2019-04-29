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
ms.openlocfilehash: 8062ab151efc6175aa68cb0563cd2ad042ee9cd8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61628009"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="a8d8f-102">Ponteiro de função FLockClrVersionCallback</span><span class="sxs-lookup"><span data-stu-id="a8d8f-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="a8d8f-103">Aponta para uma função que as chamadas de runtime (CLR) de linguagem comum para indicar que a inicialização foi iniciada ou concluída.</span><span class="sxs-lookup"><span data-stu-id="a8d8f-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="a8d8f-104">Esse ponteiro de função foi preterido no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a8d8f-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8d8f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8d8f-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="a8d8f-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8d8f-106">Remarks</span></span>  
 <span data-ttu-id="a8d8f-107">Essa função é implementada pelo host.</span><span class="sxs-lookup"><span data-stu-id="a8d8f-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8d8f-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a8d8f-108">Requirements</span></span>  
 <span data-ttu-id="a8d8f-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8d8f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8d8f-110">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a8d8f-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a8d8f-111">**Biblioteca:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="a8d8f-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="a8d8f-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8d8f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8d8f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8d8f-113">See also</span></span>

- [<span data-ttu-id="a8d8f-114">Função LockClrVersion</span><span class="sxs-lookup"><span data-stu-id="a8d8f-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [<span data-ttu-id="a8d8f-115">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="a8d8f-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
