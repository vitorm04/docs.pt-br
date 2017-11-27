---
title: "Método ICLRMetaHost::ExitProcess"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.ExitProcess
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 10fb9bef99a90a76ea5bb1f4abe73cd756717285
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="c581f-102">Método ICLRMetaHost::ExitProcess</span><span class="sxs-lookup"><span data-stu-id="c581f-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="c581f-103">Tenta desligar normalmente o carregados todos os tempos de execução e, em seguida, encerra o processo.</span><span class="sxs-lookup"><span data-stu-id="c581f-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="c581f-104">Substitui o [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="c581f-104">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c581f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c581f-105">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c581f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c581f-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="c581f-107">[in] O código de saída para o processo.</span><span class="sxs-lookup"><span data-stu-id="c581f-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c581f-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c581f-108">Return Value</span></span>  
 <span data-ttu-id="c581f-109">Este método nunca retorna, portanto, seu valor de retorno é indefinido.</span><span class="sxs-lookup"><span data-stu-id="c581f-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c581f-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="c581f-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c581f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c581f-111">Requirements</span></span>  
 <span data-ttu-id="c581f-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c581f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c581f-113">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c581f-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c581f-114">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="c581f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c581f-115">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c581f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c581f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c581f-116">See Also</span></span>  
 [<span data-ttu-id="c581f-117">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="c581f-117">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="c581f-118">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="c581f-118">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
