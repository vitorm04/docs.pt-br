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
ms.openlocfilehash: e06dc35998a2874ed1d2f76725078874817e94d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="e21cc-102">Método ICorDebugProcess::IsTransitionStub</span><span class="sxs-lookup"><span data-stu-id="e21cc-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="e21cc-103">Obtém um valor que indica se um endereço está dentro de um stub que fará com que uma transição para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e21cc-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e21cc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e21cc-104">Syntax</span></span>  
  
```  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e21cc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e21cc-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="e21cc-106">[in] Um `CORDB_ADDRESS` valor que especifica o endereço em questão.</span><span class="sxs-lookup"><span data-stu-id="e21cc-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="e21cc-107">[out] Um ponteiro para um valor booliano que é `true` se o endereço especificado está dentro de um stub que fará com que uma transição para código gerenciado; caso contrário \*`pbTransitionStub` é `false`.</span><span class="sxs-lookup"><span data-stu-id="e21cc-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e21cc-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="e21cc-108">Remarks</span></span>  
 <span data-ttu-id="e21cc-109">O `IsTransitionStub` método pode ser usado pelo revisão de código não gerenciado para decidir quando devolver o controle de revisão para o seletor gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e21cc-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="e21cc-110">Você também pode stubs de transição de identidade examinando as informações do arquivo executável portátil (PE).</span><span class="sxs-lookup"><span data-stu-id="e21cc-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e21cc-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e21cc-111">Requirements</span></span>  
 <span data-ttu-id="e21cc-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e21cc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e21cc-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e21cc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e21cc-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e21cc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e21cc-115">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e21cc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
