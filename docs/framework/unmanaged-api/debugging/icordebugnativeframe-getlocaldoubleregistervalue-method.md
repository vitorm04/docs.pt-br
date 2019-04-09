---
title: Método ICorDebugNativeFrame::GetLocalDoubleRegisterValue
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalDoubleRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue method [.NET Framework debugging]
- GetLocalDoubleRegisterValue method [.NET Framework debugging]
ms.assetid: 1f838215-ac8a-434f-8ce6-03021d3098d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13e1e3369c4e7a185c2167facc8514b5cfc85a85
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115863"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a><span data-ttu-id="efe38-102">Método ICorDebugNativeFrame::GetLocalDoubleRegisterValue</span><span class="sxs-lookup"><span data-stu-id="efe38-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Method</span></span>
<span data-ttu-id="efe38-103">Obtém o valor de um argumento ou uma variável local que é armazenado nos dois registradores especificados para este quadro nativo.</span><span class="sxs-lookup"><span data-stu-id="efe38-103">Gets the value of an argument or local variable that is stored in the two specified registers for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efe38-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="efe38-104">Syntax</span></span>  
  
```  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efe38-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="efe38-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="efe38-106">[in] Um valor de enumeração "CorDebugRegister" que especifica o registro que contém a palavra alta do valor.</span><span class="sxs-lookup"><span data-stu-id="efe38-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordReg`  
 <span data-ttu-id="efe38-107">[in] Um valor da `CorDebugRegister` enumeração que especifica o registro que contém a palavra inferior do valor.</span><span class="sxs-lookup"><span data-stu-id="efe38-107">[in] A value of the `CorDebugRegister` enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="efe38-108">[in] Um inteiro que especifica o tamanho da assinatura de metadados binária que é referenciado pelo `pvSigBlob` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="efe38-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="efe38-109">[in] Um `PCCOR_SIGNATURE` valor que aponta para a assinatura binária metadados de tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="efe38-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="efe38-110">[out] Um ponteiro para o endereço de um objeto de "ICorDebugValue" que representa o valor recuperado armazenado nos registradores especificados.</span><span class="sxs-lookup"><span data-stu-id="efe38-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified registers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efe38-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="efe38-111">Remarks</span></span>  
 <span data-ttu-id="efe38-112">O `GetLocalDoubleRegisterValue` método pode ser usado em um quadro nativo ou um just-in-time (JIT)-compilados do quadro.</span><span class="sxs-lookup"><span data-stu-id="efe38-112">The `GetLocalDoubleRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efe38-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="efe38-113">Requirements</span></span>  
 <span data-ttu-id="efe38-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efe38-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efe38-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="efe38-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="efe38-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efe38-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="efe38-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="efe38-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="efe38-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="efe38-118">See also</span></span>
