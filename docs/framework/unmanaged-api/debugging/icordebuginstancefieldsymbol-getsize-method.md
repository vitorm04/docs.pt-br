---
title: 'Método ICorDebugInstanceFieldSymbol:: GetSize'
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
ms.openlocfilehash: 71828cd8486e2ff09190d23473dbab303b92f933
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139024"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="23e59-102">Método ICorDebugInstanceFieldSymbol:: GetSize</span><span class="sxs-lookup"><span data-stu-id="23e59-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="23e59-103">Obtém o tamanho em bytes do campo de instância.</span><span class="sxs-lookup"><span data-stu-id="23e59-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23e59-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23e59-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23e59-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="23e59-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="23e59-106">fora Um ponteiro para o comprimento do campo.</span><span class="sxs-lookup"><span data-stu-id="23e59-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23e59-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="23e59-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23e59-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="23e59-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23e59-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="23e59-109">Requirements</span></span>  
 <span data-ttu-id="23e59-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23e59-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23e59-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23e59-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23e59-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23e59-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23e59-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23e59-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23e59-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23e59-114">See also</span></span>

- [<span data-ttu-id="23e59-115">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="23e59-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="23e59-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="23e59-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
