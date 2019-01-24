---
title: Método ICorDebugMergedAssemblyRecord::GetPublicKeyToken
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f77871c8547f250d4b46c11c1a0be25b6ef68a88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54581922"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="28edf-102">Método ICorDebugMergedAssemblyRecord::GetPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="28edf-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="28edf-103">Obtém o token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="28edf-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28edf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28edf-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28edf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="28edf-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="28edf-106">[in] O número máximo de bytes no `pbPublicKeyToken` matriz.</span><span class="sxs-lookup"><span data-stu-id="28edf-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="28edf-107">[out] Um ponteiro para o número real de bytes gravados para o `pbPublicKeyToken` matriz.</span><span class="sxs-lookup"><span data-stu-id="28edf-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="28edf-108">[out] Um ponteiro para uma matriz de bytes que contém o token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="28edf-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28edf-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="28edf-109">Remarks</span></span>  
 <span data-ttu-id="28edf-110">O token de chave pública do assembly é os último oito bytes de um hash SHA1 de sua chave pública.</span><span class="sxs-lookup"><span data-stu-id="28edf-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28edf-111">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="28edf-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28edf-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="28edf-112">Requirements</span></span>  
 <span data-ttu-id="28edf-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28edf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28edf-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28edf-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28edf-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28edf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28edf-116">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28edf-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28edf-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28edf-117">See also</span></span>
- [<span data-ttu-id="28edf-118">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="28edf-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="28edf-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="28edf-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
