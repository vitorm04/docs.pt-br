---
title: 'Método ICorDebugVariableSymbol:: GetName'
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23637055e493c008db36b23515001895450d6ab9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967896"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="96bed-102">Método ICorDebugVariableSymbol:: GetName</span><span class="sxs-lookup"><span data-stu-id="96bed-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="96bed-103">Obtém o nome de uma variável.</span><span class="sxs-lookup"><span data-stu-id="96bed-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96bed-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96bed-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96bed-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="96bed-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="96bed-106">no O número de caracteres no `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="96bed-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="96bed-107">fora Um ponteiro para o número de caracteres realmente gravados no `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="96bed-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="96bed-108">Um ponteiro para uma matriz de caracteres que contém o nome da variável.</span><span class="sxs-lookup"><span data-stu-id="96bed-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96bed-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="96bed-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96bed-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="96bed-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96bed-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96bed-111">Requirements</span></span>  
 <span data-ttu-id="96bed-112">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96bed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96bed-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96bed-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96bed-114">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96bed-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96bed-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96bed-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96bed-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96bed-116">See also</span></span>

- [<span data-ttu-id="96bed-117">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="96bed-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="96bed-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="96bed-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
