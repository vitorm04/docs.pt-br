---
title: Método ICorDebugProcess::IsTransitionStub
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18084cb69d2c620fc892cc05e5a561e8fda3bc1c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488182"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="35c64-102">Método ICorDebugProcess::IsTransitionStub</span><span class="sxs-lookup"><span data-stu-id="35c64-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="35c64-103">Obtém um valor que indica se um endereço está dentro de um stub que fará com que uma transição para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="35c64-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35c64-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35c64-104">Syntax</span></span>  
  
```  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35c64-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="35c64-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="35c64-106">[in] Um `CORDB_ADDRESS` valor que especifica o endereço em questão.</span><span class="sxs-lookup"><span data-stu-id="35c64-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="35c64-107">[out] Um ponteiro para um valor booliano que será `true` se o endereço especificado está dentro de um stub que fará com que uma transição para código gerenciado; caso contrário, \*`pbTransitionStub` é `false`.</span><span class="sxs-lookup"><span data-stu-id="35c64-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35c64-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="35c64-108">Remarks</span></span>  
 <span data-ttu-id="35c64-109">O `IsTransitionStub` método pode ser usado pelo código não gerenciado de passo a passo para decidir quando retornar o controle de revisão para o escalonador gerenciado.</span><span class="sxs-lookup"><span data-stu-id="35c64-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="35c64-110">Você também pode stubs de transição de identidade examinando informações no arquivo executável portátil (PE).</span><span class="sxs-lookup"><span data-stu-id="35c64-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35c64-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="35c64-111">Requirements</span></span>  
 <span data-ttu-id="35c64-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35c64-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35c64-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35c64-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35c64-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35c64-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35c64-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35c64-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
