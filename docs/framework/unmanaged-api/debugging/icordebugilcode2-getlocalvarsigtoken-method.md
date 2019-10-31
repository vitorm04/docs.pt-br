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
ms.openlocfilehash: 243000a2399b4938a3ad7f732c64e2f79b664f51
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131055"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a><span data-ttu-id="2e793-102">ICorDebugILCode2::Método GetLocalVarSigToken</span><span class="sxs-lookup"><span data-stu-id="2e793-102">ICorDebugILCode2::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="2e793-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="2e793-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="2e793-104">Obtém o token de metadados para a assinatura de variável local para a função que é representada por esta instância.</span><span class="sxs-lookup"><span data-stu-id="2e793-104">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e793-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e793-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e793-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2e793-106">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="2e793-107">[out] Um ponteiro para o token `mdSignature` para a assinatura de variável local desta função ou `mdSignatureNil` se não houver uma assinatura (isto é, se a função não tiver variáveis locais).</span><span class="sxs-lookup"><span data-stu-id="2e793-107">[out] A pointer to the `mdSignature` token for the local variable signature for this function, or `mdSignatureNil` if there is no signature (that is, if the function doesn't have any local variables).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e793-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="2e793-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e793-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2e793-109">Requirements</span></span>  
 <span data-ttu-id="2e793-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e793-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e793-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e793-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e793-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e793-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e793-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e793-113">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e793-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e793-114">See also</span></span>

- [<span data-ttu-id="2e793-115">Interface ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="2e793-115">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [<span data-ttu-id="2e793-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2e793-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
