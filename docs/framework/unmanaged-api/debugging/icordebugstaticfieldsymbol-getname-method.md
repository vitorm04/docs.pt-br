---
title: 'Método ICorDebugStaticFieldSymbol:: GetName'
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: e961ae064bd5bb2c97175b4506ddd8c0f17d3b32
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131787"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="76363-102">Método ICorDebugStaticFieldSymbol:: GetName</span><span class="sxs-lookup"><span data-stu-id="76363-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="76363-103">Obtém o nome do campo estático.</span><span class="sxs-lookup"><span data-stu-id="76363-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76363-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76363-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76363-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="76363-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="76363-106">no O número de caracteres no buffer de `szName`.</span><span class="sxs-lookup"><span data-stu-id="76363-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="76363-107">fora Um ponteiro para o número de caracteres realmente gravados no buffer de `szName`.</span><span class="sxs-lookup"><span data-stu-id="76363-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="76363-108">fora Uma matriz de caracteres que armazena o nome retornado.</span><span class="sxs-lookup"><span data-stu-id="76363-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76363-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="76363-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76363-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="76363-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76363-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="76363-111">Requirements</span></span>  
 <span data-ttu-id="76363-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76363-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76363-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76363-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76363-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76363-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76363-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76363-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76363-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76363-116">See also</span></span>

- [<span data-ttu-id="76363-117">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="76363-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="76363-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="76363-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
