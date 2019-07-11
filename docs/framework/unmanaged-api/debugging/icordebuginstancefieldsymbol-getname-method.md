---
title: Método ICorDebugInstanceFieldSymbol::GetName
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 338f68a6ffc1c23508f12b344008fecce01bbf7d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760260"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="ee1f0-102">Método ICorDebugInstanceFieldSymbol::GetName</span><span class="sxs-lookup"><span data-stu-id="ee1f0-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="ee1f0-103">Obtém o nome do campo de instância.</span><span class="sxs-lookup"><span data-stu-id="ee1f0-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee1f0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ee1f0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee1f0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ee1f0-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ee1f0-106">[in] O número de caracteres no `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="ee1f0-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ee1f0-107">[out] Um ponteiro para o número de caracteres gravados, na verdade, o `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="ee1f0-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="ee1f0-108">[out] Uma matriz de caracteres que armazena o nome retornado.</span><span class="sxs-lookup"><span data-stu-id="ee1f0-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee1f0-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ee1f0-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee1f0-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ee1f0-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee1f0-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ee1f0-111">Requirements</span></span>  
 <span data-ttu-id="ee1f0-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee1f0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee1f0-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee1f0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee1f0-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee1f0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee1f0-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee1f0-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee1f0-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee1f0-116">See also</span></span>

- [<span data-ttu-id="ee1f0-117">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="ee1f0-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="ee1f0-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ee1f0-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
