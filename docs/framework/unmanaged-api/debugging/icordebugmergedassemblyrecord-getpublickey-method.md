---
title: 'Método ICorDebugMergedAssemblyRecord:: GetPublicKey'
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e08b1edcef3e93caa82be3a4342c6a0264734bea
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940018"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="b2454-102">Método ICorDebugMergedAssemblyRecord:: GetPublicKey</span><span class="sxs-lookup"><span data-stu-id="b2454-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="b2454-103">Obtém a chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="b2454-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2454-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2454-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2454-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b2454-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="b2454-106">no O número máximo de bytes na `pbPublicKey` matriz.</span><span class="sxs-lookup"><span data-stu-id="b2454-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="b2454-107">fora Um ponteiro para o número real de bytes gravados `pbPublicKey` na matriz.</span><span class="sxs-lookup"><span data-stu-id="b2454-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="b2454-108">fora Um ponteiro para uma matriz de bytes que contém a chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="b2454-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2454-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b2454-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2454-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b2454-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2454-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b2454-111">Requirements</span></span>  
 <span data-ttu-id="b2454-112">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2454-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2454-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2454-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2454-114">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2454-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2454-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2454-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2454-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2454-116">See also</span></span>

- [<span data-ttu-id="b2454-117">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="b2454-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="b2454-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b2454-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
