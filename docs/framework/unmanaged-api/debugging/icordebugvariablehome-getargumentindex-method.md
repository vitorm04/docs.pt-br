---
title: Método ICorDebugVariableHome::GetArgumentIndex
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2457dff3063e47f1fb9d040caac1bc08441e1739
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986785"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="ad3d5-102">Método ICorDebugVariableHome::GetArgumentIndex</span><span class="sxs-lookup"><span data-stu-id="ad3d5-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>

<span data-ttu-id="ad3d5-103">Obtém o índice de um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="ad3d5-103">Gets the index of a function argument.</span></span>

## <a name="syntax"></a><span data-ttu-id="ad3d5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad3d5-104">Syntax</span></span>

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a><span data-ttu-id="ad3d5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ad3d5-105">Parameters</span></span>

`pArgumentIndex`\
<span data-ttu-id="ad3d5-106">[out] Um ponteiro para o índice do argumento.</span><span class="sxs-lookup"><span data-stu-id="ad3d5-106">[out] A pointer to the argument index.</span></span>

## <a name="return-value"></a><span data-ttu-id="ad3d5-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ad3d5-107">Return Value</span></span>

<span data-ttu-id="ad3d5-108">O método retorna os valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="ad3d5-108">The method returns the following values.</span></span>

|<span data-ttu-id="ad3d5-109">Valor</span><span class="sxs-lookup"><span data-stu-id="ad3d5-109">Value</span></span>|<span data-ttu-id="ad3d5-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad3d5-110">Description</span></span>|
|-----------|-----------------|
|`S_OK`|<span data-ttu-id="ad3d5-111">A chamada de método retornou um índice de argumento válido.</span><span class="sxs-lookup"><span data-stu-id="ad3d5-111">The method call returned a valid argument index.</span></span>|
|`E_FAIL`|<span data-ttu-id="ad3d5-112">O atual [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instância representa uma variável local.</span><span class="sxs-lookup"><span data-stu-id="ad3d5-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ad3d5-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="ad3d5-113">Remarks</span></span>

<span data-ttu-id="ad3d5-114">O índice do argumento pode ser usado para recuperar metadados para esse argumento.</span><span class="sxs-lookup"><span data-stu-id="ad3d5-114">The argument index can be used to retrieve metadata for this argument.</span></span>

## <a name="requirements"></a><span data-ttu-id="ad3d5-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad3d5-115">Requirements</span></span>

<span data-ttu-id="ad3d5-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad3d5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="ad3d5-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad3d5-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="ad3d5-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad3d5-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="ad3d5-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad3d5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ad3d5-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad3d5-120">See also</span></span>

- [<span data-ttu-id="ad3d5-121">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="ad3d5-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
