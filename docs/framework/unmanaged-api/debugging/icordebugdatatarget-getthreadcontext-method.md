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
ms.openlocfilehash: 3eace2d91b3bb6e637a659b8b49a31450ebc2c42
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783724"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="1866a-102">Método ICorDebugDataTarget::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="1866a-102">ICorDebugDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="1866a-103">Retorna o contexto do thread atual para o thread especificado.</span><span class="sxs-lookup"><span data-stu-id="1866a-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1866a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1866a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1866a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1866a-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="1866a-106">no O identificador do thread cujo contexto deve ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="1866a-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="1866a-107">O identificador é definido pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="1866a-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="1866a-108">no Uma combinação de bits e de sinalizadores que dependem de plataforma que indicam quais partes do contexto devem ser lidas.</span><span class="sxs-lookup"><span data-stu-id="1866a-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="1866a-109">[in] O tamanho do `pContext`.</span><span class="sxs-lookup"><span data-stu-id="1866a-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="1866a-110">fora O buffer em que o contexto de thread será armazenado.</span><span class="sxs-lookup"><span data-stu-id="1866a-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1866a-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="1866a-111">Remarks</span></span>  
 <span data-ttu-id="1866a-112">Em plataformas Windows, `pContext` deve ser uma estrutura de `CONTEXT` (definida em WinNT. h) apropriada para o tipo de computador especificado pelo método [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1866a-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="1866a-113">`contextFlags` deve ter os mesmos valores que o campo `ContextFlags` da estrutura de `CONTEXT`.</span><span class="sxs-lookup"><span data-stu-id="1866a-113">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="1866a-114">A estrutura de `CONTEXT` é específica do processador; consulte o arquivo WinNT. h para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="1866a-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1866a-115">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="1866a-115">Requirements</span></span>  
 <span data-ttu-id="1866a-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1866a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1866a-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1866a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1866a-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1866a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1866a-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1866a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1866a-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="1866a-120">See also</span></span>

- [<span data-ttu-id="1866a-121">Interface ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="1866a-121">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="1866a-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1866a-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="1866a-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="1866a-123">Debugging</span></span>](index.md)
