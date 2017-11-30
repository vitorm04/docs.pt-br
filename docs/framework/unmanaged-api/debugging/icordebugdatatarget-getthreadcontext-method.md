---
title: "Método ICorDebugDataTarget::GetThreadContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget.GetThreadContext Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 543956bb42d7477456426d7327f14b059b23d759
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="a7f1e-102">Método ICorDebugDataTarget::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="a7f1e-102">ICorDebugDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="a7f1e-103">Retorna o contexto do thread atual para o segmento especificado.</span><span class="sxs-lookup"><span data-stu-id="a7f1e-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7f1e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7f1e-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7f1e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a7f1e-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="a7f1e-106">[in] O identificador do segmento é cujo contexto a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="a7f1e-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="a7f1e-107">O identificador é definido pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="a7f1e-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="a7f1e-108">[in] Uma combinação bit a bit dos sinalizadores de dependente de plataforma que indicam quais partes do contexto deve ser lidos.</span><span class="sxs-lookup"><span data-stu-id="a7f1e-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="a7f1e-109">[in] O tamanho do `pContext`.</span><span class="sxs-lookup"><span data-stu-id="a7f1e-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="a7f1e-110">[out] O buffer onde o contexto do thread será armazenado.</span><span class="sxs-lookup"><span data-stu-id="a7f1e-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7f1e-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="a7f1e-111">Remarks</span></span>  
 <span data-ttu-id="a7f1e-112">Em plataformas Windows, `pContext` deve ser um `CONTEXT` estrutura (definida em Winnt. H) que é apropriada para o tipo de máquina especificado o [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="a7f1e-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="a7f1e-113">`contextFlags`deve ter os mesmos valores que o `ContextFlags` campo o `CONTEXT` estrutura.</span><span class="sxs-lookup"><span data-stu-id="a7f1e-113">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="a7f1e-114">O `CONTEXT` estrutura específicos de processador; consulte o arquivo Winnt. H para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="a7f1e-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7f1e-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a7f1e-115">Requirements</span></span>  
 <span data-ttu-id="a7f1e-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7f1e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7f1e-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7f1e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7f1e-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7f1e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7f1e-119">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7f1e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f1e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7f1e-120">See Also</span></span>  
 [<span data-ttu-id="a7f1e-121">Interface ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="a7f1e-121">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="a7f1e-122">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="a7f1e-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a7f1e-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="a7f1e-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
