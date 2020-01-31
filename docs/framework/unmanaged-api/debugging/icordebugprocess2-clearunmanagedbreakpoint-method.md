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
ms.openlocfilehash: e2aaf902afd71a4a81f7d64ef3fec046aacc91fc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792526"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="cfff6-102">Método ICorDebugProcess2::ClearUnmanagedBreakpoint</span><span class="sxs-lookup"><span data-stu-id="cfff6-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="cfff6-103">Remove um ponto de interrupção definido anteriormente no endereço fornecido.</span><span class="sxs-lookup"><span data-stu-id="cfff6-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfff6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cfff6-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfff6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cfff6-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="cfff6-106">no Um valor `CORDB_ADDRESS` que especifica o endereço no qual o ponto de interrupção foi definido.</span><span class="sxs-lookup"><span data-stu-id="cfff6-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfff6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="cfff6-107">Remarks</span></span>  
 <span data-ttu-id="cfff6-108">O ponto de interrupção especificado teria sido definido anteriormente por uma chamada anterior para [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="cfff6-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="cfff6-109">O método `ClearUnmanagedBreakpoint` pode ser chamado enquanto o processo que está sendo depurado está em execução.</span><span class="sxs-lookup"><span data-stu-id="cfff6-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="cfff6-110">O método `ClearUnmanagedBreakpoint` retornará um código de falha se o depurador estiver anexado no modo somente gerenciado ou se não existir nenhum ponto de interrupção no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="cfff6-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfff6-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="cfff6-111">Requirements</span></span>  
 <span data-ttu-id="cfff6-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfff6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfff6-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cfff6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfff6-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfff6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfff6-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfff6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
