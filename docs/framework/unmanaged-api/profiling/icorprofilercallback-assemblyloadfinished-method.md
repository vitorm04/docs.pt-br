---
title: Método ICorProfilerCallback::AssemblyLoadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
ms.openlocfilehash: ce4a842bc71ff144e46efb0d6f7068dfca9d207d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500436"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="28070-102">Método ICorProfilerCallback::AssemblyLoadFinished</span><span class="sxs-lookup"><span data-stu-id="28070-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="28070-103">Notifica o criador de perfil que concluiu o carregamento de um assembly.</span><span class="sxs-lookup"><span data-stu-id="28070-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28070-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28070-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28070-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="28070-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="28070-106">\[in] identifica o assembly que foi carregado.</span><span class="sxs-lookup"><span data-stu-id="28070-106">\[in] Identifies the assembly that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="28070-107">\[in] um HRESULT que indica se o assembly terminou de ser carregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="28070-107">\[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="28070-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="28070-108">Remarks</span></span>  
 <span data-ttu-id="28070-109">O valor de `assemblyId` não é válido para uma solicitação de informações até que o `AssemblyLoadFinished` método seja chamado.</span><span class="sxs-lookup"><span data-stu-id="28070-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="28070-110">Algumas partes do carregamento do assembly podem continuar após o `AssemblyLoadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="28070-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="28070-111">Um HRESULT de falha em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="28070-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="28070-112">No entanto, um HRESULT de êxito em `hrStatus` indica apenas que a primeira parte do carregamento do assembly foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="28070-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28070-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="28070-113">Requirements</span></span>  
 <span data-ttu-id="28070-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28070-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28070-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="28070-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="28070-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28070-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28070-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28070-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28070-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="28070-118">See also</span></span>

- [<span data-ttu-id="28070-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="28070-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
