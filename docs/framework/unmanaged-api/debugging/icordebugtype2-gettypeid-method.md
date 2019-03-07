---
title: Método ICorDebugType2::GetTypeID
ms.date: 03/30/2017
api_name:
- ICorDebugType2.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54b3f8e931507e53809a2419ab7f06e63eb70c10
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497633"
---
# <a name="icordebugtype2gettypeid-method"></a><span data-ttu-id="d7759-102">Método ICorDebugType2::GetTypeID</span><span class="sxs-lookup"><span data-stu-id="d7759-102">ICorDebugType2::GetTypeID Method</span></span>
<span data-ttu-id="d7759-103">Obtém uma [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) para esse tipo.</span><span class="sxs-lookup"><span data-stu-id="d7759-103">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7759-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7759-104">Syntax</span></span>  
  
```  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7759-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d7759-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="d7759-106">[out] Um ponteiro para o [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) para este ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="d7759-106">[out] A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this ICorDebugType.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7759-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d7759-107">Return Value</span></span>  
 <span data-ttu-id="d7759-108">O valor retornado é `S_OK` em caso de êxito, ou um código de falha `HRESULT` em caso de falha.</span><span class="sxs-lookup"><span data-stu-id="d7759-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="d7759-109">O `HRESULT` códigos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d7759-109">The `HRESULT` codes include the following:</span></span>  
  
|<span data-ttu-id="d7759-110">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="d7759-110">Return code</span></span>|<span data-ttu-id="d7759-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7759-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="d7759-112">O método foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="d7759-112">Method succeeded.</span></span> <span data-ttu-id="d7759-113">O método recuperou válida [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span><span class="sxs-lookup"><span data-stu-id="d7759-113">The method has retrieved a valid [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span></span>|  
|`CORDBG_E_CLASS_NOT_LOADED`|<span data-ttu-id="d7759-114">O tipo não foi carregado.</span><span class="sxs-lookup"><span data-stu-id="d7759-114">The type has not been loaded.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="d7759-115">Não há suporte para o tipo.</span><span class="sxs-lookup"><span data-stu-id="d7759-115">The type is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7759-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="d7759-116">Remarks</span></span>  
 <span data-ttu-id="d7759-117">Esse método fornece um mapeamento de ICorDebugType, que representa um tipo que pode, ou pode não ter sido carregado no tempo de execução, como uma [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), que serve como opaco identificador que identifica um tipo carregado no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d7759-117">This method provides a mapping from the ICorDebugType, which represents a type that may or may not have been loaded into the runtime, to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which serves as an opaque handle that identifies a type loaded into the runtime.</span></span>  
  
 <span data-ttu-id="d7759-118">Quando o tipo que representa o ICorDebugType ainda não foi carregado, esse método retornará `CORDBG_E_CLASS_NOT_LOADED`.</span><span class="sxs-lookup"><span data-stu-id="d7759-118">When the type that the ICorDebugType represents has not yet been loaded, this method returns `CORDBG_E_CLASS_NOT_LOADED`.</span></span>  <span data-ttu-id="d7759-119">Se não há suporte para o tipo, ele retorna `CORDBG_E_UNSUPPORTED`.</span><span class="sxs-lookup"><span data-stu-id="d7759-119">If the type is not supported, it returns `CORDBG_E_UNSUPPORTED`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7759-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d7759-120">Requirements</span></span>  
 <span data-ttu-id="d7759-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7759-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7759-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7759-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7759-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7759-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7759-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7759-124">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7759-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7759-125">See also</span></span>
- [<span data-ttu-id="d7759-126">Interface ICorDebugType2</span><span class="sxs-lookup"><span data-stu-id="d7759-126">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
