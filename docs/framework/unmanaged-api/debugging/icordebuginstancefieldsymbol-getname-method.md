---
title: Método ICorDebugInstanceFieldSymbol::GetName
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d23bf14fbb3d75534ac2d4a43eca0fbf3e994ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946413"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="af971-102">Método ICorDebugInstanceFieldSymbol::GetName</span><span class="sxs-lookup"><span data-stu-id="af971-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="af971-103">Obtém o nome do campo de instância.</span><span class="sxs-lookup"><span data-stu-id="af971-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af971-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af971-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af971-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="af971-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="af971-106">[in] O número de caracteres no `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="af971-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="af971-107">[out] Um ponteiro para o número de caracteres gravados, na verdade, o `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="af971-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="af971-108">[out] Uma matriz de caracteres que armazena o nome retornado.</span><span class="sxs-lookup"><span data-stu-id="af971-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af971-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="af971-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af971-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="af971-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af971-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="af971-111">Requirements</span></span>  
 <span data-ttu-id="af971-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af971-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af971-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af971-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af971-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af971-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af971-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af971-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af971-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af971-116">See also</span></span>

- [<span data-ttu-id="af971-117">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="af971-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="af971-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="af971-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
