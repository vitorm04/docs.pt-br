---
title: iCorDebugStaticFieldSymbol::Método GetName
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: b1f5ca266f51df730dfb840c7bf003c47f31ece9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178511"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="84dc1-102">iCorDebugStaticFieldSymbol::Método GetName</span><span class="sxs-lookup"><span data-stu-id="84dc1-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="84dc1-103">Obtém o nome do campo estático.</span><span class="sxs-lookup"><span data-stu-id="84dc1-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84dc1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84dc1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84dc1-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="84dc1-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="84dc1-106">[em] O número de `szName` caracteres no buffer.</span><span class="sxs-lookup"><span data-stu-id="84dc1-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="84dc1-107">[fora] Um ponteiro para o número de `szName` caracteres realmente escrito no buffer.</span><span class="sxs-lookup"><span data-stu-id="84dc1-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="84dc1-108">[fora] Uma matriz de caracteres que armazena o nome retornado.</span><span class="sxs-lookup"><span data-stu-id="84dc1-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84dc1-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="84dc1-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84dc1-110">Este método está disponível apenas com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="84dc1-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84dc1-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="84dc1-111">Requirements</span></span>  
 <span data-ttu-id="84dc1-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84dc1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84dc1-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84dc1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84dc1-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84dc1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84dc1-115">**.NET Framework Versions:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84dc1-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84dc1-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="84dc1-116">See also</span></span>

- [<span data-ttu-id="84dc1-117">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="84dc1-117">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="84dc1-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="84dc1-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
