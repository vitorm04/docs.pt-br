---
title: 'Método ICorDebugSymbolProvider:: GetCodeRange'
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
ms.openlocfilehash: dbe042641cadae182efac30502a70631be359bbe
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791647"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="ad9e0-102">Método ICorDebugSymbolProvider:: GetCodeRange</span><span class="sxs-lookup"><span data-stu-id="ad9e0-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="ad9e0-103">Obtém o endereço inicial e o tamanho do método de acordo com um endereço virtual relativo (RVA) em um método.</span><span class="sxs-lookup"><span data-stu-id="ad9e0-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad9e0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad9e0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad9e0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ad9e0-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="ad9e0-106">no O endereço virtual relativo (RVA) em um método.</span><span class="sxs-lookup"><span data-stu-id="ad9e0-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="ad9e0-107">fora Um ponteiro para o endereço inicial do método.</span><span class="sxs-lookup"><span data-stu-id="ad9e0-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="ad9e0-108">Um ponteiro para o tamanho do código do método (o número de bytes do código do método).</span><span class="sxs-lookup"><span data-stu-id="ad9e0-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad9e0-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ad9e0-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad9e0-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ad9e0-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad9e0-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="ad9e0-111">Requirements</span></span>  
 <span data-ttu-id="ad9e0-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad9e0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad9e0-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad9e0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad9e0-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad9e0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad9e0-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad9e0-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad9e0-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="ad9e0-116">See also</span></span>

- [<span data-ttu-id="ad9e0-117">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="ad9e0-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="ad9e0-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ad9e0-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
