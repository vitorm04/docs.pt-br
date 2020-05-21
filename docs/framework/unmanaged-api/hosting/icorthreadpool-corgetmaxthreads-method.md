---
title: Método ICorThreadpool::CorGetMaxThreads
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetMaxThreads
helpviewer_keywords:
- CorGetMaxThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetMaxThreads method [.NET Framework hosting]
ms.assetid: 2861533a-cda0-47b3-b716-0d363505289b
topic_type:
- apiref
ms.openlocfilehash: 46ffdb21c1f3b501cc28afffc224349887af5644
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762741"
---
# <a name="icorthreadpoolcorgetmaxthreads-method"></a><span data-ttu-id="bc855-102">Método ICorThreadpool::CorGetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="bc855-102">ICorThreadpool::CorGetMaxThreads Method</span></span>
<span data-ttu-id="bc855-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="bc855-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc855-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bc855-104">Syntax</span></span>  
  
```cpp  
HRESULT CorGetMaxThreads (  
    [out] DWORD *MaxWorkerThreads,  
    [out] DWORD *MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="bc855-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bc855-105">Requirements</span></span>  
 <span data-ttu-id="bc855-106">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc855-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc855-107">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bc855-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bc855-108">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bc855-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc855-109">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc855-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc855-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="bc855-110">See also</span></span>

- [<span data-ttu-id="bc855-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="bc855-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
