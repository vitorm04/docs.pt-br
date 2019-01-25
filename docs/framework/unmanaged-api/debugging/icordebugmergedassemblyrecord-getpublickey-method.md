---
title: Método ICorDebugMergedAssemblyRecord::GetPublicKey
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2b7c2f70b4776c5448d23f37c520bb5b07c051e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541645"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="904ab-102">Método ICorDebugMergedAssemblyRecord::GetPublicKey</span><span class="sxs-lookup"><span data-stu-id="904ab-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="904ab-103">Obtém a chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="904ab-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="904ab-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="904ab-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="904ab-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="904ab-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="904ab-106">[in] O número máximo de bytes no `pbPublicKey` matriz.</span><span class="sxs-lookup"><span data-stu-id="904ab-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="904ab-107">[out] Um ponteiro para o número real de bytes gravados para o `pbPublicKey` matriz.</span><span class="sxs-lookup"><span data-stu-id="904ab-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="904ab-108">[out] Um ponteiro para uma matriz de bytes que contém a chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="904ab-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="904ab-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="904ab-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="904ab-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="904ab-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="904ab-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="904ab-111">Requirements</span></span>  
 <span data-ttu-id="904ab-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="904ab-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="904ab-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="904ab-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="904ab-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="904ab-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="904ab-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="904ab-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="904ab-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="904ab-116">See also</span></span>
- [<span data-ttu-id="904ab-117">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="904ab-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="904ab-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="904ab-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
