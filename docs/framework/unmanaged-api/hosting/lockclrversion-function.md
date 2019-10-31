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
ms.openlocfilehash: 216852f8f051440b2814619b843a1f25013e4042
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133770"
---
# <a name="lockclrversion-function"></a><span data-ttu-id="f658a-102">Função LockClrVersion</span><span class="sxs-lookup"><span data-stu-id="f658a-102">LockClrVersion Function</span></span>
<span data-ttu-id="f658a-103">Permite que o host determine qual versão do Common Language Runtime (CLR) será usada dentro do processo antes de inicializar explicitamente o CLR.</span><span class="sxs-lookup"><span data-stu-id="f658a-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="f658a-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f658a-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f658a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f658a-105">Syntax</span></span>  
  
```cpp  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f658a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f658a-106">Parameters</span></span>  
 `hostCallback`  
 <span data-ttu-id="f658a-107">no A função a ser chamada pelo CLR na inicialização.</span><span class="sxs-lookup"><span data-stu-id="f658a-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="f658a-108">no A função a ser chamada pelo host para informar ao CLR que a inicialização está sendo iniciada.</span><span class="sxs-lookup"><span data-stu-id="f658a-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="f658a-109">no A função a ser chamada pelo host para informar ao CLR que a inicialização foi concluída.</span><span class="sxs-lookup"><span data-stu-id="f658a-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f658a-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f658a-110">Return Value</span></span>  
 <span data-ttu-id="f658a-111">Esse método retorna códigos de erro COM padrão, conforme definido no WinError. h, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="f658a-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="f658a-112">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="f658a-112">Return code</span></span>|<span data-ttu-id="f658a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f658a-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f658a-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="f658a-114">S_OK</span></span>|<span data-ttu-id="f658a-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="f658a-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="f658a-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f658a-116">E_INVALIDARG</span></span>|<span data-ttu-id="f658a-117">Um ou mais argumentos são nulos.</span><span class="sxs-lookup"><span data-stu-id="f658a-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f658a-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="f658a-118">Remarks</span></span>  
 <span data-ttu-id="f658a-119">O host chama `LockClrVersion` antes de inicializar o CLR.</span><span class="sxs-lookup"><span data-stu-id="f658a-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="f658a-120">`LockClrVersion` usa três parâmetros, todos os quais são retornos de chamada do tipo [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="f658a-120">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="f658a-121">Esse tipo é definido da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="f658a-121">This type is defined as follows.</span></span>  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="f658a-122">As etapas a seguir ocorrem na inicialização do tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="f658a-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1. <span data-ttu-id="f658a-123">O host chama [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou uma das outras funções de inicialização de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f658a-123">The host calls [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="f658a-124">Como alternativa, o host poderia inicializar o tempo de execução usando a ativação de objeto COM.</span><span class="sxs-lookup"><span data-stu-id="f658a-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2. <span data-ttu-id="f658a-125">O tempo de execução chama a função especificada pelo parâmetro `hostCallback`.</span><span class="sxs-lookup"><span data-stu-id="f658a-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3. <span data-ttu-id="f658a-126">A função especificada por `hostCallback`, em seguida, faz a seguinte sequência de chamadas:</span><span class="sxs-lookup"><span data-stu-id="f658a-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    - <span data-ttu-id="f658a-127">A função especificada pelo parâmetro `pBeginHostSetup`.</span><span class="sxs-lookup"><span data-stu-id="f658a-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    - <span data-ttu-id="f658a-128">`CorBindToRuntimeEx` (ou outra função de inicialização de tempo de execução).</span><span class="sxs-lookup"><span data-stu-id="f658a-128">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    - <span data-ttu-id="f658a-129">[ICLRRuntimeHost:: SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span><span class="sxs-lookup"><span data-stu-id="f658a-129">[ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    - <span data-ttu-id="f658a-130">[ICLRRuntimeHost:: iniciar](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="f658a-130">[ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span></span>  
  
    - <span data-ttu-id="f658a-131">A função especificada pelo parâmetro `pEndHostSetup`.</span><span class="sxs-lookup"><span data-stu-id="f658a-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="f658a-132">Todas as chamadas de `pBeginHostSetup` para `pEndHostSetup` devem ocorrer em um único thread ou fibra, com a mesma pilha lógica.</span><span class="sxs-lookup"><span data-stu-id="f658a-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="f658a-133">Esse thread pode ser diferente do thread no qual `hostCallback` é chamado.</span><span class="sxs-lookup"><span data-stu-id="f658a-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f658a-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f658a-134">Requirements</span></span>  
 <span data-ttu-id="f658a-135">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f658a-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f658a-136">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f658a-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f658a-137">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f658a-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f658a-138">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f658a-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f658a-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f658a-139">See also</span></span>

- [<span data-ttu-id="f658a-140">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="f658a-140">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
