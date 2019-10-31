---
title: Método IDebuggerInfo::IsDebuggerAttached
ms.date: 03/30/2017
api_name:
- IDebuggerInfo.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IsDebuggerAttached
helpviewer_keywords:
- IDebuggerInfo::IsDebuggerAttached method [.NET Framework hosting]
- IsDebuggerAttached method, IDebuggerInfo interface [.NET Framework hosting]
ms.assetid: 6e21872f-602f-411a-a423-bff5cdf27000
topic_type:
- apiref
ms.openlocfilehash: cbd6fa5f7935a57799d695c3ebb617d856e6dbd9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133172"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="3f64f-102">Método IDebuggerInfo::IsDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="3f64f-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="3f64f-103">Obtém um valor que indica se um depurador gerenciado está anexado a esse processo.</span><span class="sxs-lookup"><span data-stu-id="3f64f-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f64f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3f64f-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f64f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3f64f-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="3f64f-106">fora Um ponteiro para um valor `true` se um depurador gerenciado estiver anexado ao processo; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="3f64f-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f64f-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3f64f-107">Requirements</span></span>  
 <span data-ttu-id="3f64f-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f64f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f64f-109">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3f64f-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3f64f-110">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3f64f-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f64f-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f64f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f64f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f64f-112">See also</span></span>

- [<span data-ttu-id="3f64f-113">Interface IDebuggerInfo</span><span class="sxs-lookup"><span data-stu-id="3f64f-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)
