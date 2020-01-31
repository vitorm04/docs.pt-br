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
ms.openlocfilehash: 873dd5a1eb2c9356049d2d0c0cb495b963c2ae46
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784187"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="6039b-102">Método ICorDebugClass::GetStaticFieldValue</span><span class="sxs-lookup"><span data-stu-id="6039b-102">ICorDebugClass::GetStaticFieldValue Method</span></span>
<span data-ttu-id="6039b-103">Obtém o valor do campo estático especificado.</span><span class="sxs-lookup"><span data-stu-id="6039b-103">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6039b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6039b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6039b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6039b-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="6039b-106">no Um campo `Def` token que faz referência ao campo a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="6039b-106">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="6039b-107">no Um ponteiro para um objeto ICorDebugFrame que representa o quadro a ser usado para ambiguidade entre os estáticos de thread, contexto ou domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6039b-107">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="6039b-108">Se o campo estático for relativo a um thread, um contexto ou um domínio de aplicativo, o quadro determinará o valor adequado.</span><span class="sxs-lookup"><span data-stu-id="6039b-108">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="6039b-109">fora Um ponteiro para o endereço de um objeto ICorDebugValue que representa o valor do campo estático.</span><span class="sxs-lookup"><span data-stu-id="6039b-109">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6039b-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="6039b-110">Remarks</span></span>  
 <span data-ttu-id="6039b-111">Para tipos com parâmetros, o valor de um campo estático é relativo à instanciação específica.</span><span class="sxs-lookup"><span data-stu-id="6039b-111">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="6039b-112">Portanto, se o construtor de classe usar parâmetros do tipo <xref:System.Type>, chame [ICorDebugType:: GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) em vez de `ICorDebugClass::GetStaticFieldValue`.</span><span class="sxs-lookup"><span data-stu-id="6039b-112">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6039b-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="6039b-113">Requirements</span></span>  
 <span data-ttu-id="6039b-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6039b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6039b-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6039b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6039b-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6039b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6039b-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6039b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
