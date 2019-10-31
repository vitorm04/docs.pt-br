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
ms.openlocfilehash: 132e0868426670ba61d8ee12ba7007be1a8a52de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139402"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a><span data-ttu-id="ffa53-102">Método ICorDebugNativeFrame::GetLocalRegisterValue</span><span class="sxs-lookup"><span data-stu-id="ffa53-102">ICorDebugNativeFrame::GetLocalRegisterValue Method</span></span>
<span data-ttu-id="ffa53-103">Obtém o valor de um argumento ou uma variável local que é armazenada no registro especificado para esse quadro nativo.</span><span class="sxs-lookup"><span data-stu-id="ffa53-103">Gets the value of an argument or local variable that is stored in the specified register for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffa53-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ffa53-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffa53-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ffa53-105">Parameters</span></span>  
 `reg`  
 <span data-ttu-id="ffa53-106">no Um valor da enumeração "CorDebugRegister" que especifica o registro que contém o valor.</span><span class="sxs-lookup"><span data-stu-id="ffa53-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="ffa53-107">no Um inteiro que especifica o tamanho da assinatura de metadados binários que é referenciada pelo parâmetro `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="ffa53-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="ffa53-108">no Um valor `PCCOR_SIGNATURE` que aponta para a assinatura de metadados binários do tipo do valor.</span><span class="sxs-lookup"><span data-stu-id="ffa53-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="ffa53-109">fora Um ponteiro para o endereço de um objeto "ICorDebugValue" que representa o valor recuperado que é armazenado no registro especificado.</span><span class="sxs-lookup"><span data-stu-id="ffa53-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffa53-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="ffa53-110">Remarks</span></span>  
 <span data-ttu-id="ffa53-111">O método `GetLocalRegisterValue` pode ser usado em um quadro nativo ou em um quadro compilado JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="ffa53-111">The `GetLocalRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffa53-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ffa53-112">Requirements</span></span>  
 <span data-ttu-id="ffa53-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffa53-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffa53-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ffa53-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ffa53-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ffa53-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffa53-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffa53-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffa53-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ffa53-117">See also</span></span>
