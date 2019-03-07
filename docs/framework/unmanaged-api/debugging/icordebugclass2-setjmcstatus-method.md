---
title: Método ICorDebugClass2::SetJMCStatus
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ed6570e11008e52d4b1f97c2dc90e2ccbef2e35
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471375"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="574e2-102">Método ICorDebugClass2::SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="574e2-102">ICorDebugClass2::SetJMCStatus Method</span></span>
<span data-ttu-id="574e2-103">Para cada método da classe, define um valor que indica se o método é o código definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="574e2-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="574e2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="574e2-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="574e2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="574e2-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="574e2-106">[in] Definido como `true` para indicar que o método é definido pelo usuário de código; caso contrário, é definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="574e2-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="574e2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="574e2-107">Remarks</span></span>  
 <span data-ttu-id="574e2-108">Um seletor do just my code (JMC) vai ignorar o código definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="574e2-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="574e2-109">Código definido pelo usuário deve ser um subconjunto de código depurável.</span><span class="sxs-lookup"><span data-stu-id="574e2-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="574e2-110">`SetJMCStatus` Retorna um valor HRESULT de S_FALSE se ele falhar ao definir o valor de qualquer método, mesmo que define o valor para todos os outros métodos com êxito.</span><span class="sxs-lookup"><span data-stu-id="574e2-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="574e2-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="574e2-111">Requirements</span></span>  
 <span data-ttu-id="574e2-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="574e2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="574e2-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="574e2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="574e2-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="574e2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="574e2-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="574e2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
