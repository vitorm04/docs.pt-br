---
title: Método ICorDebugNativeFrame::GetLocalRegisterValue
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterValue
helpviewer_keywords:
- GetLocalRegisterValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalRegisterValue method [.NET Framework debugging]
ms.assetid: 5ccb74f3-f891-430c-b70a-e370624edde2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e6512871bf9a5cb0219a470267d1be4ecd403b3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478356"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a><span data-ttu-id="a8c85-102">Método ICorDebugNativeFrame::GetLocalRegisterValue</span><span class="sxs-lookup"><span data-stu-id="a8c85-102">ICorDebugNativeFrame::GetLocalRegisterValue Method</span></span>
<span data-ttu-id="a8c85-103">Obtém o valor de um argumento ou uma variável local que é armazenado no registrador especificado para este quadro nativo.</span><span class="sxs-lookup"><span data-stu-id="a8c85-103">Gets the value of an argument or local variable that is stored in the specified register for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8c85-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8c85-104">Syntax</span></span>  
  
```  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8c85-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a8c85-105">Parameters</span></span>  
 `reg`  
 <span data-ttu-id="a8c85-106">[in] Um valor de enumeração "CorDebugRegister" que especifica o registro que contém o valor.</span><span class="sxs-lookup"><span data-stu-id="a8c85-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="a8c85-107">[in] Um inteiro que especifica o tamanho da assinatura de metadados binária que é referenciado pelo `pvSigBlob` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a8c85-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="a8c85-108">[in] Um `PCCOR_SIGNATURE` valor que aponta para a assinatura binária metadados de tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="a8c85-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a8c85-109">[out] Um ponteiro para o endereço de um objeto de "ICorDebugValue" que representa o valor recuperado armazenado no registrador especificado.</span><span class="sxs-lookup"><span data-stu-id="a8c85-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8c85-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8c85-110">Remarks</span></span>  
 <span data-ttu-id="a8c85-111">O `GetLocalRegisterValue` método pode ser usado em um quadro nativo ou um just-in-time (JIT)-compilados do quadro.</span><span class="sxs-lookup"><span data-stu-id="a8c85-111">The `GetLocalRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8c85-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a8c85-112">Requirements</span></span>  
 <span data-ttu-id="a8c85-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8c85-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8c85-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a8c85-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8c85-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8c85-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8c85-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8c85-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8c85-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8c85-117">See also</span></span>

