---
title: Método ICorDebugMergedAssemblyRecord::GetPublicKey
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 610e46d5cb550a266c5558c49239d1818c1e85de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107270"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="77ae4-102">Método ICorDebugMergedAssemblyRecord::GetPublicKey</span><span class="sxs-lookup"><span data-stu-id="77ae4-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="77ae4-103">Obtém a chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="77ae4-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77ae4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77ae4-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77ae4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="77ae4-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="77ae4-106">[in] O número máximo de bytes no `pbPublicKey` matriz.</span><span class="sxs-lookup"><span data-stu-id="77ae4-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="77ae4-107">[out] Um ponteiro para o número real de bytes gravados para o `pbPublicKey` matriz.</span><span class="sxs-lookup"><span data-stu-id="77ae4-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="77ae4-108">[out] Um ponteiro para uma matriz de bytes que contém a chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="77ae4-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77ae4-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="77ae4-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77ae4-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="77ae4-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77ae4-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="77ae4-111">Requirements</span></span>  
 <span data-ttu-id="77ae4-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77ae4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77ae4-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77ae4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77ae4-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77ae4-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="77ae4-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="77ae4-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="77ae4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77ae4-116">See also</span></span>

- [<span data-ttu-id="77ae4-117">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="77ae4-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="77ae4-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="77ae4-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
