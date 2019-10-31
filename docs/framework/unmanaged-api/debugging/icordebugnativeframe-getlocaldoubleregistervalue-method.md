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
ms.openlocfilehash: a45061b6a3105565fdbb36173731b3c3dfe5aa4f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137293"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a><span data-ttu-id="4d10d-102">Método ICorDebugNativeFrame::GetLocalDoubleRegisterValue</span><span class="sxs-lookup"><span data-stu-id="4d10d-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Method</span></span>
<span data-ttu-id="4d10d-103">Obtém o valor de um argumento ou uma variável local que é armazenada nos dois registros especificados para esse quadro nativo.</span><span class="sxs-lookup"><span data-stu-id="4d10d-103">Gets the value of an argument or local variable that is stored in the two specified registers for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d10d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4d10d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d10d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4d10d-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="4d10d-106">no Um valor da enumeração "CorDebugRegister" que especifica o registro que contém a palavra alta do valor.</span><span class="sxs-lookup"><span data-stu-id="4d10d-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordReg`  
 <span data-ttu-id="4d10d-107">no Um valor da enumeração de `CorDebugRegister` que especifica o registro que contém a palavra inferior do valor.</span><span class="sxs-lookup"><span data-stu-id="4d10d-107">[in] A value of the `CorDebugRegister` enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="4d10d-108">no Um inteiro que especifica o tamanho da assinatura de metadados binários que é referenciada pelo parâmetro `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="4d10d-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="4d10d-109">no Um valor `PCCOR_SIGNATURE` que aponta para a assinatura de metadados binários do tipo do valor.</span><span class="sxs-lookup"><span data-stu-id="4d10d-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="4d10d-110">fora Um ponteiro para o endereço de um objeto "ICorDebugValue" que representa o valor recuperado que é armazenado nos registros especificados.</span><span class="sxs-lookup"><span data-stu-id="4d10d-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified registers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d10d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="4d10d-111">Remarks</span></span>  
 <span data-ttu-id="4d10d-112">O método `GetLocalDoubleRegisterValue` pode ser usado em um quadro nativo ou em um quadro compilado JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="4d10d-112">The `GetLocalDoubleRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d10d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4d10d-113">Requirements</span></span>  
 <span data-ttu-id="4d10d-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d10d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d10d-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d10d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d10d-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d10d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d10d-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d10d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d10d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d10d-118">See also</span></span>
