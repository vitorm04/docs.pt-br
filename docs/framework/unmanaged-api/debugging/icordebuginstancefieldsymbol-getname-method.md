---
title: Método ICorDebugInstanceFieldSymbol::GetName
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64357f873c9f125712fce33a1d9995c79a8cc006
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54533449"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="fbb41-102">Método ICorDebugInstanceFieldSymbol::GetName</span><span class="sxs-lookup"><span data-stu-id="fbb41-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="fbb41-103">Obtém o nome do campo de instância.</span><span class="sxs-lookup"><span data-stu-id="fbb41-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbb41-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbb41-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fbb41-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fbb41-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="fbb41-106">[in] O número de caracteres no `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="fbb41-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="fbb41-107">[out] Um ponteiro para o número de caracteres gravados, na verdade, o `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="fbb41-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="fbb41-108">[out] Uma matriz de caracteres que armazena o nome retornado.</span><span class="sxs-lookup"><span data-stu-id="fbb41-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbb41-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="fbb41-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbb41-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fbb41-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbb41-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fbb41-111">Requirements</span></span>  
 <span data-ttu-id="fbb41-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbb41-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbb41-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fbb41-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fbb41-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbb41-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbb41-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbb41-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbb41-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbb41-116">See also</span></span>
- [<span data-ttu-id="fbb41-117">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="fbb41-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="fbb41-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="fbb41-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
