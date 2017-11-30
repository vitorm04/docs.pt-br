---
title: "Método ICorProfilerCallback::AssemblyLoadFinished"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyLoadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: af5089603c2044b10061a32c5921b9eeadf86b36
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="af968-102">Método ICorProfilerCallback::AssemblyLoadFinished</span><span class="sxs-lookup"><span data-stu-id="af968-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="af968-103">Notifica o criador de perfil que um assembly terminou o carregamento.</span><span class="sxs-lookup"><span data-stu-id="af968-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af968-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af968-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af968-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="af968-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="af968-106">[in] Identifica o assembly foi carregado.</span><span class="sxs-lookup"><span data-stu-id="af968-106">[in] Identifies the assembly that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="af968-107">[in] Um HRESULT que indica se o assembly de carregamento concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="af968-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af968-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="af968-108">Remarks</span></span>  
 <span data-ttu-id="af968-109">O valor de `assemblyId` não é válido para uma solicitação de informações até que o `AssemblyLoadFinished` método é chamado.</span><span class="sxs-lookup"><span data-stu-id="af968-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="af968-110">Algumas partes do carregamento do assembly podem continuar após o `AssemblyLoadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="af968-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="af968-111">Uma falha de HRESULT em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="af968-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="af968-112">No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte do carregamento do assembly foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="af968-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af968-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="af968-113">Requirements</span></span>  
 <span data-ttu-id="af968-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af968-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af968-115">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="af968-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="af968-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af968-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af968-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af968-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af968-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af968-118">See Also</span></span>  
 [<span data-ttu-id="af968-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="af968-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
