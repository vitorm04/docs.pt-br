---
title: Método ICorProfilerCallback::AppDomainCreationFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 35dac5fd000f5ae30af917e3813239b2e365e64a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153979"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="d06fe-102">Método ICorProfilerCallback::AppDomainCreationFinished</span><span class="sxs-lookup"><span data-stu-id="d06fe-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="d06fe-103">Notifica o criador de perfil que foi criado um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d06fe-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d06fe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d06fe-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
## <a name="parameters"></a><span data-ttu-id="d06fe-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d06fe-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="d06fe-106">[in] Identifica o domínio que foi criado.</span><span class="sxs-lookup"><span data-stu-id="d06fe-106">[in] Identifies the domain which has been created.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="d06fe-107">[in] Um HRESULT que indica se a criação do domínio do aplicativo foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="d06fe-107">[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d06fe-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="d06fe-108">Remarks</span></span>  
 <span data-ttu-id="d06fe-109">A ID do aplicativo não é válida para qualquer solicitação de informações até que o `AppDomainCreationFinished` método é chamado.</span><span class="sxs-lookup"><span data-stu-id="d06fe-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="d06fe-110">Algumas partes de carregamento de domínio do aplicativo podem continuar após o `AppDomainCreationFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="d06fe-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="d06fe-111">Uma falha HRESULT em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="d06fe-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="d06fe-112">No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte da criação do domínio de aplicativo teve êxito.</span><span class="sxs-lookup"><span data-stu-id="d06fe-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d06fe-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d06fe-113">Requirements</span></span>  
 <span data-ttu-id="d06fe-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d06fe-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d06fe-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d06fe-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d06fe-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d06fe-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d06fe-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="d06fe-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d06fe-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d06fe-118">See also</span></span>

- [<span data-ttu-id="d06fe-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="d06fe-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
