---
title: Método ICorDebugObjectValue::GetFieldValue
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8778edf9ac6e32d5dab3a53a6d9cc643a8df13b1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107907"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a><span data-ttu-id="73f00-102">Método ICorDebugObjectValue::GetFieldValue</span><span class="sxs-lookup"><span data-stu-id="73f00-102">ICorDebugObjectValue::GetFieldValue Method</span></span>
<span data-ttu-id="73f00-103">Obtém o valor do campo especificado da classe especificada para o valor desse objeto.</span><span class="sxs-lookup"><span data-stu-id="73f00-103">Gets the value of the specified field of the specified class for this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73f00-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73f00-104">Syntax</span></span>  
  
```  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73f00-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="73f00-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="73f00-106">[in] Um ponteiro para um objeto de "ICorDebugClass" que representa a classe para o qual obter o valor do campo.</span><span class="sxs-lookup"><span data-stu-id="73f00-106">[in] A pointer to an "ICorDebugClass" object that represents the class for which to get the field value.</span></span>  
  
 `fieldDef`  
 <span data-ttu-id="73f00-107">[in] Um `mdFieldDef` token que referencia os metadados que descrevem o campo.</span><span class="sxs-lookup"><span data-stu-id="73f00-107">[in] An `mdFieldDef` token that references the metadata describing the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="73f00-108">[out] Um ponteiro para um objeto de "ICorDebugValue" que representa o valor do campo especificado.</span><span class="sxs-lookup"><span data-stu-id="73f00-108">[out] A pointer to an "ICorDebugValue" object that represents the value of the specified field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73f00-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="73f00-109">Remarks</span></span>  
 <span data-ttu-id="73f00-110">A classe especificada no `pClass` parâmetro, deve estar na hierarquia de classe do valor do objeto e o campo deve ser um campo de classe.</span><span class="sxs-lookup"><span data-stu-id="73f00-110">The class, specified in the `pClass` parameter, must be in the hierarchy of the object value's class, and the field must be a field of that class.</span></span>  
  
 <span data-ttu-id="73f00-111">O `GetFieldValue` método ainda será bem-sucedida para objetos genéricos e as classes genéricas.</span><span class="sxs-lookup"><span data-stu-id="73f00-111">The `GetFieldValue` method will still succeed for generic objects and generic classes.</span></span> <span data-ttu-id="73f00-112">Por exemplo, se MyDictionary\<V > herda de dicionário\<de cadeia de caracteres, V >, e o valor do objeto é do tipo MyDictionary\<int32 >, passando o `ICorDebugClass` objeto de dicionário\<K, V > será obter com êxito um campo de dicionário\<string, int32 >.</span><span class="sxs-lookup"><span data-stu-id="73f00-112">For example, if MyDictionary\<V> inherits from Dictionary\<string,V>, and the object value is of type MyDictionary\<int32>, passing the `ICorDebugClass` object for Dictionary\<K,V> will successfully get a field of Dictionary\<string,int32>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73f00-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="73f00-113">Requirements</span></span>  
 <span data-ttu-id="73f00-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73f00-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73f00-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73f00-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73f00-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73f00-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="73f00-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="73f00-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="73f00-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73f00-118">See also</span></span>
