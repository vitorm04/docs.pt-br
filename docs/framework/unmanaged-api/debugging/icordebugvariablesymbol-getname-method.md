---
title: 'Método ICorDebugVariableSymbol:: GetName'
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: 9bc32d3372710b4c4e92aa89df5e6e7839ad3078
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121011"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="c620c-102">Método ICorDebugVariableSymbol:: GetName</span><span class="sxs-lookup"><span data-stu-id="c620c-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="c620c-103">Obtém o nome de uma variável.</span><span class="sxs-lookup"><span data-stu-id="c620c-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c620c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c620c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c620c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c620c-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="c620c-106">no O número de caracteres no buffer de `szName`.</span><span class="sxs-lookup"><span data-stu-id="c620c-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c620c-107">fora Um ponteiro para o número de caracteres realmente gravados no buffer de `szName`.</span><span class="sxs-lookup"><span data-stu-id="c620c-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="c620c-108">Um ponteiro para uma matriz de caracteres que contém o nome da variável.</span><span class="sxs-lookup"><span data-stu-id="c620c-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c620c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c620c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c620c-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c620c-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c620c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c620c-111">Requirements</span></span>  
 <span data-ttu-id="c620c-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c620c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c620c-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c620c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c620c-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c620c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c620c-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c620c-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c620c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c620c-116">See also</span></span>

- [<span data-ttu-id="c620c-117">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="c620c-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="c620c-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c620c-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
