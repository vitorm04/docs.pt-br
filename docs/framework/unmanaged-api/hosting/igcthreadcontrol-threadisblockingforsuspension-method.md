---
title: Método IGCThreadControl::ThreadIsBlockingForSuspension
ms.date: 03/30/2017
api_name:
- IGCThreadControl.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type:
- apiref
ms.openlocfilehash: e6534c3085b70b590c2dcc3f50cf0253bd5e6682
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134749"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="adfdf-102">Método IGCThreadControl::ThreadIsBlockingForSuspension</span><span class="sxs-lookup"><span data-stu-id="adfdf-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="adfdf-103">Notifica o host que o thread que está fazendo a chamada está prestes a bloquear, talvez para uma coleta de lixo ou outra suspensão.</span><span class="sxs-lookup"><span data-stu-id="adfdf-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adfdf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="adfdf-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="adfdf-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="adfdf-105">Remarks</span></span>  
 <span data-ttu-id="adfdf-106">O host pode escolher dentro do `ThreadIsBlockingForSuspension` retorno de chamada se for reagendado um thread.</span><span class="sxs-lookup"><span data-stu-id="adfdf-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adfdf-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="adfdf-107">Requirements</span></span>  
 <span data-ttu-id="adfdf-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adfdf-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adfdf-109">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="adfdf-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="adfdf-110">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="adfdf-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="adfdf-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adfdf-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adfdf-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="adfdf-112">See also</span></span>

- [<span data-ttu-id="adfdf-113">Interface IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="adfdf-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
