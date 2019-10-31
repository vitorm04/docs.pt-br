---
title: Método ICorDebugClass::GetStaticFieldValue
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type:
- apiref
ms.openlocfilehash: 867db3325f9b18b31f66429d01ea02be3603c0f6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125757"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="8cec6-102">Método ICorDebugClass::GetStaticFieldValue</span><span class="sxs-lookup"><span data-stu-id="8cec6-102">ICorDebugClass::GetStaticFieldValue Method</span></span>
<span data-ttu-id="8cec6-103">Obtém o valor do campo estático especificado.</span><span class="sxs-lookup"><span data-stu-id="8cec6-103">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cec6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8cec6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cec6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8cec6-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="8cec6-106">no Um campo `Def` token que faz referência ao campo a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="8cec6-106">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="8cec6-107">no Um ponteiro para um objeto ICorDebugFrame que representa o quadro a ser usado para ambiguidade entre os estáticos de thread, contexto ou domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8cec6-107">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="8cec6-108">Se o campo estático for relativo a um thread, um contexto ou um domínio de aplicativo, o quadro determinará o valor adequado.</span><span class="sxs-lookup"><span data-stu-id="8cec6-108">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="8cec6-109">fora Um ponteiro para o endereço de um objeto ICorDebugValue que representa o valor do campo estático.</span><span class="sxs-lookup"><span data-stu-id="8cec6-109">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8cec6-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="8cec6-110">Remarks</span></span>  
 <span data-ttu-id="8cec6-111">Para tipos com parâmetros, o valor de um campo estático é relativo à instanciação específica.</span><span class="sxs-lookup"><span data-stu-id="8cec6-111">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="8cec6-112">Portanto, se o construtor de classe usar parâmetros do tipo <xref:System.Type>, chame [ICorDebugType:: GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) em vez de `ICorDebugClass::GetStaticFieldValue`.</span><span class="sxs-lookup"><span data-stu-id="8cec6-112">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cec6-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8cec6-113">Requirements</span></span>  
 <span data-ttu-id="8cec6-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cec6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cec6-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8cec6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8cec6-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8cec6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8cec6-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cec6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
