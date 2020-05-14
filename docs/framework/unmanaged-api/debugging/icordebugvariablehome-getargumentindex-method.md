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
ms.openlocfilehash: 27a676fd1d2d7903943e44f8a7201b88af4fba89
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397002"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="d695e-102">Método ICorDebugVariableHome:: GetArgumentIndex</span><span class="sxs-lookup"><span data-stu-id="d695e-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>

<span data-ttu-id="d695e-103">Obtém o índice de um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="d695e-103">Gets the index of a function argument.</span></span>

## <a name="syntax"></a><span data-ttu-id="d695e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d695e-104">Syntax</span></span>

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a><span data-ttu-id="d695e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d695e-105">Parameters</span></span>

`pArgumentIndex`\
<span data-ttu-id="d695e-106">fora Um ponteiro para o índice de argumento.</span><span class="sxs-lookup"><span data-stu-id="d695e-106">[out] A pointer to the argument index.</span></span>

## <a name="return-value"></a><span data-ttu-id="d695e-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d695e-107">Return Value</span></span>

<span data-ttu-id="d695e-108">O método retorna os valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="d695e-108">The method returns the following values.</span></span>

|<span data-ttu-id="d695e-109">Valor</span><span class="sxs-lookup"><span data-stu-id="d695e-109">Value</span></span>|<span data-ttu-id="d695e-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="d695e-110">Description</span></span>|
|-----------|-----------------|
|`S_OK`|<span data-ttu-id="d695e-111">A chamada do método retornou um índice de argumento válido.</span><span class="sxs-lookup"><span data-stu-id="d695e-111">The method call returned a valid argument index.</span></span>|
|`E_FAIL`|<span data-ttu-id="d695e-112">A instância [ICorDebugVariableHome](icordebugvariablehome-interface.md) atual representa uma variável local.</span><span class="sxs-lookup"><span data-stu-id="d695e-112">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d695e-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="d695e-113">Remarks</span></span>

<span data-ttu-id="d695e-114">O índice de argumento pode ser usado para recuperar metadados para esse argumento.</span><span class="sxs-lookup"><span data-stu-id="d695e-114">The argument index can be used to retrieve metadata for this argument.</span></span>

## <a name="requirements"></a><span data-ttu-id="d695e-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d695e-115">Requirements</span></span>

<span data-ttu-id="d695e-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d695e-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="d695e-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d695e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="d695e-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d695e-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="d695e-119">**.NET Framework versões:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d695e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d695e-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="d695e-120">See also</span></span>

- [<span data-ttu-id="d695e-121">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="d695e-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
