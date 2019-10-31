---
title: Método ICorDebugILFrame::GetLocalVariable
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetLocalVariable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetLocalVariable
helpviewer_keywords:
- ICorDebugILFrame::GetLocalVariable method [.NET Framework debugging]
- GetLocalVariable method [.NET Framework debugging]
ms.assetid: c8706356-d50b-4f87-a40c-39c3b7f4fd38
topic_type:
- apiref
ms.openlocfilehash: 85f06b49aab1f1d1745bd7e359ed311c2ba1e44d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130974"
---
# <a name="icordebugilframegetlocalvariable-method"></a><span data-ttu-id="a77d4-102">Método ICorDebugILFrame::GetLocalVariable</span><span class="sxs-lookup"><span data-stu-id="a77d4-102">ICorDebugILFrame::GetLocalVariable Method</span></span>
<span data-ttu-id="a77d4-103">Obtém o valor da variável local especificada neste quadro de ativação da MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="a77d4-103">Gets the value of the specified local variable in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a77d4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a77d4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a77d4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a77d4-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="a77d4-106">no O índice da variável local neste quadro da pilha MSIL.</span><span class="sxs-lookup"><span data-stu-id="a77d4-106">[in] The index of the local variable in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a77d4-107">fora Um ponteiro para o endereço de um objeto ICorDebugValue que representa o valor recuperado.</span><span class="sxs-lookup"><span data-stu-id="a77d4-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a77d4-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a77d4-108">Remarks</span></span>  
 <span data-ttu-id="a77d4-109">O método `GetLocalVariable` pode ser usado em um quadro de pilha MSIL ou em um quadro compilado JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="a77d4-109">The `GetLocalVariable` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a77d4-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a77d4-110">Requirements</span></span>  
 <span data-ttu-id="a77d4-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a77d4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a77d4-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a77d4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a77d4-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a77d4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a77d4-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a77d4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
