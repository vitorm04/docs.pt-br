---
title: Método ICorDebugFrame::GetStackRange
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5da87071bc23ac17a3077049cd77f0fb8611439f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413014"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="914c0-102">Método ICorDebugFrame::GetStackRange</span><span class="sxs-lookup"><span data-stu-id="914c0-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="914c0-103">Obtém o intervalo de endereços absolutos deste quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="914c0-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="914c0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="914c0-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="914c0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="914c0-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="914c0-106">[out] Um ponteiro para um `CORDB_ADDRESS` que especifica o endereço inicial do quadro de pilhas representado por esse `ICorDebugFrame` objeto.</span><span class="sxs-lookup"><span data-stu-id="914c0-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="914c0-107">[out] Um ponteiro para um `CORDB_ADDRESS` que especifica o endereço final do quadro de pilhas representado por esse `ICorDebugFrame` objeto.</span><span class="sxs-lookup"><span data-stu-id="914c0-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="914c0-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="914c0-108">Remarks</span></span>  
 <span data-ttu-id="914c0-109">O intervalo de endereços da pilha é útil para juntando rastreamentos de pilha intercalada coletados a partir de vários mecanismos de depuração.</span><span class="sxs-lookup"><span data-stu-id="914c0-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="914c0-110">O intervalo numérico não fornece nenhuma informação sobre o conteúdo do quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="914c0-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="914c0-111">Faz sentido somente para comparação de locais de quadro de pilha.</span><span class="sxs-lookup"><span data-stu-id="914c0-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="914c0-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="914c0-112">Requirements</span></span>  
 <span data-ttu-id="914c0-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="914c0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="914c0-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="914c0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="914c0-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="914c0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="914c0-116">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="914c0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
