---
title: Método ICorDebugSymbolProvider::GetObjectSize
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbcdb5541fdd49944f462321dc24131a32a42391
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953758"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="1cda9-102">Método ICorDebugSymbolProvider::GetObjectSize</span><span class="sxs-lookup"><span data-stu-id="1cda9-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="1cda9-103">Retorna o tamanho do objeto para um objeto com base em sua assinatura typespec.</span><span class="sxs-lookup"><span data-stu-id="1cda9-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cda9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1cda9-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cda9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1cda9-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="1cda9-106">[in] O número de bytes na assinatura typespec.</span><span class="sxs-lookup"><span data-stu-id="1cda9-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="1cda9-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="1cda9-107">typeSig</span></span>  
 <span data-ttu-id="1cda9-108">[in] A assinatura de typespec.</span><span class="sxs-lookup"><span data-stu-id="1cda9-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="1cda9-109">[out] Um ponteiro para o tamanho do objeto.</span><span class="sxs-lookup"><span data-stu-id="1cda9-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cda9-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="1cda9-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1cda9-111">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1cda9-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cda9-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1cda9-112">Requirements</span></span>  
 <span data-ttu-id="1cda9-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cda9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cda9-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1cda9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1cda9-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1cda9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cda9-116">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cda9-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cda9-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cda9-117">See also</span></span>

- [<span data-ttu-id="1cda9-118">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="1cda9-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="1cda9-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1cda9-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
