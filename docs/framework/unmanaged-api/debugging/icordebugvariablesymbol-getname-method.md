---
title: 'Método ICorDebugVariableSymbol:: GetName'
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: 172eea452442aa94ea010e2c434908ab8d040a93
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790919"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="2a5e0-102">Método ICorDebugVariableSymbol:: GetName</span><span class="sxs-lookup"><span data-stu-id="2a5e0-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="2a5e0-103">Obtém o nome de uma variável.</span><span class="sxs-lookup"><span data-stu-id="2a5e0-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a5e0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a5e0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a5e0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2a5e0-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="2a5e0-106">no O número de caracteres no buffer de `szName`.</span><span class="sxs-lookup"><span data-stu-id="2a5e0-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="2a5e0-107">fora Um ponteiro para o número de caracteres realmente gravados no buffer de `szName`.</span><span class="sxs-lookup"><span data-stu-id="2a5e0-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="2a5e0-108">Um ponteiro para uma matriz de caracteres que contém o nome da variável.</span><span class="sxs-lookup"><span data-stu-id="2a5e0-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a5e0-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a5e0-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a5e0-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2a5e0-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a5e0-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="2a5e0-111">Requirements</span></span>  
 <span data-ttu-id="2a5e0-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a5e0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a5e0-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a5e0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a5e0-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a5e0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a5e0-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a5e0-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a5e0-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="2a5e0-116">See also</span></span>

- [<span data-ttu-id="2a5e0-117">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="2a5e0-117">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="2a5e0-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2a5e0-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
