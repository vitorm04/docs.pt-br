---
title: Método ICorDebug::DebugActiveProcess
ms.date: 03/30/2017
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b880358ed0d7bce4896217bc07c6ef6268d62962
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076270"
---
# <a name="icordebugdebugactiveprocess-method"></a><span data-ttu-id="80aa1-102">Método ICorDebug::DebugActiveProcess</span><span class="sxs-lookup"><span data-stu-id="80aa1-102">ICorDebug::DebugActiveProcess Method</span></span>
<span data-ttu-id="80aa1-103">Anexa o depurador a um processo existente.</span><span class="sxs-lookup"><span data-stu-id="80aa1-103">Attaches the debugger to an existing process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80aa1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80aa1-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80aa1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="80aa1-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="80aa1-106">[in] A ID do processo ao qual o depurador deve ser anexado.</span><span class="sxs-lookup"><span data-stu-id="80aa1-106">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="80aa1-107">[in] Valor booliano que é definido como `true` se o depurador deve se comportar como o depurador do Win32 para o processo e expedir os retornos de chamada não gerenciados; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="80aa1-107">[in] Boolean value that is set to `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="80aa1-108">[out] Um ponteiro para o endereço de um objeto de "ICorDebugProcess" que representa o processo ao qual o depurador foi anexado.</span><span class="sxs-lookup"><span data-stu-id="80aa1-108">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80aa1-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="80aa1-109">Remarks</span></span>  
 <span data-ttu-id="80aa1-110">Não há suporte para depuração Interop em plataformas Win9x e não x86, como plataformas baseadas em IA-64 e com base em AMD64.</span><span class="sxs-lookup"><span data-stu-id="80aa1-110">Interop debugging is not supported on Win9x and non-x86 platforms, such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80aa1-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80aa1-111">Requirements</span></span>  
 <span data-ttu-id="80aa1-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80aa1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80aa1-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80aa1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80aa1-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80aa1-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="80aa1-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="80aa1-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="80aa1-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80aa1-116">See also</span></span>

- [<span data-ttu-id="80aa1-117">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="80aa1-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
