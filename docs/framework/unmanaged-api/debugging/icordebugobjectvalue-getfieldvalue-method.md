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
ms.openlocfilehash: 660bc13e8109994f59444c0adebbc97f54de0b43
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207586"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a><span data-ttu-id="beec8-102">Método ICorDebugObjectValue::GetFieldValue</span><span class="sxs-lookup"><span data-stu-id="beec8-102">ICorDebugObjectValue::GetFieldValue Method</span></span>
<span data-ttu-id="beec8-103">Obtém o valor do campo especificado da classe especificada para esse valor de objeto.</span><span class="sxs-lookup"><span data-stu-id="beec8-103">Gets the value of the specified field of the specified class for this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beec8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="beec8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="beec8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="beec8-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="beec8-106">no Um ponteiro para um objeto "ICorDebugClass" que representa a classe para a qual obter o valor do campo.</span><span class="sxs-lookup"><span data-stu-id="beec8-106">[in] A pointer to an "ICorDebugClass" object that represents the class for which to get the field value.</span></span>  
  
 `fieldDef`  
 <span data-ttu-id="beec8-107">no Um `mdFieldDef` token que faz referência aos metadados que descrevem o campo.</span><span class="sxs-lookup"><span data-stu-id="beec8-107">[in] An `mdFieldDef` token that references the metadata describing the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="beec8-108">fora Um ponteiro para um objeto "ICorDebugValue" que representa o valor do campo especificado.</span><span class="sxs-lookup"><span data-stu-id="beec8-108">[out] A pointer to an "ICorDebugValue" object that represents the value of the specified field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="beec8-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="beec8-109">Remarks</span></span>  
 <span data-ttu-id="beec8-110">A classe, especificada no `pClass` parâmetro, deve estar na hierarquia da classe do valor do objeto e o campo deve ser um campo dessa classe.</span><span class="sxs-lookup"><span data-stu-id="beec8-110">The class, specified in the `pClass` parameter, must be in the hierarchy of the object value's class, and the field must be a field of that class.</span></span>  
  
 <span data-ttu-id="beec8-111">O `GetFieldValue` método ainda terá sucesso para objetos genéricos e classes genéricas.</span><span class="sxs-lookup"><span data-stu-id="beec8-111">The `GetFieldValue` method will still succeed for generic objects and generic classes.</span></span> <span data-ttu-id="beec8-112">Por exemplo, se MyDictionary \< V> herdar da \< cadeia de caracteres do dicionário, V> e o valor do objeto for do tipo MyDictionary \< Int32>, passando o `ICorDebugClass` objeto para o Dictionary \< K, v> receberá com êxito um campo de string de dicionário \< , Int32>.</span><span class="sxs-lookup"><span data-stu-id="beec8-112">For example, if MyDictionary\<V> inherits from Dictionary\<string,V>, and the object value is of type MyDictionary\<int32>, passing the `ICorDebugClass` object for Dictionary\<K,V> will successfully get a field of Dictionary\<string,int32>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="beec8-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="beec8-113">Requirements</span></span>  
 <span data-ttu-id="beec8-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="beec8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="beec8-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="beec8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="beec8-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="beec8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="beec8-117">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="beec8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beec8-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="beec8-118">See also</span></span>
