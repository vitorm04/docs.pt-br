---
title: Método ICorDebugNativeFrame::GetLocalMemoryValue
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryValue
helpviewer_keywords:
- GetLocalMemoryValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalMemoryValue method [.NET Framework debugging]
ms.assetid: b600b3a2-9908-42d8-8093-ab6f39e9a2c9
topic_type:
- apiref
ms.openlocfilehash: 4c4bfe6a797fc1476ff53a8f2db4f80debc41f6b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212432"
---
# <a name="icordebugnativeframegetlocalmemoryvalue-method"></a><span data-ttu-id="7723a-102">Método ICorDebugNativeFrame::GetLocalMemoryValue</span><span class="sxs-lookup"><span data-stu-id="7723a-102">ICorDebugNativeFrame::GetLocalMemoryValue Method</span></span>
<span data-ttu-id="7723a-103">Obtém o valor de um argumento ou uma variável local que é armazenada no local de memória especificado para esse quadro nativo.</span><span class="sxs-lookup"><span data-stu-id="7723a-103">Gets the value of an argument or local variable that is stored in the specified memory location for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7723a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7723a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalMemoryValue (  
    [in]  CORDB_ADDRESS      address,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7723a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7723a-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="7723a-106">no Um `CORDB_ADDRESS` valor que especifica o local da memória que contém o valor.</span><span class="sxs-lookup"><span data-stu-id="7723a-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="7723a-107">no Um inteiro que especifica o tamanho da assinatura de metadados binários que é referenciada pelo `pvSigBlob` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7723a-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="7723a-108">no Um `PCCOR_SIGNATURE` valor que aponta para a assinatura de metadados binários do tipo do valor.</span><span class="sxs-lookup"><span data-stu-id="7723a-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="7723a-109">fora Um ponteiro para o endereço de um objeto "ICorDebugValue" que representa o valor recuperado que é armazenado no local da memória especificado.</span><span class="sxs-lookup"><span data-stu-id="7723a-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7723a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7723a-110">Requirements</span></span>  
 <span data-ttu-id="7723a-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7723a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7723a-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7723a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7723a-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7723a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7723a-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7723a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7723a-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="7723a-115">See also</span></span>
