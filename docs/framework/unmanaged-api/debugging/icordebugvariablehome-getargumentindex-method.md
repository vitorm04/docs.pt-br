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
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366823"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="f5f36-102">Método ICorDebugVariableHome::GetArgumentIndex</span><span class="sxs-lookup"><span data-stu-id="f5f36-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>

<span data-ttu-id="f5f36-103">Obtém o índice de um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="f5f36-103">Gets the index of a function argument.</span></span>

## <a name="syntax"></a><span data-ttu-id="f5f36-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5f36-104">Syntax</span></span>

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a><span data-ttu-id="f5f36-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f5f36-105">Parameters</span></span>

`pArgumentIndex`\
<span data-ttu-id="f5f36-106">[out] Um ponteiro para o índice do argumento.</span><span class="sxs-lookup"><span data-stu-id="f5f36-106">[out] A pointer to the argument index.</span></span>

## <a name="return-value"></a><span data-ttu-id="f5f36-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f5f36-107">Return Value</span></span>

<span data-ttu-id="f5f36-108">O método retorna os valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="f5f36-108">The method returns the following values.</span></span>

|<span data-ttu-id="f5f36-109">Valor</span><span class="sxs-lookup"><span data-stu-id="f5f36-109">Value</span></span>|<span data-ttu-id="f5f36-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5f36-110">Description</span></span>|
|-----------|-----------------|
|`S_OK`|<span data-ttu-id="f5f36-111">A chamada de método retornou um índice de argumento válido.</span><span class="sxs-lookup"><span data-stu-id="f5f36-111">The method call returned a valid argument index.</span></span>|
|`E_FAIL`|<span data-ttu-id="f5f36-112">O atual [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instância representa uma variável local.</span><span class="sxs-lookup"><span data-stu-id="f5f36-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f5f36-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="f5f36-113">Remarks</span></span>

<span data-ttu-id="f5f36-114">O índice do argumento pode ser usado para recuperar metadados para esse argumento.</span><span class="sxs-lookup"><span data-stu-id="f5f36-114">The argument index can be used to retrieve metadata for this argument.</span></span>

## <a name="requirements"></a><span data-ttu-id="f5f36-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f5f36-115">Requirements</span></span>

<span data-ttu-id="f5f36-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5f36-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="f5f36-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5f36-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="f5f36-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5f36-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="f5f36-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5f36-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f5f36-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5f36-120">See also</span></span>

- [<span data-ttu-id="f5f36-121">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="f5f36-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
