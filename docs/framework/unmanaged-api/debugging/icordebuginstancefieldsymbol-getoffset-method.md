---
title: Método ICorDebugInstanceFieldSymbol::GetOffset
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c77ac2eac1022fa591066901f48eaf609b5367af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413557"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="d0ce3-102">Método ICorDebugInstanceFieldSymbol::GetOffset</span><span class="sxs-lookup"><span data-stu-id="d0ce3-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="d0ce3-103">Obtém o deslocamento de bytes deste campo de instância em sua classe pai.</span><span class="sxs-lookup"><span data-stu-id="d0ce3-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0ce3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0ce3-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0ce3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d0ce3-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="d0ce3-106">Um ponteiro para o número de bytes que este campo de instância é deslocado em sua classe pai.</span><span class="sxs-lookup"><span data-stu-id="d0ce3-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0ce3-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0ce3-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0ce3-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d0ce3-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0ce3-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d0ce3-109">Requirements</span></span>  
 <span data-ttu-id="d0ce3-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0ce3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0ce3-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0ce3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0ce3-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0ce3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0ce3-113">**Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0ce3-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0ce3-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0ce3-114">See Also</span></span>  
 [<span data-ttu-id="d0ce3-115">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="d0ce3-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="d0ce3-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d0ce3-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
