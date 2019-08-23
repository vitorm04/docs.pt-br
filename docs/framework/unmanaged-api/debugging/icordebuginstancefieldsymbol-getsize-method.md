---
title: 'Método ICorDebugInstanceFieldSymbol:: GetSize'
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94ff0ddc266ef9a3f5fabf56f43f1eba2c74e3a8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910182"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="fcb4e-102">Método ICorDebugInstanceFieldSymbol:: GetSize</span><span class="sxs-lookup"><span data-stu-id="fcb4e-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="fcb4e-103">Obtém o tamanho em bytes do campo de instância.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcb4e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fcb4e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcb4e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fcb4e-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="fcb4e-106">fora Um ponteiro para o comprimento do campo.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcb4e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="fcb4e-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fcb4e-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fcb4e-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcb4e-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fcb4e-109">Requirements</span></span>  
 <span data-ttu-id="fcb4e-110">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcb4e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcb4e-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fcb4e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fcb4e-112">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fcb4e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcb4e-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcb4e-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcb4e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fcb4e-114">See also</span></span>

- [<span data-ttu-id="fcb4e-115">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="fcb4e-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="fcb4e-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="fcb4e-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
