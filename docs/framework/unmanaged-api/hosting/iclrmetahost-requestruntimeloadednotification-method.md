---
title: "Método ICLRMetaHost::RequestRuntimeLoadedNotification"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.RequestRuntimeLoadedNotification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b7866270d8c9234a375401dfd05b504a06ddbf4b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a><span data-ttu-id="538c9-102">Método ICLRMetaHost::RequestRuntimeLoadedNotification</span><span class="sxs-lookup"><span data-stu-id="538c9-102">ICLRMetaHost::RequestRuntimeLoadedNotification Method</span></span>
<span data-ttu-id="538c9-103">Fornece uma função de retorno de chamada que é garantida para ser chamado quando uma versão de runtime (CLR) de linguagem comum é carregado pela primeira vez, mas ainda não começou.</span><span class="sxs-lookup"><span data-stu-id="538c9-103">Provides a callback function that is guaranteed to be called when a common language runtime (CLR) version is first loaded, but not yet started.</span></span> <span data-ttu-id="538c9-104">Esse método substitui o [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="538c9-104">This method supersedes the [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="538c9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="538c9-105">Syntax</span></span>  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="538c9-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="538c9-106">Parameters</span></span>  
 `pCallbackFunction`  
 <span data-ttu-id="538c9-107">[in] A função de retorno de chamada que é chamada quando um novo tempo de execução foi carregado.</span><span class="sxs-lookup"><span data-stu-id="538c9-107">[in] The callback function that is invoked when a new runtime has been loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="538c9-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="538c9-108">Return Value</span></span>  
 <span data-ttu-id="538c9-109">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="538c9-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="538c9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="538c9-110">HRESULT</span></span>|<span data-ttu-id="538c9-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="538c9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="538c9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="538c9-112">S_OK</span></span>|<span data-ttu-id="538c9-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="538c9-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="538c9-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="538c9-114">E_POINTER</span></span>|<span data-ttu-id="538c9-115">`pCallbackFunction` é nulo.</span><span class="sxs-lookup"><span data-stu-id="538c9-115">`pCallbackFunction` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="538c9-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="538c9-116">Remarks</span></span>  
 <span data-ttu-id="538c9-117">O retorno de chamada funciona da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="538c9-117">The callback works in the following way:</span></span>  
  
-   <span data-ttu-id="538c9-118">O retorno de chamada é invocado apenas quando um tempo de execução é carregado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="538c9-118">The callback is invoked only when a runtime is loaded for the first time.</span></span>  
  
-   <span data-ttu-id="538c9-119">O retorno de chamada não é invocado para cargas reentrantes de tempo de execução do mesmo.</span><span class="sxs-lookup"><span data-stu-id="538c9-119">The callback is not invoked for reentrant loads of the same runtime.</span></span>  
  
-   <span data-ttu-id="538c9-120">Para cargas de tempo de execução não reentrante chamadas para a função de retorno de chamada são serializadas.</span><span class="sxs-lookup"><span data-stu-id="538c9-120">For non-reentrant runtime loads, calls to the callback function are serialized.</span></span>  
  
 <span data-ttu-id="538c9-121">A função de retorno de chamada tem o seguinte protótipo:</span><span class="sxs-lookup"><span data-stu-id="538c9-121">The callback function has the following prototype:</span></span>  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 <span data-ttu-id="538c9-122">Os protótipos de função de retorno de chamada são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="538c9-122">The callback function prototypes are as follows:</span></span>  
  
-   <span data-ttu-id="538c9-123">`pfnCallbackThreadSet`:</span><span class="sxs-lookup"><span data-stu-id="538c9-123">`pfnCallbackThreadSet`:</span></span>  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
-   <span data-ttu-id="538c9-124">`pfnCallbackThreadUnset`:</span><span class="sxs-lookup"><span data-stu-id="538c9-124">`pfnCallbackThreadUnset`:</span></span>  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 <span data-ttu-id="538c9-125">Se o host pretende carregar ou fazer com que o outro em tempo de execução a ser carregado de forma reentrante o `pfnCallbackThreadSet` e `pfnCallbackThreadUnset` parâmetros que são fornecidas no retorno de chamada a função deve ser usada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="538c9-125">If the host intends to load or cause another runtime to be loaded in a reentrant manner, the `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` parameters that are provided in the callback function must be used in the following way:</span></span>  
  
-   <span data-ttu-id="538c9-126">`pfnCallbackThreadSet`deve ser chamado pelo thread que pode causar uma carga de tempo de execução antes de uma tentativa de tal carga.</span><span class="sxs-lookup"><span data-stu-id="538c9-126">`pfnCallbackThreadSet` must be called by the thread that might cause a runtime load before such a load is attempted.</span></span>  
  
-   <span data-ttu-id="538c9-127">`pfnCallbackThreadUnset`deve ser chamado quando o thread não fará com que tal carga de tempo de execução (e antes de retornar de retorno de chamada inicial).</span><span class="sxs-lookup"><span data-stu-id="538c9-127">`pfnCallbackThreadUnset` must be called when the thread will no longer cause such a runtime load (and before returning from the initial callback).</span></span>  
  
-   <span data-ttu-id="538c9-128">`pfnCallbackThreadSet`e `pfnCallbackThreadUnset` são ambos não reentrante.</span><span class="sxs-lookup"><span data-stu-id="538c9-128">`pfnCallbackThreadSet` and `pfnCallbackThreadUnset` are both non-reentrant.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="538c9-129">Hospedar aplicativos não devem chamar `pfnCallbackThreadSet` e `pfnCallbackThreadUnset` fora do escopo de `pCallbackFunction` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="538c9-129">Host applications must not call `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` outside the scope of the `pCallbackFunction` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="538c9-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="538c9-130">Requirements</span></span>  
 <span data-ttu-id="538c9-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="538c9-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="538c9-132">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="538c9-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="538c9-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="538c9-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="538c9-134">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="538c9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="538c9-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="538c9-135">See Also</span></span>  
 [<span data-ttu-id="538c9-136">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="538c9-136">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="538c9-137">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="538c9-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
