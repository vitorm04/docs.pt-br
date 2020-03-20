---
title: iCorDebugInstanceCampo de imagemSímbolo:Método GetName
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
ms.openlocfilehash: dd925cc213ed8a6c5d1def85b3e6335751c1b594
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178766"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="e9985-102">iCorDebugInstanceCampo de imagemSímbolo:Método GetName</span><span class="sxs-lookup"><span data-stu-id="e9985-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="e9985-103">Obtém o nome do campo de instâncias.</span><span class="sxs-lookup"><span data-stu-id="e9985-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9985-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9985-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9985-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="e9985-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="e9985-106">[em] O número de `szName` caracteres no buffer.</span><span class="sxs-lookup"><span data-stu-id="e9985-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e9985-107">[fora] Um ponteiro para o número de `szName` caracteres realmente escrito no buffer.</span><span class="sxs-lookup"><span data-stu-id="e9985-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="e9985-108">[fora] Uma matriz de caracteres que armazena o nome retornado.</span><span class="sxs-lookup"><span data-stu-id="e9985-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9985-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e9985-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e9985-110">Este método está disponível apenas com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e9985-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9985-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e9985-111">Requirements</span></span>  
 <span data-ttu-id="e9985-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9985-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9985-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9985-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9985-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9985-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9985-115">**.NET Framework Versions:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9985-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9985-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="e9985-116">See also</span></span>

- [<span data-ttu-id="e9985-117">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="e9985-117">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="e9985-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e9985-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
