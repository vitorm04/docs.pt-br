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
ms.openlocfilehash: d8643c54950486b6374045ff83928c8c7fb568a9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140943"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="af9a3-102">Método ICLRMetaHost::ExitProcess</span><span class="sxs-lookup"><span data-stu-id="af9a3-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="af9a3-103">Tenta desligar todos os tempos de execução carregados normalmente e, em seguida, encerra o processo.</span><span class="sxs-lookup"><span data-stu-id="af9a3-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="af9a3-104">Substitui a função [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) .</span><span class="sxs-lookup"><span data-stu-id="af9a3-104">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af9a3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af9a3-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af9a3-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="af9a3-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="af9a3-107">no O código de saída do processo.</span><span class="sxs-lookup"><span data-stu-id="af9a3-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af9a3-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="af9a3-108">Return Value</span></span>  
 <span data-ttu-id="af9a3-109">Esse método nunca retorna, portanto, seu valor de retorno é indefinido.</span><span class="sxs-lookup"><span data-stu-id="af9a3-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af9a3-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="af9a3-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af9a3-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="af9a3-111">Requirements</span></span>  
 <span data-ttu-id="af9a3-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af9a3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af9a3-113">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="af9a3-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="af9a3-114">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="af9a3-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af9a3-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af9a3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af9a3-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af9a3-116">See also</span></span>

- [<span data-ttu-id="af9a3-117">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="af9a3-117">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="af9a3-118">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="af9a3-118">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
