---
title: Método ICorDebugRegisterSet::SetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetThreadContext
helpviewer_keywords:
- ICorDebugRegisterSet::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 73afa930-32cb-4c40-81f8-83e8e6fbe213
topic_type:
- apiref
ms.openlocfilehash: dc2a41524d3fafe1cb45c9494d80aabe7dae0ed8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792036"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="b7023-102">Método ICorDebugRegisterSet::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="b7023-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>
<span data-ttu-id="b7023-103">`SetThreadContext` não está implementado na versão .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="b7023-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="b7023-104">Não chame esse método.</span><span class="sxs-lookup"><span data-stu-id="b7023-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7023-105">Use a operação de nível superior [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md) para definir o contexto de um thread.</span><span class="sxs-lookup"><span data-stu-id="b7023-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7023-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7023-106">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="b7023-107">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="b7023-107">Requirements</span></span>  
 <span data-ttu-id="b7023-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7023-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7023-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7023-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7023-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7023-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7023-111">**Versões do .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="b7023-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7023-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="b7023-112">See also</span></span>

- [<span data-ttu-id="b7023-113">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="b7023-113">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="b7023-114">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="b7023-114">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
