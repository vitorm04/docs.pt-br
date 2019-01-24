---
title: Método ICorDebugInstanceFieldSymbol::GetSize
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04d866888c15585ff5058f870257b317ac888be7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696974"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="f0594-102">Método ICorDebugInstanceFieldSymbol::GetSize</span><span class="sxs-lookup"><span data-stu-id="f0594-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="f0594-103">Obtém o tamanho em bytes do campo de instância.</span><span class="sxs-lookup"><span data-stu-id="f0594-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0594-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f0594-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0594-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f0594-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="f0594-106">[out] Um ponteiro para o comprimento do campo.</span><span class="sxs-lookup"><span data-stu-id="f0594-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0594-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f0594-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0594-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f0594-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0594-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f0594-109">Requirements</span></span>  
 <span data-ttu-id="f0594-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0594-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0594-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0594-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0594-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0594-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0594-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0594-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0594-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0594-114">See also</span></span>
- [<span data-ttu-id="f0594-115">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="f0594-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="f0594-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f0594-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
