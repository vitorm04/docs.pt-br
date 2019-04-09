---
title: Método ICorDebugInstanceFieldSymbol::GetOffset
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8ea777755aebb59f3e865df26c38c74ef68ae31
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203867"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="a89f3-102">Método ICorDebugInstanceFieldSymbol::GetOffset</span><span class="sxs-lookup"><span data-stu-id="a89f3-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="a89f3-103">Obtém o deslocamento em bytes desse campo de instância em sua classe pai.</span><span class="sxs-lookup"><span data-stu-id="a89f3-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a89f3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a89f3-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a89f3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a89f3-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="a89f3-106">Um ponteiro para o número de bytes que este campo de instância é deslocado em sua classe pai.</span><span class="sxs-lookup"><span data-stu-id="a89f3-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a89f3-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a89f3-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a89f3-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a89f3-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a89f3-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a89f3-109">Requirements</span></span>  
 <span data-ttu-id="a89f3-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a89f3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a89f3-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a89f3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a89f3-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a89f3-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a89f3-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="a89f3-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a89f3-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a89f3-114">See also</span></span>

- [<span data-ttu-id="a89f3-115">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="a89f3-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="a89f3-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a89f3-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
