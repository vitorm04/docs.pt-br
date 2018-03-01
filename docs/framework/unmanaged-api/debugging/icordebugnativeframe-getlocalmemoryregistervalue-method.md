---
title: "Método ICorDebugNativeFrame::GetLocalMemoryRegisterValue"
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
- ICorDebugNativeFrame.GetLocalMemoryRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue method [.NET Framework debugging]
- GetLocalMemoryRegisterValue method
ms.assetid: 33a19f6e-1029-4d53-af64-19591c6e58ee
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 19b3a184272af06e465257d317ab32f5a9c3686a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a><span data-ttu-id="a23f6-102">Método ICorDebugNativeFrame::GetLocalMemoryRegisterValue</span><span class="sxs-lookup"><span data-stu-id="a23f6-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue Method</span></span>
<span data-ttu-id="a23f6-103">Obtém o valor de um argumento ou uma variável local, dos quais a palavra baixa e alta word são armazenadas no registro especificado e o local de memória, respectivamente, para este quadro nativo.</span><span class="sxs-lookup"><span data-stu-id="a23f6-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the specified register and memory location, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a23f6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a23f6-104">Syntax</span></span>  
  
```  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a23f6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a23f6-105">Parameters</span></span>  
 `highWordAddress`  
 <span data-ttu-id="a23f6-106">[in] Um `CORDB_ADDRESS` valor que especifica o local de memória que contém a palavra alta do valor.</span><span class="sxs-lookup"><span data-stu-id="a23f6-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the high word of the value.</span></span>  
  
 `lowWordRegister`  
 <span data-ttu-id="a23f6-107">[in] Um valor da enumeração "CorDebugRegister" que especifica o registro que contém a palavra baixa do valor.</span><span class="sxs-lookup"><span data-stu-id="a23f6-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="a23f6-108">[in] Um inteiro que especifica o tamanho da assinatura de metadados binária que é referenciado pelo `pvSigBlob` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a23f6-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="a23f6-109">[in] Um `PCCOR_SIGNATURE` valor que aponta para a assinatura de metadados binário do tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="a23f6-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a23f6-110">[out] Um ponteiro para o endereço de um objeto de "ICorDebugValue" que representa o valor recuperado é armazenado no local de memória e o registro especificado.</span><span class="sxs-lookup"><span data-stu-id="a23f6-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a23f6-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a23f6-111">Requirements</span></span>  
 <span data-ttu-id="a23f6-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a23f6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a23f6-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a23f6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a23f6-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a23f6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a23f6-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a23f6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a23f6-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a23f6-116">See Also</span></span>  
 
