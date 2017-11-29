---
title: "Método ICorDebugRegisterSet::SetThreadContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet.SetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet::SetThreadContext
helpviewer_keywords:
- ICorDebugRegisterSet::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 73afa930-32cb-4c40-81f8-83e8e6fbe213
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9a97706e5cf407f16b6d06efce11576fbb131d1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="c2a6b-102">Método ICorDebugRegisterSet::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="c2a6b-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>
<span data-ttu-id="c2a6b-103">`SetThreadContext`não é implementado no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="c2a6b-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="c2a6b-104">Não chame este método.</span><span class="sxs-lookup"><span data-stu-id="c2a6b-104">Do not call this method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2a6b-105">Use a operação de nível mais alto [Icordebugnativeframe](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) para definir o contexto de thread.</span><span class="sxs-lookup"><span data-stu-id="c2a6b-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2a6b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2a6b-106">Syntax</span></span>  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="c2a6b-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2a6b-107">Requirements</span></span>  
 <span data-ttu-id="c2a6b-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2a6b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2a6b-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2a6b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2a6b-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2a6b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2a6b-111">**Versões do .NET framework:** 1.1 e 1.0</span><span class="sxs-lookup"><span data-stu-id="c2a6b-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2a6b-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2a6b-112">See Also</span></span>  
 [<span data-ttu-id="c2a6b-113">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="c2a6b-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="c2a6b-114">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="c2a6b-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
