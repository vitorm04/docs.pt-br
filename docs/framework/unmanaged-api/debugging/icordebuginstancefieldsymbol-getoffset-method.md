---
title: 'Método ICorDebugInstanceFieldSymbol:: GetOffset'
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: f7c13d397b39698bdf1a22f14820680e1fd0a25f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782298"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="dfe2d-102">Método ICorDebugInstanceFieldSymbol:: GetOffset</span><span class="sxs-lookup"><span data-stu-id="dfe2d-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="dfe2d-103">Obtém o deslocamento em bytes deste campo de instância em sua classe pai.</span><span class="sxs-lookup"><span data-stu-id="dfe2d-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfe2d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dfe2d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfe2d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dfe2d-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="dfe2d-106">Um ponteiro para o número de bytes que esse campo de instância é deslocado em sua classe pai.</span><span class="sxs-lookup"><span data-stu-id="dfe2d-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfe2d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="dfe2d-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dfe2d-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="dfe2d-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfe2d-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="dfe2d-109">Requirements</span></span>  
 <span data-ttu-id="dfe2d-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfe2d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfe2d-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dfe2d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfe2d-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfe2d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfe2d-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfe2d-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfe2d-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="dfe2d-114">See also</span></span>

- [<span data-ttu-id="dfe2d-115">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="dfe2d-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="dfe2d-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="dfe2d-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
