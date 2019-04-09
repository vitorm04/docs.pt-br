---
title: Método ICorDebugInstanceFieldSymbol::GetSize
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cc09de2120399dcfe309757d554e1de72e55f07
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081444"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="65ba8-102">Método ICorDebugInstanceFieldSymbol::GetSize</span><span class="sxs-lookup"><span data-stu-id="65ba8-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="65ba8-103">Obtém o tamanho em bytes do campo de instância.</span><span class="sxs-lookup"><span data-stu-id="65ba8-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65ba8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65ba8-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65ba8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="65ba8-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="65ba8-106">[out] Um ponteiro para o comprimento do campo.</span><span class="sxs-lookup"><span data-stu-id="65ba8-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65ba8-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="65ba8-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65ba8-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="65ba8-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65ba8-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65ba8-109">Requirements</span></span>  
 <span data-ttu-id="65ba8-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65ba8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65ba8-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65ba8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65ba8-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65ba8-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="65ba8-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="65ba8-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="65ba8-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65ba8-114">See also</span></span>

- [<span data-ttu-id="65ba8-115">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="65ba8-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="65ba8-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="65ba8-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
