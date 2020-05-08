---
title: Método ICorDebugDataTarget2::GetImageFromPointer
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
ms.openlocfilehash: f316ddb04cdaad2f528e8fac0a970ca6263ebd8f
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976467"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="89023-102">Método ICorDebugDataTarget2::GetImageFromPointer</span><span class="sxs-lookup"><span data-stu-id="89023-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="89023-103">Retorna o endereço base do módulo e o tamanho de um endereço no módulo.</span><span class="sxs-lookup"><span data-stu-id="89023-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89023-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89023-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,
   [out] CORDB_ADDRESS *pImageBase,
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89023-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="89023-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="89023-106">Um valor [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) que representa um endereço em um módulo.</span><span class="sxs-lookup"><span data-stu-id="89023-106">A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="89023-107">fora Um valor [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) que representa o endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="89023-107">[out] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="89023-108">Um ponteiro para o tamanho do módulo.</span><span class="sxs-lookup"><span data-stu-id="89023-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89023-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="89023-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89023-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="89023-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89023-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="89023-111">Requirements</span></span>  
 <span data-ttu-id="89023-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89023-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89023-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89023-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89023-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89023-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89023-115">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89023-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89023-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89023-116">See also</span></span>

- [<span data-ttu-id="89023-117">Interface ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="89023-117">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="89023-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="89023-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
