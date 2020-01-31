---
title: 'Método ICorDebugSymbolProvider:: getobjectize'
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
ms.openlocfilehash: fce7410b5ae9571af0c8a5963596e2af41737798
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791566"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="85ad9-102">Método ICorDebugSymbolProvider:: getobjectize</span><span class="sxs-lookup"><span data-stu-id="85ad9-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="85ad9-103">Retorna o tamanho do objeto de um objeto com base em sua assinatura de TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="85ad9-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85ad9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="85ad9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85ad9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="85ad9-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="85ad9-106">no O número de bytes na assinatura TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="85ad9-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="85ad9-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="85ad9-107">typeSig</span></span>  
 <span data-ttu-id="85ad9-108">no A assinatura TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="85ad9-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="85ad9-109">fora Um ponteiro para o tamanho do objeto.</span><span class="sxs-lookup"><span data-stu-id="85ad9-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85ad9-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="85ad9-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85ad9-111">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="85ad9-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85ad9-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="85ad9-112">Requirements</span></span>  
 <span data-ttu-id="85ad9-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85ad9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85ad9-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85ad9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85ad9-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85ad9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85ad9-116">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85ad9-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85ad9-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="85ad9-117">See also</span></span>

- [<span data-ttu-id="85ad9-118">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="85ad9-118">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="85ad9-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="85ad9-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
