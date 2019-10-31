---
title: Método ICorDebugNativeFrame::GetLocalMemoryRegisterValue
ms.date: 03/30/2017
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
ms.openlocfilehash: 788ce2d47769caa72518e0357a0affdff5862699
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137281"
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a><span data-ttu-id="25f9a-102">Método ICorDebugNativeFrame::GetLocalMemoryRegisterValue</span><span class="sxs-lookup"><span data-stu-id="25f9a-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue Method</span></span>
<span data-ttu-id="25f9a-103">Obtém o valor de um argumento ou uma variável local, da qual a palavra inferior e a palavra alta são armazenadas no registro especificado e no local da memória, respectivamente, para esse quadro nativo.</span><span class="sxs-lookup"><span data-stu-id="25f9a-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the specified register and memory location, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25f9a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25f9a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25f9a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="25f9a-105">Parameters</span></span>  
 `highWordAddress`  
 <span data-ttu-id="25f9a-106">no Um valor `CORDB_ADDRESS` que especifica o local da memória que contém a palavra alta do valor.</span><span class="sxs-lookup"><span data-stu-id="25f9a-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the high word of the value.</span></span>  
  
 `lowWordRegister`  
 <span data-ttu-id="25f9a-107">no Um valor da enumeração "CorDebugRegister" que especifica o registro que contém a palavra inferior do valor.</span><span class="sxs-lookup"><span data-stu-id="25f9a-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="25f9a-108">no Um inteiro que especifica o tamanho da assinatura de metadados binários que é referenciada pelo parâmetro `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="25f9a-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="25f9a-109">no Um valor `PCCOR_SIGNATURE` que aponta para a assinatura de metadados binários do tipo do valor.</span><span class="sxs-lookup"><span data-stu-id="25f9a-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="25f9a-110">fora Um ponteiro para o endereço de um objeto "ICorDebugValue" que representa o valor recuperado que é armazenado no registro especificado e no local da memória.</span><span class="sxs-lookup"><span data-stu-id="25f9a-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25f9a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="25f9a-111">Requirements</span></span>  
 <span data-ttu-id="25f9a-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25f9a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25f9a-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25f9a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25f9a-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25f9a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25f9a-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25f9a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25f9a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25f9a-116">See also</span></span>
