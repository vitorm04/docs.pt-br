---
title: "Método ICorDebugNativeFrame::GetLocalRegisterMemoryValue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.GetLocalRegisterMemoryValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::GetLocalRegisterMemoryValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue method [.NET Framework debugging]
- GetLocalRegisterMemoryValue method [.NET Framework debugging]
ms.assetid: d350f69d-9aff-4f5a-8301-daea22dee2da
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47520e6ab4c8c3bba7383ddd08b7ff23be9dddc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a><span data-ttu-id="59f67-102">Método ICorDebugNativeFrame::GetLocalRegisterMemoryValue</span><span class="sxs-lookup"><span data-stu-id="59f67-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Method</span></span>
<span data-ttu-id="59f67-103">Obtém o valor de um argumento ou uma variável local, dos quais a palavra baixa e alta word são armazenados no local de memória e especificado no registro, respectivamente, para este quadro nativo.</span><span class="sxs-lookup"><span data-stu-id="59f67-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the memory location and specified register, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59f67-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59f67-104">Syntax</span></span>  
  
```  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="59f67-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="59f67-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="59f67-106">[in] Um valor da enumeração "CorDebugRegister" que especifica o registro que contém a palavra alta do valor.</span><span class="sxs-lookup"><span data-stu-id="59f67-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordAddress`  
 <span data-ttu-id="59f67-107">[in] Um `CORDB_ADDRESS` valor que especifica o local de memória que contém a palavra baixa do valor.</span><span class="sxs-lookup"><span data-stu-id="59f67-107">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="59f67-108">[in] Um inteiro que especifica o tamanho da assinatura de metadados binária que é referenciado pelo `pvSigBlob` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="59f67-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="59f67-109">[in] Um `PCCOR_SIGNATURE` valor que aponta para a assinatura de metadados binário do tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="59f67-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="59f67-110">[out] Um ponteiro para o endereço de um objeto de "ICorDebugValue" que representa o valor recuperado é armazenado no local de memória e o registro especificado.</span><span class="sxs-lookup"><span data-stu-id="59f67-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59f67-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="59f67-111">Requirements</span></span>  
 <span data-ttu-id="59f67-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59f67-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59f67-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59f67-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59f67-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59f67-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59f67-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59f67-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59f67-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59f67-116">See Also</span></span>  
 
