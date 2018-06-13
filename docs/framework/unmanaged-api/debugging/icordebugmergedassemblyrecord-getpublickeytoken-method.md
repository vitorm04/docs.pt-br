---
title: Método ICorDebugMergedAssemblyRecord::GetPublicKeyToken
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71b70118d77deb7ad6879ed4bd48b1cd37122820
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414002"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="e6f07-102">Método ICorDebugMergedAssemblyRecord::GetPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="e6f07-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="e6f07-103">Obtém a chave pública do assembly token.</span><span class="sxs-lookup"><span data-stu-id="e6f07-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6f07-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6f07-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6f07-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e6f07-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="e6f07-106">[in] O número máximo de bytes a `pbPublicKeyToken` matriz.</span><span class="sxs-lookup"><span data-stu-id="e6f07-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="e6f07-107">[out] Um ponteiro para o número real de bytes gravados para o `pbPublicKeyToken` matriz.</span><span class="sxs-lookup"><span data-stu-id="e6f07-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="e6f07-108">[out] Um ponteiro para uma matriz de bytes que contém o token de chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="e6f07-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6f07-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e6f07-109">Remarks</span></span>  
 <span data-ttu-id="e6f07-110">Token de chave pública de um assembly é o último oito bytes de um hash SHA1 de sua chave pública.</span><span class="sxs-lookup"><span data-stu-id="e6f07-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6f07-111">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e6f07-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6f07-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e6f07-112">Requirements</span></span>  
 <span data-ttu-id="e6f07-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6f07-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6f07-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6f07-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6f07-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6f07-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6f07-116">**Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6f07-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6f07-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6f07-117">See Also</span></span>  
 [<span data-ttu-id="e6f07-118">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="e6f07-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="e6f07-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e6f07-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
