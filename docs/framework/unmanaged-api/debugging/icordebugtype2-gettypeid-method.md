---
title: 'Método ICorDebugType2:: GetTypeId'
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
ms.openlocfilehash: 944313893d88b8eff97291d2517e4863a5ae958a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092756"
---
# <a name="icordebugtype2gettypeid-method"></a><span data-ttu-id="f13e6-102">Método ICorDebugType2:: GetTypeId</span><span class="sxs-lookup"><span data-stu-id="f13e6-102">ICorDebugType2::GetTypeID Method</span></span>
<span data-ttu-id="f13e6-103">Obtém um [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) para este tipo.</span><span class="sxs-lookup"><span data-stu-id="f13e6-103">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f13e6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f13e6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f13e6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f13e6-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="f13e6-106">fora Um ponteiro para o [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) para este ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="f13e6-106">[out] A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this ICorDebugType.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f13e6-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f13e6-107">Return Value</span></span>  
 <span data-ttu-id="f13e6-108">O valor retornado é `S_OK` em caso de êxito, ou um código de falha `HRESULT` em caso de falha.</span><span class="sxs-lookup"><span data-stu-id="f13e6-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="f13e6-109">Os códigos de `HRESULT` incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f13e6-109">The `HRESULT` codes include the following:</span></span>  
  
|<span data-ttu-id="f13e6-110">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="f13e6-110">Return code</span></span>|<span data-ttu-id="f13e6-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f13e6-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="f13e6-112">O método foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="f13e6-112">Method succeeded.</span></span> <span data-ttu-id="f13e6-113">O método recuperou um [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)válido.</span><span class="sxs-lookup"><span data-stu-id="f13e6-113">The method has retrieved a valid [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span></span>|  
|`CORDBG_E_CLASS_NOT_LOADED`|<span data-ttu-id="f13e6-114">O tipo não foi carregado.</span><span class="sxs-lookup"><span data-stu-id="f13e6-114">The type has not been loaded.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="f13e6-115">Não há suporte para o tipo.</span><span class="sxs-lookup"><span data-stu-id="f13e6-115">The type is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f13e6-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="f13e6-116">Remarks</span></span>  
 <span data-ttu-id="f13e6-117">Esse método fornece um mapeamento do ICorDebugType, que representa um tipo que pode ou não ter sido carregado no tempo de execução, para um [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), que serve como um identificador opaco que identifica um tipo carregado no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f13e6-117">This method provides a mapping from the ICorDebugType, which represents a type that may or may not have been loaded into the runtime, to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which serves as an opaque handle that identifies a type loaded into the runtime.</span></span>  
  
 <span data-ttu-id="f13e6-118">Quando o tipo que o ICorDebugType representa ainda não foi carregado, esse método retorna `CORDBG_E_CLASS_NOT_LOADED`.</span><span class="sxs-lookup"><span data-stu-id="f13e6-118">When the type that the ICorDebugType represents has not yet been loaded, this method returns `CORDBG_E_CLASS_NOT_LOADED`.</span></span>  <span data-ttu-id="f13e6-119">Se não houver suporte para o tipo, ele retornará `CORDBG_E_UNSUPPORTED`.</span><span class="sxs-lookup"><span data-stu-id="f13e6-119">If the type is not supported, it returns `CORDBG_E_UNSUPPORTED`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f13e6-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f13e6-120">Requirements</span></span>  
 <span data-ttu-id="f13e6-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f13e6-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f13e6-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f13e6-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f13e6-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f13e6-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f13e6-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f13e6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f13e6-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f13e6-125">See also</span></span>

- [<span data-ttu-id="f13e6-126">Interface ICorDebugType2</span><span class="sxs-lookup"><span data-stu-id="f13e6-126">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
