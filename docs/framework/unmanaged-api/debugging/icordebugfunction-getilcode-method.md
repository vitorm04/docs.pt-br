---
title: Método ICorDebugFunction::GetILCode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
ms.openlocfilehash: 8c7be2d48a30a9f649c6d86e4edbc10085195b68
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213615"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="ac83f-102">Método ICorDebugFunction::GetILCode</span><span class="sxs-lookup"><span data-stu-id="ac83f-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="ac83f-103">Obtém a instância ICorDebugCode que representa o código MSIL (Microsoft Intermediate Language) associado a este objeto ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="ac83f-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac83f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac83f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac83f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac83f-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="ac83f-106">fora Um ponteiro para a `ICorDebugCode` instância, ou NULL, se a função não foi compilada em MSIL.</span><span class="sxs-lookup"><span data-stu-id="ac83f-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac83f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac83f-107">Remarks</span></span>  
 <span data-ttu-id="ac83f-108">Se editar e continuar tiver sido permitido nessa função, o `GetILCode` método obterá o código MSIL correspondente à versão editada da função do código no Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ac83f-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac83f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac83f-109">Requirements</span></span>  
 <span data-ttu-id="ac83f-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac83f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac83f-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac83f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac83f-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac83f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac83f-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac83f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
