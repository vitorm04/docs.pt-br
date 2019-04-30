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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993246"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="bb640-102">Método ICLRMetaHost::ExitProcess</span><span class="sxs-lookup"><span data-stu-id="bb640-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="bb640-103">Tenta desligar normalmente o carregados todos os tempos de execução e, em seguida, encerra o processo.</span><span class="sxs-lookup"><span data-stu-id="bb640-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="bb640-104">Substitui o [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="bb640-104">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb640-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb640-105">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb640-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bb640-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="bb640-107">[in] O código de saída para o processo.</span><span class="sxs-lookup"><span data-stu-id="bb640-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb640-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bb640-108">Return Value</span></span>  
 <span data-ttu-id="bb640-109">Esse método nunca retorna, portanto, seu valor de retorno será indefinido.</span><span class="sxs-lookup"><span data-stu-id="bb640-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb640-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb640-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb640-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bb640-111">Requirements</span></span>  
 <span data-ttu-id="bb640-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb640-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb640-113">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="bb640-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bb640-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="bb640-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb640-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb640-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb640-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb640-116">See also</span></span>

- [<span data-ttu-id="bb640-117">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="bb640-117">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="bb640-118">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="bb640-118">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
