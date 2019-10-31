---
title: 'Método ICorDebugInstanceFieldSymbol:: GetName'
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
ms.openlocfilehash: d88e18b8d6d497098e340b396972f9ead28dbaf6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139047"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="292dc-102">Método ICorDebugInstanceFieldSymbol:: GetName</span><span class="sxs-lookup"><span data-stu-id="292dc-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="292dc-103">Obtém o nome do campo de instância.</span><span class="sxs-lookup"><span data-stu-id="292dc-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="292dc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="292dc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="292dc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="292dc-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="292dc-106">no O número de caracteres no buffer de `szName`.</span><span class="sxs-lookup"><span data-stu-id="292dc-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="292dc-107">fora Um ponteiro para o número de caracteres realmente gravados no buffer de `szName`.</span><span class="sxs-lookup"><span data-stu-id="292dc-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="292dc-108">fora Uma matriz de caracteres que armazena o nome retornado.</span><span class="sxs-lookup"><span data-stu-id="292dc-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="292dc-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="292dc-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="292dc-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="292dc-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="292dc-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="292dc-111">Requirements</span></span>  
 <span data-ttu-id="292dc-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="292dc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="292dc-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="292dc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="292dc-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="292dc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="292dc-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="292dc-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="292dc-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="292dc-116">See also</span></span>

- [<span data-ttu-id="292dc-117">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="292dc-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="292dc-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="292dc-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
