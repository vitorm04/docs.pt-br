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
ms.openlocfilehash: 1c11946bc5ea69a090091c014aba859935b48b36
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396670"
---
# <a name="icordebugtype2gettypeid-method"></a><span data-ttu-id="f7fcb-102">Método ICorDebugType2:: GetTypeId</span><span class="sxs-lookup"><span data-stu-id="f7fcb-102">ICorDebugType2::GetTypeID Method</span></span>
<span data-ttu-id="f7fcb-103">Obtém um [COR_TYPEID](cor-typeid-structure.md) para este tipo.</span><span class="sxs-lookup"><span data-stu-id="f7fcb-103">Gets a [COR_TYPEID](cor-typeid-structure.md) for this type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7fcb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7fcb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7fcb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f7fcb-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="f7fcb-106">fora Um ponteiro para a [COR_TYPEID](cor-typeid-structure.md) para este ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="f7fcb-106">[out] A pointer to the [COR_TYPEID](cor-typeid-structure.md) for this ICorDebugType.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7fcb-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f7fcb-107">Return Value</span></span>  
 <span data-ttu-id="f7fcb-108">O valor retornado é `S_OK` em caso de êxito, ou um código de falha `HRESULT` em caso de falha.</span><span class="sxs-lookup"><span data-stu-id="f7fcb-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="f7fcb-109">Os `HRESULT` códigos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f7fcb-109">The `HRESULT` codes include the following:</span></span>  
  
|<span data-ttu-id="f7fcb-110">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="f7fcb-110">Return code</span></span>|<span data-ttu-id="f7fcb-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7fcb-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="f7fcb-112">O método foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="f7fcb-112">Method succeeded.</span></span> <span data-ttu-id="f7fcb-113">O método recuperou um [COR_TYPEID](cor-typeid-structure.md)válido.</span><span class="sxs-lookup"><span data-stu-id="f7fcb-113">The method has retrieved a valid [COR_TYPEID](cor-typeid-structure.md).</span></span>|  
|`CORDBG_E_CLASS_NOT_LOADED`|<span data-ttu-id="f7fcb-114">O tipo não foi carregado.</span><span class="sxs-lookup"><span data-stu-id="f7fcb-114">The type has not been loaded.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="f7fcb-115">Não há suporte para o tipo.</span><span class="sxs-lookup"><span data-stu-id="f7fcb-115">The type is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7fcb-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="f7fcb-116">Remarks</span></span>  
 <span data-ttu-id="f7fcb-117">Esse método fornece um mapeamento do ICorDebugType, que representa um tipo que pode ou não ter sido carregado no tempo de execução, para um [COR_TYPEID](cor-typeid-structure.md), que serve como um identificador opaco que identifica um tipo carregado no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f7fcb-117">This method provides a mapping from the ICorDebugType, which represents a type that may or may not have been loaded into the runtime, to a [COR_TYPEID](cor-typeid-structure.md), which serves as an opaque handle that identifies a type loaded into the runtime.</span></span>  
  
 <span data-ttu-id="f7fcb-118">Quando o tipo que o ICorDebugType representa ainda não foi carregado, esse método retorna `CORDBG_E_CLASS_NOT_LOADED` .</span><span class="sxs-lookup"><span data-stu-id="f7fcb-118">When the type that the ICorDebugType represents has not yet been loaded, this method returns `CORDBG_E_CLASS_NOT_LOADED`.</span></span>  <span data-ttu-id="f7fcb-119">Se não houver suporte para o tipo, ele retornará `CORDBG_E_UNSUPPORTED` .</span><span class="sxs-lookup"><span data-stu-id="f7fcb-119">If the type is not supported, it returns `CORDBG_E_UNSUPPORTED`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7fcb-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f7fcb-120">Requirements</span></span>  
 <span data-ttu-id="f7fcb-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7fcb-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7fcb-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7fcb-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7fcb-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7fcb-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7fcb-124">**.NET Framework versões:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7fcb-124">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7fcb-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="f7fcb-125">See also</span></span>

- [<span data-ttu-id="f7fcb-126">Interface ICorDebugType2</span><span class="sxs-lookup"><span data-stu-id="f7fcb-126">ICorDebugType2 Interface</span></span>](icordebugtype2-interface.md)
