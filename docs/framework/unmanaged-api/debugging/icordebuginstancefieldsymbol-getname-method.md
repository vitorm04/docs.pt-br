---
title: 'Método ICorDebugInstanceFieldSymbol:: GetName'
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
ms.openlocfilehash: 0f1b648f494a2f2676374cfd13db46b70f1f195c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209988"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="ee574-102">Método ICorDebugInstanceFieldSymbol:: GetName</span><span class="sxs-lookup"><span data-stu-id="ee574-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="ee574-103">Obtém o nome do campo de instância.</span><span class="sxs-lookup"><span data-stu-id="ee574-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee574-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ee574-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee574-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ee574-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ee574-106">no O número de caracteres no `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="ee574-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ee574-107">fora Um ponteiro para o número de caracteres realmente gravados no `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="ee574-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="ee574-108">fora Uma matriz de caracteres que armazena o nome retornado.</span><span class="sxs-lookup"><span data-stu-id="ee574-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee574-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ee574-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee574-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ee574-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee574-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ee574-111">Requirements</span></span>  
 <span data-ttu-id="ee574-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee574-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee574-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee574-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee574-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee574-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee574-115">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee574-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee574-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="ee574-116">See also</span></span>

- [<span data-ttu-id="ee574-117">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="ee574-117">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="ee574-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ee574-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
