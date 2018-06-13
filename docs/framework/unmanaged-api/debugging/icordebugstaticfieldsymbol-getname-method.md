---
title: Método ICorDebugStaticFieldSymbol::GetName
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 095c84a5cb448803bbfa45e0fad8a494343ca7f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422312"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="fcc19-102">Método ICorDebugStaticFieldSymbol::GetName</span><span class="sxs-lookup"><span data-stu-id="fcc19-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="fcc19-103">Obtém o nome do campo estático.</span><span class="sxs-lookup"><span data-stu-id="fcc19-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcc19-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fcc19-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fcc19-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fcc19-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="fcc19-106">[in] O número de caracteres a `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="fcc19-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="fcc19-107">[out] Um ponteiro para o número de caracteres gravados o `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="fcc19-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="fcc19-108">[out] Uma matriz de caracteres que armazena o nome retornado.</span><span class="sxs-lookup"><span data-stu-id="fcc19-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcc19-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="fcc19-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fcc19-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fcc19-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcc19-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fcc19-111">Requirements</span></span>  
 <span data-ttu-id="fcc19-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcc19-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcc19-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fcc19-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fcc19-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fcc19-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcc19-115">**Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcc19-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcc19-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fcc19-116">See Also</span></span>  
 [<span data-ttu-id="fcc19-117">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="fcc19-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="fcc19-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="fcc19-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
