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
ms.openlocfilehash: 76f56971223154d3ed966c272081049adf30de54
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500488"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="4a72f-102">Método ICorProfilerCallback::AppDomainCreationFinished</span><span class="sxs-lookup"><span data-stu-id="4a72f-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="4a72f-103">Notifica o criador de perfil de que um domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="4a72f-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a72f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a72f-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a><span data-ttu-id="4a72f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4a72f-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="4a72f-106">\[em] identifica o domínio que foi criado.</span><span class="sxs-lookup"><span data-stu-id="4a72f-106">\[in] Identifies the domain which has been created.</span></span>

- `hrStatus`

  <span data-ttu-id="4a72f-107">\[in] um HRESULT que indica se a criação do domínio do aplicativo foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="4a72f-107">\[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="4a72f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a72f-108">Remarks</span></span>  
 <span data-ttu-id="4a72f-109">A ID do aplicativo não é válida para nenhuma solicitação de informações até que o `AppDomainCreationFinished` método seja chamado.</span><span class="sxs-lookup"><span data-stu-id="4a72f-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="4a72f-110">Algumas partes do carregamento do domínio do aplicativo podem continuar após o `AppDomainCreationFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="4a72f-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="4a72f-111">Um HRESULT de falha em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="4a72f-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="4a72f-112">No entanto, um HRESULT de êxito em `hrStatus` indica apenas que a primeira parte da criação do domínio do aplicativo foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="4a72f-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a72f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a72f-113">Requirements</span></span>  
 <span data-ttu-id="4a72f-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a72f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a72f-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4a72f-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4a72f-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a72f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a72f-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a72f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a72f-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="4a72f-118">See also</span></span>

- [<span data-ttu-id="4a72f-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="4a72f-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
