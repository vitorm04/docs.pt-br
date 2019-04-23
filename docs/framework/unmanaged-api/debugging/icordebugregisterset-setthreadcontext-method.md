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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b1ea34c187de99d23b05b5e1a30c53bc54a6c0c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197393"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="cb003-102">Método ICorDebugRegisterSet::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="cb003-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>
<span data-ttu-id="cb003-103">`SetThreadContext` não é implementada no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="cb003-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="cb003-104">Não chame este método.</span><span class="sxs-lookup"><span data-stu-id="cb003-104">Do not call this method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb003-105">Use a operação de nível mais alto [icordebugnativeframe:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) para definir o contexto de um thread.</span><span class="sxs-lookup"><span data-stu-id="cb003-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb003-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb003-106">Syntax</span></span>  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="cb003-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cb003-107">Requirements</span></span>  
 <span data-ttu-id="cb003-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb003-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb003-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb003-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb003-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb003-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb003-111">**Versões do .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="cb003-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb003-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb003-112">See also</span></span>

- [<span data-ttu-id="cb003-113">Interface ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="cb003-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="cb003-114">Interface ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="cb003-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
