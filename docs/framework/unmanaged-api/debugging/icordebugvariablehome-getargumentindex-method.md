---
title: 'Método ICorDebugVariableHome:: GetArgumentIndex'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
ms.openlocfilehash: 86b2815c6f95c674c49bba7455e8497192bd8bac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125146"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="06260-102">Método ICorDebugVariableHome:: GetArgumentIndex</span><span class="sxs-lookup"><span data-stu-id="06260-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>

<span data-ttu-id="06260-103">Obtém o índice de um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="06260-103">Gets the index of a function argument.</span></span>

## <a name="syntax"></a><span data-ttu-id="06260-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06260-104">Syntax</span></span>

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a><span data-ttu-id="06260-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="06260-105">Parameters</span></span>

`pArgumentIndex`\
<span data-ttu-id="06260-106">fora Um ponteiro para o índice de argumento.</span><span class="sxs-lookup"><span data-stu-id="06260-106">[out] A pointer to the argument index.</span></span>

## <a name="return-value"></a><span data-ttu-id="06260-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="06260-107">Return Value</span></span>

<span data-ttu-id="06260-108">O método retorna os valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="06260-108">The method returns the following values.</span></span>

|<span data-ttu-id="06260-109">Valor</span><span class="sxs-lookup"><span data-stu-id="06260-109">Value</span></span>|<span data-ttu-id="06260-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="06260-110">Description</span></span>|
|-----------|-----------------|
|`S_OK`|<span data-ttu-id="06260-111">A chamada do método retornou um índice de argumento válido.</span><span class="sxs-lookup"><span data-stu-id="06260-111">The method call returned a valid argument index.</span></span>|
|`E_FAIL`|<span data-ttu-id="06260-112">A instância [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) atual representa uma variável local.</span><span class="sxs-lookup"><span data-stu-id="06260-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|

## <a name="remarks"></a><span data-ttu-id="06260-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="06260-113">Remarks</span></span>

<span data-ttu-id="06260-114">O índice de argumento pode ser usado para recuperar metadados para esse argumento.</span><span class="sxs-lookup"><span data-stu-id="06260-114">The argument index can be used to retrieve metadata for this argument.</span></span>

## <a name="requirements"></a><span data-ttu-id="06260-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="06260-115">Requirements</span></span>

<span data-ttu-id="06260-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06260-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="06260-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06260-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="06260-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06260-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="06260-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06260-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="06260-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06260-120">See also</span></span>

- [<span data-ttu-id="06260-121">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="06260-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
