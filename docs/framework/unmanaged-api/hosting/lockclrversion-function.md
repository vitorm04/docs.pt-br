---
title: "Função LockClrVersion"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: LockClrVersion
helpviewer_keywords: LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a58d7e99f545026f6f133901ef35a1f9b9fabc7d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="lockclrversion-function"></a><span data-ttu-id="ffa25-102">Função LockClrVersion</span><span class="sxs-lookup"><span data-stu-id="ffa25-102">LockClrVersion Function</span></span>
<span data-ttu-id="ffa25-103">Permite que o host determinar qual versão do common language runtime (CLR) será usado no processo antes de inicializar explicitamente o CLR.</span><span class="sxs-lookup"><span data-stu-id="ffa25-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="ffa25-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ffa25-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffa25-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ffa25-105">Syntax</span></span>  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ffa25-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ffa25-106">Parameters</span></span>  
 `hostCallback`  
 <span data-ttu-id="ffa25-107">[in] A função a ser chamada pelo CLR na inicialização.</span><span class="sxs-lookup"><span data-stu-id="ffa25-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="ffa25-108">[in] A função a ser chamado pelo host para informar ao CLR que a inicialização está iniciando.</span><span class="sxs-lookup"><span data-stu-id="ffa25-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="ffa25-109">[in] A função a ser chamado pelo host para informar ao CLR que a inicialização for concluída.</span><span class="sxs-lookup"><span data-stu-id="ffa25-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ffa25-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ffa25-110">Return Value</span></span>  
 <span data-ttu-id="ffa25-111">Esse método retorna códigos de erro COM padrão, conforme definido no Winerror. H, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="ffa25-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="ffa25-112">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="ffa25-112">Return code</span></span>|<span data-ttu-id="ffa25-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ffa25-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ffa25-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ffa25-114">S_OK</span></span>|<span data-ttu-id="ffa25-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="ffa25-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="ffa25-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ffa25-116">E_INVALIDARG</span></span>|<span data-ttu-id="ffa25-117">Um ou mais dos argumentos for nulo.</span><span class="sxs-lookup"><span data-stu-id="ffa25-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffa25-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="ffa25-118">Remarks</span></span>  
 <span data-ttu-id="ffa25-119">As chamadas de host `LockClrVersion` antes de inicializar o CLR.</span><span class="sxs-lookup"><span data-stu-id="ffa25-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="ffa25-120">`LockClrVersion`usa três parâmetros, que são chamadas de retorno do tipo [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="ffa25-120">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="ffa25-121">Esse tipo é definido da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="ffa25-121">This type is defined as follows.</span></span>  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="ffa25-122">As seguintes etapas ocorrem na inicialização do tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="ffa25-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1.  <span data-ttu-id="ffa25-123">As chamadas de host [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou uma das outras funções de inicialização de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ffa25-123">The host calls [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="ffa25-124">Como alternativa, o host foi possível inicializar o tempo de execução usando a ativação de objeto COM.</span><span class="sxs-lookup"><span data-stu-id="ffa25-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2.  <span data-ttu-id="ffa25-125">O tempo de execução chama a função especificada pelo `hostCallback` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ffa25-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3.  <span data-ttu-id="ffa25-126">A função especificada por `hostCallback` , em seguida, faz com que a seguinte sequência de chamadas:</span><span class="sxs-lookup"><span data-stu-id="ffa25-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    -   <span data-ttu-id="ffa25-127">A função especificada pelo `pBeginHostSetup` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ffa25-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    -   <span data-ttu-id="ffa25-128">`CorBindToRuntimeEx`(ou outra função de inicialização do tempo de execução).</span><span class="sxs-lookup"><span data-stu-id="ffa25-128">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    -   <span data-ttu-id="ffa25-129">[Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span><span class="sxs-lookup"><span data-stu-id="ffa25-129">[ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    -   <span data-ttu-id="ffa25-130">[Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="ffa25-130">[ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span></span>  
  
    -   <span data-ttu-id="ffa25-131">A função especificada pelo `pEndHostSetup` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ffa25-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="ffa25-132">Todas as chamadas de `pBeginHostSetup` para `pEndHostSetup` devem ocorrer em um único thread ou fibra, com a mesma pilha de lógica.</span><span class="sxs-lookup"><span data-stu-id="ffa25-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="ffa25-133">Esse thread pode ser diferente do thread no qual `hostCallback` é chamado.</span><span class="sxs-lookup"><span data-stu-id="ffa25-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffa25-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ffa25-134">Requirements</span></span>  
 <span data-ttu-id="ffa25-135">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffa25-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffa25-136">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ffa25-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ffa25-137">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ffa25-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ffa25-138">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffa25-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffa25-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ffa25-139">See Also</span></span>  
 [<span data-ttu-id="ffa25-140">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="ffa25-140">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
