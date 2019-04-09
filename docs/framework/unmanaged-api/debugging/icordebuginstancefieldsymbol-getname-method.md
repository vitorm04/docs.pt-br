---
title: Método ICorDebugInstanceFieldSymbol::GetName
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d23bf14fbb3d75534ac2d4a43eca0fbf3e994ae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161389"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="033b3-102">Método ICorDebugInstanceFieldSymbol::GetName</span><span class="sxs-lookup"><span data-stu-id="033b3-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="033b3-103">Obtém o nome do campo de instância.</span><span class="sxs-lookup"><span data-stu-id="033b3-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="033b3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="033b3-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="033b3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="033b3-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="033b3-106">[in] O número de caracteres no `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="033b3-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="033b3-107">[out] Um ponteiro para o número de caracteres gravados, na verdade, o `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="033b3-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="033b3-108">[out] Uma matriz de caracteres que armazena o nome retornado.</span><span class="sxs-lookup"><span data-stu-id="033b3-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="033b3-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="033b3-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="033b3-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="033b3-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="033b3-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="033b3-111">Requirements</span></span>  
 <span data-ttu-id="033b3-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="033b3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="033b3-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="033b3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="033b3-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="033b3-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="033b3-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="033b3-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="033b3-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="033b3-116">See also</span></span>

- [<span data-ttu-id="033b3-117">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="033b3-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="033b3-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="033b3-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
