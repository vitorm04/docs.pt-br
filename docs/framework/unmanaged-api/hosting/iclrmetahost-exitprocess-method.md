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
ms.openlocfilehash: bbf3c00eafe47556c6b46e1acb687a19df5a2b28
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601747"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="a4d4b-102">Método ICLRMetaHost::ExitProcess</span><span class="sxs-lookup"><span data-stu-id="a4d4b-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="a4d4b-103">Tenta desligar normalmente o carregados todos os tempos de execução e, em seguida, encerra o processo.</span><span class="sxs-lookup"><span data-stu-id="a4d4b-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="a4d4b-104">Substitui o [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="a4d4b-104">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4d4b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a4d4b-105">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4d4b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a4d4b-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="a4d4b-107">[in] O código de saída para o processo.</span><span class="sxs-lookup"><span data-stu-id="a4d4b-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4d4b-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a4d4b-108">Return Value</span></span>  
 <span data-ttu-id="a4d4b-109">Esse método nunca retorna, portanto, seu valor de retorno será indefinido.</span><span class="sxs-lookup"><span data-stu-id="a4d4b-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4d4b-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a4d4b-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4d4b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a4d4b-111">Requirements</span></span>  
 <span data-ttu-id="a4d4b-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4d4b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4d4b-113">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a4d4b-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a4d4b-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a4d4b-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4d4b-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4d4b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4d4b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4d4b-116">See also</span></span>
- [<span data-ttu-id="a4d4b-117">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="a4d4b-117">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="a4d4b-118">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="a4d4b-118">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
