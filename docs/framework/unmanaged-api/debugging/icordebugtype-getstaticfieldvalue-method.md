---
title: "Método ICorDebugType::GetStaticFieldValue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetStaticFieldValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a6a7305017c83b539a3d5ec11fa61ccd2af90a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a><span data-ttu-id="65004-102">Método ICorDebugType::GetStaticFieldValue</span><span class="sxs-lookup"><span data-stu-id="65004-102">ICorDebugType::GetStaticFieldValue Method</span></span>
<span data-ttu-id="65004-103">Obtém um ponteiro de interface para um objeto ICorDebugValue que contém o valor do campo estático referenciado pelo campo especificado token no quadro de pilha especificada.</span><span class="sxs-lookup"><span data-stu-id="65004-103">Gets an interface pointer to an ICorDebugValue object that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65004-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65004-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65004-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="65004-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="65004-106">[in] Um `mdFieldDef` token que especifica o campo estático.</span><span class="sxs-lookup"><span data-stu-id="65004-106">[in] An `mdFieldDef` token that specifies the static field.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="65004-107">[in] Um ponteiro para um ICorDebugFrame que representa o quadro de pilhas.</span><span class="sxs-lookup"><span data-stu-id="65004-107">[in] A pointer to an ICorDebugFrame that represents the stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="65004-108">[out] Um ponteiro para o endereço de um `ICorDebugValue` que contém o valor do campo estático.</span><span class="sxs-lookup"><span data-stu-id="65004-108">[out] A pointer to the address of an `ICorDebugValue` that contains the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65004-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="65004-109">Remarks</span></span>  
 <span data-ttu-id="65004-110">O `GetStaticFieldValue` método pode ser usado somente se o tipo é ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, conforme indicado pelo [Icordebugtype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="65004-110">The `GetStaticFieldValue` method may be used only if the type is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
 <span data-ttu-id="65004-111">Para tipos não genérica, a operação é executada por `GetStaticFieldValue` é idêntico ao chamar [: GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) no que é retornado pelo objeto ICorDebugClass [: Getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).</span><span class="sxs-lookup"><span data-stu-id="65004-111">For non-generic types, the operation performed by `GetStaticFieldValue` is identical to calling [ICorDebugClass::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) on the ICorDebugClass object that is returned by [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).</span></span>  
  
 <span data-ttu-id="65004-112">Para tipos genéricos, um valor de campo estático será em relação a uma instanciação específica.</span><span class="sxs-lookup"><span data-stu-id="65004-112">For generic types, a static field value will be relative to a particular instantiation.</span></span> <span data-ttu-id="65004-113">Além disso, pode ser um campo estático em relação a um thread, um contexto ou um domínio de aplicativo, em seguida, o quadro de pilhas ajuda o depurador determinar o valor correto.</span><span class="sxs-lookup"><span data-stu-id="65004-113">Also, if the static field could possibly be relative to a thread, a context, or an application domain, then the stack frame will help the debugger determine the proper value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65004-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="65004-114">Remarks</span></span>  
 <span data-ttu-id="65004-115">`GetStaticFieldValue`pode ser utilizada somente quando uma chamada para `ICorDebugType::GetType` retorna um valor de ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE.</span><span class="sxs-lookup"><span data-stu-id="65004-115">`GetStaticFieldValue` can be used only when a call to `ICorDebugType::GetType` returns a value of ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65004-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65004-116">Requirements</span></span>  
 <span data-ttu-id="65004-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65004-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65004-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65004-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65004-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65004-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65004-120">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65004-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
