---
title: 'Método ICorDebugVariableSymbol:: GetName'
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: ea414a39e140c74df736764dbbb1bb3934bda78f
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397123"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="5f4db-102">Método ICorDebugVariableSymbol:: GetName</span><span class="sxs-lookup"><span data-stu-id="5f4db-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="5f4db-103">Obtém o nome de uma variável.</span><span class="sxs-lookup"><span data-stu-id="5f4db-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f4db-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f4db-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f4db-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5f4db-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="5f4db-106">no O número de caracteres no `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="5f4db-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5f4db-107">fora Um ponteiro para o número de caracteres realmente gravados no `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="5f4db-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="5f4db-108">Um ponteiro para uma matriz de caracteres que contém o nome da variável.</span><span class="sxs-lookup"><span data-stu-id="5f4db-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f4db-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="5f4db-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f4db-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5f4db-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f4db-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5f4db-111">Requirements</span></span>  
 <span data-ttu-id="5f4db-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f4db-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f4db-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f4db-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f4db-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f4db-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f4db-115">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f4db-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f4db-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="5f4db-116">See also</span></span>

- [<span data-ttu-id="5f4db-117">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="5f4db-117">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="5f4db-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5f4db-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
