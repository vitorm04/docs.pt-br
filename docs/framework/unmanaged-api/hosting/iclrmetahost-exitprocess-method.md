---
title: Método ICLRMetaHost::ExitProcess
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.ExitProcess
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64c212d064ad658678926690d1e680afe27c7c99
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219233"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="48def-102">Método ICLRMetaHost::ExitProcess</span><span class="sxs-lookup"><span data-stu-id="48def-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="48def-103">Tenta desligar normalmente o carregados todos os tempos de execução e, em seguida, encerra o processo.</span><span class="sxs-lookup"><span data-stu-id="48def-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="48def-104">Substitui o [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="48def-104">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48def-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48def-105">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48def-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="48def-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="48def-107">[in] O código de saída para o processo.</span><span class="sxs-lookup"><span data-stu-id="48def-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48def-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="48def-108">Return Value</span></span>  
 <span data-ttu-id="48def-109">Esse método nunca retorna, portanto, seu valor de retorno será indefinido.</span><span class="sxs-lookup"><span data-stu-id="48def-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48def-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="48def-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48def-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48def-111">Requirements</span></span>  
 <span data-ttu-id="48def-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48def-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48def-113">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="48def-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="48def-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="48def-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="48def-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48def-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48def-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48def-116">See also</span></span>

- [<span data-ttu-id="48def-117">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="48def-117">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="48def-118">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="48def-118">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
