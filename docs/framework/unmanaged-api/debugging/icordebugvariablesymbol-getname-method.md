---
title: Método ICorDebugVariableSymbol::GetName
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f514acbd772c9d33ec4372cfaccb778d6bb41eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170164"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="759dc-102">Método ICorDebugVariableSymbol::GetName</span><span class="sxs-lookup"><span data-stu-id="759dc-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="759dc-103">Obtém o nome de uma variável.</span><span class="sxs-lookup"><span data-stu-id="759dc-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="759dc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="759dc-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="759dc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="759dc-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="759dc-106">[in] O número de caracteres no `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="759dc-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="759dc-107">[out] Um ponteiro para o número de caracteres gravados, na verdade, o `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="759dc-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="759dc-108">Um ponteiro para uma matriz de caracteres que contém o nome da variável.</span><span class="sxs-lookup"><span data-stu-id="759dc-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="759dc-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="759dc-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="759dc-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="759dc-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="759dc-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="759dc-111">Requirements</span></span>  
 <span data-ttu-id="759dc-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="759dc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="759dc-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="759dc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="759dc-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="759dc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="759dc-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="759dc-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="759dc-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="759dc-116">See also</span></span>

- [<span data-ttu-id="759dc-117">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="759dc-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="759dc-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="759dc-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
