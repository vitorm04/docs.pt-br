---
title: Método ICorDebugProcess2::ClearUnmanagedBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type:
- apiref
ms.openlocfilehash: 8377ead42c752d8ebe9813d9e00662b94339f8a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137239"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="ad824-102">Método ICorDebugProcess2::ClearUnmanagedBreakpoint</span><span class="sxs-lookup"><span data-stu-id="ad824-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="ad824-103">Remove um ponto de interrupção definido anteriormente no endereço fornecido.</span><span class="sxs-lookup"><span data-stu-id="ad824-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad824-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad824-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad824-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ad824-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="ad824-106">no Um valor `CORDB_ADDRESS` que especifica o endereço no qual o ponto de interrupção foi definido.</span><span class="sxs-lookup"><span data-stu-id="ad824-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad824-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ad824-107">Remarks</span></span>  
 <span data-ttu-id="ad824-108">O ponto de interrupção especificado teria sido definido anteriormente por uma chamada anterior para [ICorDebugProcess2:: SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="ad824-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="ad824-109">O método `ClearUnmanagedBreakpoint` pode ser chamado enquanto o processo que está sendo depurado está em execução.</span><span class="sxs-lookup"><span data-stu-id="ad824-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="ad824-110">O método `ClearUnmanagedBreakpoint` retornará um código de falha se o depurador estiver anexado no modo somente gerenciado ou se não existir nenhum ponto de interrupção no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="ad824-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad824-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad824-111">Requirements</span></span>  
 <span data-ttu-id="ad824-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad824-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad824-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad824-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad824-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad824-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad824-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad824-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
