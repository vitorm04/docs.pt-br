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
ms.openlocfilehash: 1cf3f2b62b388b6c2d6fcd75b1b07a67d5b2e49f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866696"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="a286f-102">Método ICorProfilerCallback::AppDomainCreationFinished</span><span class="sxs-lookup"><span data-stu-id="a286f-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="a286f-103">Notifica o criador de perfil de que um domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="a286f-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a286f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a286f-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
## <a name="parameters"></a><span data-ttu-id="a286f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a286f-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="a286f-106">\[em] identifica o domínio que foi criado.</span><span class="sxs-lookup"><span data-stu-id="a286f-106">\[in] Identifies the domain which has been created.</span></span>

- `hrStatus`

  <span data-ttu-id="a286f-107">\[em] um HRESULT que indica se a criação do domínio do aplicativo foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="a286f-107">\[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="a286f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a286f-108">Remarks</span></span>  
 <span data-ttu-id="a286f-109">A ID do aplicativo não é válida para nenhuma solicitação de informações até que o método `AppDomainCreationFinished` seja chamado.</span><span class="sxs-lookup"><span data-stu-id="a286f-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="a286f-110">Algumas partes do carregamento do domínio do aplicativo podem continuar após o retorno de chamada `AppDomainCreationFinished`.</span><span class="sxs-lookup"><span data-stu-id="a286f-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="a286f-111">Uma falha HRESULT no `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="a286f-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="a286f-112">No entanto, um HRESULT de êxito em `hrStatus` indica apenas que a primeira parte da criação do domínio do aplicativo foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="a286f-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a286f-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="a286f-113">Requirements</span></span>  
 <span data-ttu-id="a286f-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a286f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a286f-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a286f-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a286f-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a286f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a286f-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a286f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a286f-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="a286f-118">See also</span></span>

- [<span data-ttu-id="a286f-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a286f-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
