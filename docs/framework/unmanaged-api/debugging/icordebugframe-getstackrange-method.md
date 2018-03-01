---
title: "Método ICorDebugFrame::GetStackRange"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3c4c9c0a531d93ca2c7c72f50bcd2f7ee98887e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="eeea4-102">Método ICorDebugFrame::GetStackRange</span><span class="sxs-lookup"><span data-stu-id="eeea4-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="eeea4-103">Obtém o intervalo de endereços absolutos deste quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="eeea4-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eeea4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eeea4-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eeea4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eeea4-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="eeea4-106">[out] Um ponteiro para um `CORDB_ADDRESS` que especifica o endereço inicial do quadro de pilhas representado por esse `ICorDebugFrame` objeto.</span><span class="sxs-lookup"><span data-stu-id="eeea4-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="eeea4-107">[out] Um ponteiro para um `CORDB_ADDRESS` que especifica o endereço final do quadro de pilhas representado por esse `ICorDebugFrame` objeto.</span><span class="sxs-lookup"><span data-stu-id="eeea4-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eeea4-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="eeea4-108">Remarks</span></span>  
 <span data-ttu-id="eeea4-109">O intervalo de endereços da pilha é útil para juntando rastreamentos de pilha intercalada coletados a partir de vários mecanismos de depuração.</span><span class="sxs-lookup"><span data-stu-id="eeea4-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="eeea4-110">O intervalo numérico não fornece nenhuma informação sobre o conteúdo do quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="eeea4-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="eeea4-111">Faz sentido somente para comparação de locais de quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="eeea4-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eeea4-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eeea4-112">Requirements</span></span>  
 <span data-ttu-id="eeea4-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eeea4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eeea4-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eeea4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eeea4-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eeea4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eeea4-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eeea4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
