---
title: Método ICorDebugDataTarget::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71d267eedf621a11f8ad21cc7148e1810955521c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713425"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="b8332-102">Método ICorDebugDataTarget::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="b8332-102">ICorDebugDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="b8332-103">Retorna o contexto do thread atual para o thread especificado.</span><span class="sxs-lookup"><span data-stu-id="b8332-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8332-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8332-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b8332-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b8332-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="b8332-106">[in] O identificador do thread cujo contexto deve ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="b8332-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="b8332-107">O identificador está definido pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="b8332-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="b8332-108">[in] Uma combinação bit a bit dos sinalizadores de dependente de plataforma que indicam quais partes do contexto devem ser lida.</span><span class="sxs-lookup"><span data-stu-id="b8332-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="b8332-109">[in] O tamanho do `pContext`.</span><span class="sxs-lookup"><span data-stu-id="b8332-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="b8332-110">[out] O buffer no qual o contexto do thread será armazenado.</span><span class="sxs-lookup"><span data-stu-id="b8332-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8332-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8332-111">Remarks</span></span>  
 <span data-ttu-id="b8332-112">Em plataformas Windows, `pContext` deve ser um `CONTEXT` estrutura (definida em Winnt. H) que é apropriada para o tipo de computador especificado pelo [icordebugdatatarget:: Getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="b8332-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="b8332-113">`contextFlags` deve ter os mesmos valores que o `ContextFlags` campo do `CONTEXT` estrutura.</span><span class="sxs-lookup"><span data-stu-id="b8332-113">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="b8332-114">O `CONTEXT` estrutura é específico do processador, consulte o arquivo de Winnt. H para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="b8332-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8332-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8332-115">Requirements</span></span>  
 <span data-ttu-id="b8332-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8332-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8332-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8332-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8332-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8332-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8332-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8332-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8332-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8332-120">See also</span></span>
- [<span data-ttu-id="b8332-121">Interface ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="b8332-121">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="b8332-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b8332-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b8332-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="b8332-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
