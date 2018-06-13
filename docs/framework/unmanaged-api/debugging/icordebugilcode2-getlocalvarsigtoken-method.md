---
title: ICorDebugILCode2::Método GetLocalVarSigToken
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 17665b77-1342-4115-94fd-9f45b0ecfb0f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e02f44e4f581170a842a1c103ed069cb90cde79c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412292"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a><span data-ttu-id="f222f-102">ICorDebugILCode2::Método GetLocalVarSigToken</span><span class="sxs-lookup"><span data-stu-id="f222f-102">ICorDebugILCode2::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="f222f-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="f222f-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f222f-104">Obtém o token de metadados para a assinatura de variável local para a função que é representada por esta instância.</span><span class="sxs-lookup"><span data-stu-id="f222f-104">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f222f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f222f-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f222f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f222f-106">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="f222f-107">[out] Um ponteiro para o token `mdSignature` para a assinatura de variável local desta função ou `mdSignatureNil` se não houver uma assinatura (isto é, se a função não tiver variáveis locais).</span><span class="sxs-lookup"><span data-stu-id="f222f-107">[out] A pointer to the `mdSignature` token for the local variable signature for this function, or `mdSignatureNil` if there is no signature (that is, if the function doesn't have any local variables).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f222f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="f222f-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f222f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f222f-109">Requirements</span></span>  
 <span data-ttu-id="f222f-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f222f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f222f-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f222f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f222f-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f222f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f222f-113">**Versões do .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f222f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f222f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f222f-114">See Also</span></span>  
 [<span data-ttu-id="f222f-115">Interface ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="f222f-115">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 [<span data-ttu-id="f222f-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f222f-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
