---
title: "Método ICorDebugNativeFrame::GetLocalDoubleRegisterValue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.GetLocalDoubleRegisterValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::GetLocalDoubleRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue method [.NET Framework debugging]
- GetLocalDoubleRegisterValue method [.NET Framework debugging]
ms.assetid: 1f838215-ac8a-434f-8ce6-03021d3098d9
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ece07fcffbc0d0e6b8cf06cc04866c1b651e6a01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a><span data-ttu-id="68196-102">Método ICorDebugNativeFrame::GetLocalDoubleRegisterValue</span><span class="sxs-lookup"><span data-stu-id="68196-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Method</span></span>
<span data-ttu-id="68196-103">Obtém o valor de um argumento ou uma variável local que é armazenado em dois registros especificados para este quadro nativo.</span><span class="sxs-lookup"><span data-stu-id="68196-103">Gets the value of an argument or local variable that is stored in the two specified registers for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68196-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="68196-104">Syntax</span></span>  
  
```  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68196-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="68196-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="68196-106">[in] Um valor da enumeração "CorDebugRegister" que especifica o registro que contém a palavra alta do valor.</span><span class="sxs-lookup"><span data-stu-id="68196-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordReg`  
 <span data-ttu-id="68196-107">[in] Um valor de `CorDebugRegister` enumeração que especifica o registro que contém a palavra baixa do valor.</span><span class="sxs-lookup"><span data-stu-id="68196-107">[in] A value of the `CorDebugRegister` enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="68196-108">[in] Um inteiro que especifica o tamanho da assinatura de metadados binária que é referenciado pelo `pvSigBlob` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="68196-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="68196-109">[in] Um `PCCOR_SIGNATURE` valor que aponta para a assinatura de metadados binário do tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="68196-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="68196-110">[out] Um ponteiro para o endereço de um objeto de "ICorDebugValue" que representa o valor recuperado é armazenado nos registradores especificados.</span><span class="sxs-lookup"><span data-stu-id="68196-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified registers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68196-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="68196-111">Remarks</span></span>  
 <span data-ttu-id="68196-112">O `GetLocalDoubleRegisterValue` método pode ser usado em um quadro nativo ou um just-in-time (JIT)-compilado quadro.</span><span class="sxs-lookup"><span data-stu-id="68196-112">The `GetLocalDoubleRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68196-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="68196-113">Requirements</span></span>  
 <span data-ttu-id="68196-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68196-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68196-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68196-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68196-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68196-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68196-117">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68196-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68196-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68196-118">See Also</span></span>  
 
