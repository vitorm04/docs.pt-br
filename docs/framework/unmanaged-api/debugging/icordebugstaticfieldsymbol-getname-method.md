---
title: Método ICorDebugStaticFieldSymbol::GetName
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5f52999c3f680fbccefe4681f83d473cdb86306
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782610"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="b1553-102">Método ICorDebugStaticFieldSymbol::GetName</span><span class="sxs-lookup"><span data-stu-id="b1553-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="b1553-103">Obtém o nome do campo estático.</span><span class="sxs-lookup"><span data-stu-id="b1553-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1553-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1553-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1553-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b1553-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="b1553-106">[in] O número de caracteres no `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="b1553-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b1553-107">[out] Um ponteiro para o número de caracteres gravados, na verdade, o `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="b1553-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="b1553-108">[out] Uma matriz de caracteres que armazena o nome retornado.</span><span class="sxs-lookup"><span data-stu-id="b1553-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1553-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1553-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1553-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b1553-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1553-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1553-111">Requirements</span></span>  
 <span data-ttu-id="b1553-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1553-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1553-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1553-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1553-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1553-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1553-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1553-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1553-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1553-116">See also</span></span>

- [<span data-ttu-id="b1553-117">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="b1553-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="b1553-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b1553-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
