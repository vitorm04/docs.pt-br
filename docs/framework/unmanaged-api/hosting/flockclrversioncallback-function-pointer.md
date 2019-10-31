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
ms.openlocfilehash: f1ad414c30788801e14a33e98a0893e2a0f58d0c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136512"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="f5a70-102">Ponteiro de função FLockClrVersionCallback</span><span class="sxs-lookup"><span data-stu-id="f5a70-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="f5a70-103">Aponta para uma função que o Common Language Runtime (CLR) chama para indicar que a inicialização foi iniciada ou concluída.</span><span class="sxs-lookup"><span data-stu-id="f5a70-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="f5a70-104">Esse ponteiro de função foi preterido no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f5a70-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5a70-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5a70-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="f5a70-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="f5a70-106">Remarks</span></span>  
 <span data-ttu-id="f5a70-107">Essa função é implementada pelo host.</span><span class="sxs-lookup"><span data-stu-id="f5a70-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5a70-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f5a70-108">Requirements</span></span>  
 <span data-ttu-id="f5a70-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5a70-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5a70-110">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f5a70-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5a70-111">**Biblioteca:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="f5a70-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="f5a70-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5a70-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5a70-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5a70-113">See also</span></span>

- [<span data-ttu-id="f5a70-114">Função LockClrVersion</span><span class="sxs-lookup"><span data-stu-id="f5a70-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [<span data-ttu-id="f5a70-115">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="f5a70-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
