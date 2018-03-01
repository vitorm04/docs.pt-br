---
title: "Método ICorDebugAppDomain2::GetArrayOrPointerType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAppDomain2.GetArrayOrPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6beb75638ccbf81149fd7fa1682acca3e7673dc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a><span data-ttu-id="d2bfc-102">Método ICorDebugAppDomain2::GetArrayOrPointerType</span><span class="sxs-lookup"><span data-stu-id="d2bfc-102">ICorDebugAppDomain2::GetArrayOrPointerType Method</span></span>
<span data-ttu-id="d2bfc-103">Obtém uma matriz do tipo especificado, ou um ponteiro ou referência ao tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="d2bfc-103">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2bfc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2bfc-104">Syntax</span></span>  
  
```  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2bfc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d2bfc-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="d2bfc-106">[in] Um valor da enumeração CorElementType que especifica o tipo nativo subjacente (uma matriz, ponteiro ou referência) a ser criado.</span><span class="sxs-lookup"><span data-stu-id="d2bfc-106">[in] A value of the CorElementType enumeration that specifies the underlying native type (an array, pointer, or reference) to be created.</span></span>  
  
 `nRank`  
 <span data-ttu-id="d2bfc-107">[in] A classificação (ou seja, o número de dimensões) da matriz.</span><span class="sxs-lookup"><span data-stu-id="d2bfc-107">[in] The rank (that is, number of dimensions) of the array.</span></span> <span data-ttu-id="d2bfc-108">Esse valor deve ser 0 se `elementType` Especifica um tipo de ponteiro ou referência.</span><span class="sxs-lookup"><span data-stu-id="d2bfc-108">This value must be 0 if `elementType` specifies a pointer or reference type.</span></span>  
  
 `pTypeArg`  
 <span data-ttu-id="d2bfc-109">[in] Um ponteiro para um objeto ICorDebugType que representa o tipo de matriz, um ponteiro ou uma referência a ser criado.</span><span class="sxs-lookup"><span data-stu-id="d2bfc-109">[in] A pointer to an ICorDebugType object that represents the type of array, pointer, or reference to be created.</span></span>  
  
 `ppType`  
 <span data-ttu-id="d2bfc-110">[out] Um ponteiro para o endereço de um `ICorDebugType` tipo de objeto que representa a matriz construído, tipo de ponteiro ou referência.</span><span class="sxs-lookup"><span data-stu-id="d2bfc-110">[out] A pointer to the address of an `ICorDebugType` object that represents the constructed array, pointer type, or reference type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2bfc-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d2bfc-111">Remarks</span></span>  
 <span data-ttu-id="d2bfc-112">O valor de *elementType* deve ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="d2bfc-112">The value of *elementType* must be one of the following:</span></span>  
  
-   <span data-ttu-id="d2bfc-113">ELEMENT_TYPE_PTR</span><span class="sxs-lookup"><span data-stu-id="d2bfc-113">ELEMENT_TYPE_PTR</span></span>  
  
-   <span data-ttu-id="d2bfc-114">ELEMENT_TYPE_BYREF</span><span class="sxs-lookup"><span data-stu-id="d2bfc-114">ELEMENT_TYPE_BYREF</span></span>  
  
-   <span data-ttu-id="d2bfc-115">ELEMENT_TYPE_ARRAY ou ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="d2bfc-115">ELEMENT_TYPE_ARRAY or ELEMENT_TYPE_SZARRAY</span></span>  
  
 <span data-ttu-id="d2bfc-116">Se o valor de *elementType* é ELEMENT_TYPE_PTR ou ELEMENT_TYPE_BYREF, *nRank* devem ser zero.</span><span class="sxs-lookup"><span data-stu-id="d2bfc-116">If the value of *elementType* is ELEMENT_TYPE_PTR or ELEMENT_TYPE_BYREF, *nRank* must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2bfc-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d2bfc-117">Requirements</span></span>  
 <span data-ttu-id="d2bfc-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2bfc-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2bfc-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2bfc-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2bfc-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2bfc-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2bfc-121">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2bfc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
