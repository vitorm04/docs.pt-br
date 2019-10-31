---
title: Método ICorDebugNativeFrame::GetLocalRegisterMemoryValue
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue method [.NET Framework debugging]
- GetLocalRegisterMemoryValue method [.NET Framework debugging]
ms.assetid: d350f69d-9aff-4f5a-8301-daea22dee2da
topic_type:
- apiref
ms.openlocfilehash: d44d7c23f88f5ea93f608d06b69f69b2c3637b5e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096841"
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a><span data-ttu-id="a5708-102">Método ICorDebugNativeFrame::GetLocalRegisterMemoryValue</span><span class="sxs-lookup"><span data-stu-id="a5708-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Method</span></span>
<span data-ttu-id="a5708-103">Obtém o valor de um argumento ou uma variável local, da qual a palavra inferior e a palavra alta são armazenadas no local da memória e no registro especificado, respectivamente, para esse quadro nativo.</span><span class="sxs-lookup"><span data-stu-id="a5708-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the memory location and specified register, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5708-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a5708-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5708-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a5708-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="a5708-106">no Um valor da enumeração "CorDebugRegister" que especifica o registro que contém a palavra alta do valor.</span><span class="sxs-lookup"><span data-stu-id="a5708-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordAddress`  
 <span data-ttu-id="a5708-107">no Um valor `CORDB_ADDRESS` que especifica o local da memória que contém a palavra inferior do valor.</span><span class="sxs-lookup"><span data-stu-id="a5708-107">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="a5708-108">no Um inteiro que especifica o tamanho da assinatura de metadados binários que é referenciada pelo parâmetro `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="a5708-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="a5708-109">no Um valor `PCCOR_SIGNATURE` que aponta para a assinatura de metadados binários do tipo do valor.</span><span class="sxs-lookup"><span data-stu-id="a5708-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a5708-110">fora Um ponteiro para o endereço de um objeto "ICorDebugValue" que representa o valor recuperado que é armazenado no registro especificado e no local da memória.</span><span class="sxs-lookup"><span data-stu-id="a5708-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5708-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a5708-111">Requirements</span></span>  
 <span data-ttu-id="a5708-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5708-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5708-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5708-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5708-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5708-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5708-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5708-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5708-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5708-116">See also</span></span>
