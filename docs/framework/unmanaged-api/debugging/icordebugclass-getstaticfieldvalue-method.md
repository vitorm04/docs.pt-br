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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d3c3c0c5634653d14577de9a1334048d75216b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="1b9a5-102">Método ICorDebugClass::GetStaticFieldValue</span><span class="sxs-lookup"><span data-stu-id="1b9a5-102">ICorDebugClass::GetStaticFieldValue Method</span></span>
<span data-ttu-id="1b9a5-103">Obtém o valor do campo estático especificado.</span><span class="sxs-lookup"><span data-stu-id="1b9a5-103">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b9a5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b9a5-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b9a5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1b9a5-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="1b9a5-106">[in] Um campo `Def` token que referencia o campo a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="1b9a5-106">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="1b9a5-107">[in] Um ponteiro para um objeto ICorDebugFrame que representa o quadro a ser usado para resolver a ambiguidade entre threads, contexto ou estáticos de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1b9a5-107">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="1b9a5-108">Se o campo estático é em relação a um thread, um contexto ou um domínio de aplicativo, o quadro determinará o valor adequado.</span><span class="sxs-lookup"><span data-stu-id="1b9a5-108">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="1b9a5-109">[out] Um ponteiro para o endereço de um objeto ICorDebugValue que representa o valor do campo estático.</span><span class="sxs-lookup"><span data-stu-id="1b9a5-109">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b9a5-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b9a5-110">Remarks</span></span>  
 <span data-ttu-id="1b9a5-111">Para tipos parametrizados, o valor de um campo estático é relativo a instanciação específica.</span><span class="sxs-lookup"><span data-stu-id="1b9a5-111">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="1b9a5-112">Portanto, se o construtor de classe aceitar parâmetros de tipo <xref:System.Type>, chame [Icordebugtype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) em vez de `ICorDebugClass::GetStaticFieldValue`.</span><span class="sxs-lookup"><span data-stu-id="1b9a5-112">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b9a5-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1b9a5-113">Requirements</span></span>  
 <span data-ttu-id="1b9a5-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b9a5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b9a5-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b9a5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b9a5-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b9a5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b9a5-117">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b9a5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
