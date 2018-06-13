---
title: Método ICLRMetaHost::RequestRuntimeLoadedNotification
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ac041db64a874cc143657c601f30e4482dd2462
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434429"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a><span data-ttu-id="5f7f2-102">Método ICLRMetaHost::RequestRuntimeLoadedNotification</span><span class="sxs-lookup"><span data-stu-id="5f7f2-102">ICLRMetaHost::RequestRuntimeLoadedNotification Method</span></span>
<span data-ttu-id="5f7f2-103">Fornece uma função de retorno de chamada que é garantida para ser chamado quando uma versão de runtime (CLR) de linguagem comum é carregado pela primeira vez, mas ainda não começou.</span><span class="sxs-lookup"><span data-stu-id="5f7f2-103">Provides a callback function that is guaranteed to be called when a common language runtime (CLR) version is first loaded, but not yet started.</span></span> <span data-ttu-id="5f7f2-104">Esse método substitui o [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="5f7f2-104">This method supersedes the [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f7f2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f7f2-105">Syntax</span></span>  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5f7f2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5f7f2-106">Parameters</span></span>  
 `pCallbackFunction`  
 <span data-ttu-id="5f7f2-107">[in] A função de retorno de chamada que é chamada quando um novo tempo de execução foi carregado.</span><span class="sxs-lookup"><span data-stu-id="5f7f2-107">[in] The callback function that is invoked when a new runtime has been loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f7f2-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5f7f2-108">Return Value</span></span>  
 <span data-ttu-id="5f7f2-109">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="5f7f2-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5f7f2-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5f7f2-110">HRESULT</span></span>|<span data-ttu-id="5f7f2-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f7f2-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5f7f2-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="5f7f2-112">S_OK</span></span>|<span data-ttu-id="5f7f2-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="5f7f2-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="5f7f2-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="5f7f2-114">E_POINTER</span></span>|<span data-ttu-id="5f7f2-115">`pCallbackFunction` é nulo.</span><span class="sxs-lookup"><span data-stu-id="5f7f2-115">`pCallbackFunction` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f7f2-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="5f7f2-116">Remarks</span></span>  
 <span data-ttu-id="5f7f2-117">O retorno de chamada funciona da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="5f7f2-117">The callback works in the following way:</span></span>  
  
-   <span data-ttu-id="5f7f2-118">O retorno de chamada é invocado apenas quando um tempo de execução é carregado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="5f7f2-118">The callback is invoked only when a runtime is loaded for the first time.</span></span>  
  
-   <span data-ttu-id="5f7f2-119">O retorno de chamada não é invocado para cargas reentrantes de tempo de execução do mesmo.</span><span class="sxs-lookup"><span data-stu-id="5f7f2-119">The callback is not invoked for reentrant loads of the same runtime.</span></span>  
  
-   <span data-ttu-id="5f7f2-120">Para cargas de tempo de execução não reentrante chamadas para a função de retorno de chamada são serializadas.</span><span class="sxs-lookup"><span data-stu-id="5f7f2-120">For non-reentrant runtime loads, calls to the callback function are serialized.</span></span>  
  
 <span data-ttu-id="5f7f2-121">A função de retorno de chamada tem o seguinte protótipo:</span><span class="sxs-lookup"><span data-stu-id="5f7f2-121">The callback function has the following prototype:</span></span>  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 <span data-ttu-id="5f7f2-122">Os protótipos de função de retorno de chamada são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="5f7f2-122">The callback function prototypes are as follows:</span></span>  
  
-   <span data-ttu-id="5f7f2-123">`pfnCallbackThreadSet`:</span><span class="sxs-lookup"><span data-stu-id="5f7f2-123">`pfnCallbackThreadSet`:</span></span>  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
-   <span data-ttu-id="5f7f2-124">`pfnCallbackThreadUnset`:</span><span class="sxs-lookup"><span data-stu-id="5f7f2-124">`pfnCallbackThreadUnset`:</span></span>  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 <span data-ttu-id="5f7f2-125">Se o host pretende carregar ou fazer com que o outro em tempo de execução a ser carregado de forma reentrante o `pfnCallbackThreadSet` e `pfnCallbackThreadUnset` parâmetros que são fornecidas no retorno de chamada a função deve ser usada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="5f7f2-125">If the host intends to load or cause another runtime to be loaded in a reentrant manner, the `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` parameters that are provided in the callback function must be used in the following way:</span></span>  
  
-   <span data-ttu-id="5f7f2-126">`pfnCallbackThreadSet` deve ser chamado pelo thread que pode causar uma carga de tempo de execução antes de uma tentativa de tal carga.</span><span class="sxs-lookup"><span data-stu-id="5f7f2-126">`pfnCallbackThreadSet` must be called by the thread that might cause a runtime load before such a load is attempted.</span></span>  
  
-   <span data-ttu-id="5f7f2-127">`pfnCallbackThreadUnset` deve ser chamado quando o thread não fará com que tal carga de tempo de execução (e antes de retornar de retorno de chamada inicial).</span><span class="sxs-lookup"><span data-stu-id="5f7f2-127">`pfnCallbackThreadUnset` must be called when the thread will no longer cause such a runtime load (and before returning from the initial callback).</span></span>  
  
-   <span data-ttu-id="5f7f2-128">`pfnCallbackThreadSet` e `pfnCallbackThreadUnset` são ambos não reentrante.</span><span class="sxs-lookup"><span data-stu-id="5f7f2-128">`pfnCallbackThreadSet` and `pfnCallbackThreadUnset` are both non-reentrant.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f7f2-129">Hospedar aplicativos não devem chamar `pfnCallbackThreadSet` e `pfnCallbackThreadUnset` fora do escopo de `pCallbackFunction` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5f7f2-129">Host applications must not call `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` outside the scope of the `pCallbackFunction` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f7f2-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5f7f2-130">Requirements</span></span>  
 <span data-ttu-id="5f7f2-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f7f2-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f7f2-132">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5f7f2-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5f7f2-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="5f7f2-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f7f2-134">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f7f2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f7f2-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f7f2-135">See Also</span></span>  
 [<span data-ttu-id="5f7f2-136">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="5f7f2-136">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="5f7f2-137">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="5f7f2-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
