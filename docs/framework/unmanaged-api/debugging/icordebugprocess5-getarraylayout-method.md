---
title: Método ICorDebugProcess5::GetArrayLayout
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetArrayLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type:
- apiref
ms.openlocfilehash: aac3d54d25b50d0e2ce3e93cdfba5a17679e1f76
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209663"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="4157a-102">Método ICorDebugProcess5::GetArrayLayout</span><span class="sxs-lookup"><span data-stu-id="4157a-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="4157a-103">Fornece informações sobre o layout de tipos de matriz.</span><span class="sxs-lookup"><span data-stu-id="4157a-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4157a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4157a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4157a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4157a-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="4157a-106">no Um [COR_TYPEID](cor-typeid-structure.md) token que especifica a matriz cujo layout é desejado.</span><span class="sxs-lookup"><span data-stu-id="4157a-106">[in] A [COR_TYPEID](cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="4157a-107">fora Um ponteiro para uma estrutura de [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) que contém informações sobre o layout da matriz na memória.</span><span class="sxs-lookup"><span data-stu-id="4157a-107">[out] A pointer to a [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4157a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="4157a-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4157a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4157a-109">Requirements</span></span>  
 <span data-ttu-id="4157a-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4157a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4157a-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4157a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4157a-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4157a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4157a-113">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4157a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4157a-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="4157a-114">See also</span></span>

- [<span data-ttu-id="4157a-115">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="4157a-115">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="4157a-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4157a-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
