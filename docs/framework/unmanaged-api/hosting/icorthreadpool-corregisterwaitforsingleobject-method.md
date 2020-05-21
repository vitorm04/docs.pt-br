---
title: Método ICorThreadpool::CorRegisterWaitForSingleObject
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorRegisterWaitForSingleObject
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRegisterWaitForSingleObject
helpviewer_keywords:
- ICorThreadpool::CorRegisterWaitForSingleObject method [.NET Framework hosting]
- CorRegisterWaitForSingleObject method [.NET Framework hosting]
ms.assetid: cade1feb-71d2-43ed-85ca-7b2e9da12994
topic_type:
- apiref
ms.openlocfilehash: 8e251ade301ce3ed85f4483634eeae4ca135334a
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762715"
---
# <a name="icorthreadpoolcorregisterwaitforsingleobject-method"></a><span data-ttu-id="00560-102">Método ICorThreadpool::CorRegisterWaitForSingleObject</span><span class="sxs-lookup"><span data-stu-id="00560-102">ICorThreadpool::CorRegisterWaitForSingleObject Method</span></span>
<span data-ttu-id="00560-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="00560-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00560-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00560-104">Syntax</span></span>  
  
```cpp  
HRESULT CorRegisterWaitForSingleObject (  
    [in]  HANDLE*             phNewWaitObject,  
    [in]  HANDLE              hWaitObject,  
    [in]  WAITORTIMERCALLBACK Callback,  
    [in]  PVOID               Context,  
    [in]  ULONG               timeout,  
    [in]  BOOL                executeOnlyOnce,  
    [out] BOOL*               result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="00560-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="00560-105">Requirements</span></span>  
 <span data-ttu-id="00560-106">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00560-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00560-107">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="00560-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="00560-108">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="00560-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00560-109">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00560-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00560-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="00560-110">See also</span></span>

- [<span data-ttu-id="00560-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="00560-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
