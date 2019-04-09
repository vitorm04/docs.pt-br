---
title: Função LockClrVersion
ms.date: 03/30/2017
api_name:
- LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LockClrVersion
helpviewer_keywords:
- LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 571a676496683ba3251f13c41600bb017e1ced5d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156098"
---
# <a name="lockclrversion-function"></a><span data-ttu-id="92c63-102">Função LockClrVersion</span><span class="sxs-lookup"><span data-stu-id="92c63-102">LockClrVersion Function</span></span>
<span data-ttu-id="92c63-103">Permite que o host determine qual versão do common language runtime (CLR) será usado dentro do processo antes de inicializar explicitamente o CLR.</span><span class="sxs-lookup"><span data-stu-id="92c63-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="92c63-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92c63-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92c63-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92c63-105">Syntax</span></span>  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92c63-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="92c63-106">Parameters</span></span>  
 `hostCallback`  
 <span data-ttu-id="92c63-107">[in] A função a ser chamado pelo CLR na inicialização.</span><span class="sxs-lookup"><span data-stu-id="92c63-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="92c63-108">[in] A função a ser chamado pelo host para informar ao CLR que a inicialização está sendo iniciado.</span><span class="sxs-lookup"><span data-stu-id="92c63-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="92c63-109">[in] A função a ser chamado pelo host para informar ao CLR que a inicialização foi concluída.</span><span class="sxs-lookup"><span data-stu-id="92c63-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92c63-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="92c63-110">Return Value</span></span>  
 <span data-ttu-id="92c63-111">Esse método retorna códigos de erro COM padrão, conforme definido em Winerror. H, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="92c63-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="92c63-112">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="92c63-112">Return code</span></span>|<span data-ttu-id="92c63-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="92c63-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="92c63-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="92c63-114">S_OK</span></span>|<span data-ttu-id="92c63-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="92c63-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="92c63-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="92c63-116">E_INVALIDARG</span></span>|<span data-ttu-id="92c63-117">Um ou mais dos argumentos é nulo.</span><span class="sxs-lookup"><span data-stu-id="92c63-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92c63-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="92c63-118">Remarks</span></span>  
 <span data-ttu-id="92c63-119">O host chama `LockClrVersion` antes de inicializar o CLR.</span><span class="sxs-lookup"><span data-stu-id="92c63-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> `LockClrVersion` <span data-ttu-id="92c63-120">usa três parâmetros, que são os retornos de chamada do tipo [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="92c63-120">takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="92c63-121">Esse tipo é definido da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="92c63-121">This type is defined as follows.</span></span>  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="92c63-122">As seguintes etapas ocorrem após a inicialização do tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="92c63-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1.  <span data-ttu-id="92c63-123">O host chama [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou uma das outras funções de inicialização de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="92c63-123">The host calls [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="92c63-124">Como alternativa, o host foi possível inicializar o tempo de execução usando a ativação de objeto COM.</span><span class="sxs-lookup"><span data-stu-id="92c63-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2.  <span data-ttu-id="92c63-125">O tempo de execução chama a função especificada pelo `hostCallback` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="92c63-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3.  <span data-ttu-id="92c63-126">A função especificada por `hostCallback` , em seguida, faz a seguinte sequência de chamadas:</span><span class="sxs-lookup"><span data-stu-id="92c63-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    -   <span data-ttu-id="92c63-127">A função especificada pelo `pBeginHostSetup` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="92c63-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    -   `CorBindToRuntimeEx` <span data-ttu-id="92c63-128">(ou outra função de inicialização de tempo de execução).</span><span class="sxs-lookup"><span data-stu-id="92c63-128">(or another runtime initialization function).</span></span>  
  
    -   <span data-ttu-id="92c63-129">[ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span><span class="sxs-lookup"><span data-stu-id="92c63-129">[ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    -   <span data-ttu-id="92c63-130">[ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="92c63-130">[ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span></span>  
  
    -   <span data-ttu-id="92c63-131">A função especificada pelo `pEndHostSetup` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="92c63-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="92c63-132">Todas as chamadas de `pBeginHostSetup` para `pEndHostSetup` deve ocorrer em um único thread ou fibra, com a mesma pilha de lógica.</span><span class="sxs-lookup"><span data-stu-id="92c63-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="92c63-133">Esse thread pode ser diferente do thread no qual `hostCallback` é chamado.</span><span class="sxs-lookup"><span data-stu-id="92c63-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92c63-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="92c63-134">Requirements</span></span>  
 <span data-ttu-id="92c63-135">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92c63-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92c63-136">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="92c63-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92c63-137">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="92c63-137">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="92c63-138">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="92c63-138">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="92c63-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92c63-139">See also</span></span>

- [<span data-ttu-id="92c63-140">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="92c63-140">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
