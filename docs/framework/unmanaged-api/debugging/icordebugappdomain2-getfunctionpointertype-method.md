---
title: Método ICorDebugAppDomain2::GetFunctionPointerType
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetFunctionPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType
helpviewer_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType method [.NET Framework debugging]
- GetFunctionPointerType method [.NET Framework debugging]
ms.assetid: 0aba6096-5b38-435c-a72a-86d35db4daef
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec1a9968dbec10783c6f1383fb523e95ff79561e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683894"
---
# <a name="icordebugappdomain2getfunctionpointertype-method"></a><span data-ttu-id="cf0e7-102">Método ICorDebugAppDomain2::GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="cf0e7-102">ICorDebugAppDomain2::GetFunctionPointerType Method</span></span>
<span data-ttu-id="cf0e7-103">Obtém um ponteiro para uma função que tem uma determinada assinatura.</span><span class="sxs-lookup"><span data-stu-id="cf0e7-103">Gets a pointer to a function that has a given signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf0e7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf0e7-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionPointerType (  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType   *ppTypeArgs[],  
    [out] ICorDebugType                      **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf0e7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cf0e7-105">Parameters</span></span>  
 `nTypeArgs`  
 <span data-ttu-id="cf0e7-106">[in] O número de argumentos de tipo para a função.</span><span class="sxs-lookup"><span data-stu-id="cf0e7-106">[in] The number of type arguments for the function.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="cf0e7-107">[in] Uma matriz de ponteiros, cada um deles aponta para um objeto de ICorDebugType que representa um argumento de tipo da função.</span><span class="sxs-lookup"><span data-stu-id="cf0e7-107">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument of the function.</span></span> <span data-ttu-id="cf0e7-108">O primeiro elemento é o tipo de retorno; cada um dos outros elementos é um tipo de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cf0e7-108">The first element is the return type; each of the other elements is a parameter type.</span></span>  
  
 `ppType`  
 <span data-ttu-id="cf0e7-109">[out] Um ponteiro para o endereço de um `ICorDebugType` objeto que representa o ponteiro para a função.</span><span class="sxs-lookup"><span data-stu-id="cf0e7-109">[out] A pointer to the address of an `ICorDebugType` object that represents the pointer to the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf0e7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cf0e7-110">Requirements</span></span>  
 <span data-ttu-id="cf0e7-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf0e7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf0e7-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf0e7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf0e7-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf0e7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf0e7-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf0e7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
