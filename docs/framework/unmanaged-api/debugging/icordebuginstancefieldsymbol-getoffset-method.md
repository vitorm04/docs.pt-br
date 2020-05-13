---
title: 'Método ICorDebugInstanceFieldSymbol:: GetOffset'
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: 7d553c1a446e06f34c20da18c0edfe6773cfb597
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209975"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="cfbb3-102">Método ICorDebugInstanceFieldSymbol:: GetOffset</span><span class="sxs-lookup"><span data-stu-id="cfbb3-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="cfbb3-103">Obtém o deslocamento em bytes deste campo de instância em sua classe pai.</span><span class="sxs-lookup"><span data-stu-id="cfbb3-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfbb3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cfbb3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfbb3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cfbb3-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="cfbb3-106">Um ponteiro para o número de bytes que esse campo de instância é deslocado em sua classe pai.</span><span class="sxs-lookup"><span data-stu-id="cfbb3-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfbb3-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="cfbb3-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cfbb3-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cfbb3-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfbb3-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cfbb3-109">Requirements</span></span>  
 <span data-ttu-id="cfbb3-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfbb3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfbb3-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cfbb3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfbb3-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfbb3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfbb3-113">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfbb3-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfbb3-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="cfbb3-114">See also</span></span>

- [<span data-ttu-id="cfbb3-115">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="cfbb3-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="cfbb3-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="cfbb3-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
