---
title: 'Método ICorDebugInstanceFieldSymbol:: GetOffset'
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 453f691f414050905f5d73e201ebeed79e2aaf50
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910200"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="84eed-102">Método ICorDebugInstanceFieldSymbol:: GetOffset</span><span class="sxs-lookup"><span data-stu-id="84eed-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="84eed-103">Obtém o deslocamento em bytes deste campo de instância em sua classe pai.</span><span class="sxs-lookup"><span data-stu-id="84eed-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84eed-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84eed-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84eed-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="84eed-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="84eed-106">Um ponteiro para o número de bytes que esse campo de instância é deslocado em sua classe pai.</span><span class="sxs-lookup"><span data-stu-id="84eed-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84eed-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="84eed-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84eed-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="84eed-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84eed-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="84eed-109">Requirements</span></span>  
 <span data-ttu-id="84eed-110">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84eed-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84eed-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84eed-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84eed-112">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84eed-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84eed-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84eed-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84eed-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84eed-114">See also</span></span>

- [<span data-ttu-id="84eed-115">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="84eed-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="84eed-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="84eed-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
