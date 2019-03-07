---
title: Método ICorDebugCode::CreateBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df27d2ab609551bb7a7f6f4b0ff8c7118c9f93f8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478668"
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="f91e0-102">Método ICorDebugCode::CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="f91e0-102">ICorDebugCode::CreateBreakpoint Method</span></span>
<span data-ttu-id="f91e0-103">Cria um ponto de interrupção neste segmento de código no deslocamento especificado.</span><span class="sxs-lookup"><span data-stu-id="f91e0-103">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f91e0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f91e0-104">Syntax</span></span>  
  
```  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f91e0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f91e0-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="f91e0-106">[in] O deslocamento no qual criar o ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="f91e0-106">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="f91e0-107">[out] Um ponteiro para o endereço de um objeto de "ICorDebugFunctionBreakpoint" que representa o ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="f91e0-107">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f91e0-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="f91e0-108">Remarks</span></span>  
 <span data-ttu-id="f91e0-109">Antes do ponto de interrupção estiver ativo, ele deve ser adicionado ao objeto do processo.</span><span class="sxs-lookup"><span data-stu-id="f91e0-109">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="f91e0-110">Se esse código é o código Microsoft intermediate language (MSIL), e há um just-in-time (JIT)-versão compilada, nativo do código, o ponto de interrupção será aplicado o código de compilação JIT.</span><span class="sxs-lookup"><span data-stu-id="f91e0-110">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="f91e0-111">(O mesmo é verdadeiro se o código é compilado por JIT mais tarde.)</span><span class="sxs-lookup"><span data-stu-id="f91e0-111">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f91e0-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f91e0-112">Requirements</span></span>  
 <span data-ttu-id="f91e0-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f91e0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f91e0-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f91e0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f91e0-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f91e0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f91e0-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f91e0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f91e0-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f91e0-117">See also</span></span>

