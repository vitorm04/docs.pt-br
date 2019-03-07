---
title: Método ICorDebugVariableSymbol::GetName
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d01f8c3956298daee9f11c912406079d98964225
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465292"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="4d6cc-102">Método ICorDebugVariableSymbol::GetName</span><span class="sxs-lookup"><span data-stu-id="4d6cc-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="4d6cc-103">Obtém o nome de uma variável.</span><span class="sxs-lookup"><span data-stu-id="4d6cc-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d6cc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4d6cc-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d6cc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4d6cc-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="4d6cc-106">[in] O número de caracteres no `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="4d6cc-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="4d6cc-107">[out] Um ponteiro para o número de caracteres gravados, na verdade, o `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="4d6cc-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="4d6cc-108">Um ponteiro para uma matriz de caracteres que contém o nome da variável.</span><span class="sxs-lookup"><span data-stu-id="4d6cc-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d6cc-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="4d6cc-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d6cc-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4d6cc-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d6cc-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4d6cc-111">Requirements</span></span>  
 <span data-ttu-id="4d6cc-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d6cc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d6cc-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d6cc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d6cc-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d6cc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d6cc-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d6cc-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d6cc-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d6cc-116">See also</span></span>
- [<span data-ttu-id="4d6cc-117">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="4d6cc-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="4d6cc-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4d6cc-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
