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
ms.openlocfilehash: ea7630efedb7b667dc58174eda0cb98d9f382cfc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792383"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="edaa3-102">Método ICorDebugProcess5::GetArrayLayout</span><span class="sxs-lookup"><span data-stu-id="edaa3-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="edaa3-103">Fornece informações sobre o layout de tipos de matriz.</span><span class="sxs-lookup"><span data-stu-id="edaa3-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edaa3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="edaa3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="edaa3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="edaa3-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="edaa3-106">no Um [COR_TYPEID](cor-typeid-structure.md) token que especifica a matriz cujo layout é desejado.</span><span class="sxs-lookup"><span data-stu-id="edaa3-106">[in] A [COR_TYPEID](cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="edaa3-107">fora Um ponteiro para uma estrutura de [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) que contém informações sobre o layout da matriz na memória.</span><span class="sxs-lookup"><span data-stu-id="edaa3-107">[out] A pointer to a [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edaa3-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="edaa3-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edaa3-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="edaa3-109">Requirements</span></span>  
 <span data-ttu-id="edaa3-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edaa3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edaa3-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="edaa3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="edaa3-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edaa3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edaa3-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edaa3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edaa3-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="edaa3-114">See also</span></span>

- [<span data-ttu-id="edaa3-115">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="edaa3-115">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="edaa3-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="edaa3-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
