---
title: "Método ICorDebugMergedAssemblyRecord::GetPublicKey"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a47eb051cd9922b8640b8b612ff0ac5882b6a8ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="da3c7-102">Método ICorDebugMergedAssemblyRecord::GetPublicKey</span><span class="sxs-lookup"><span data-stu-id="da3c7-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="da3c7-103">Obtém a chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="da3c7-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da3c7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da3c7-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da3c7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="da3c7-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="da3c7-106">[in] O número máximo de bytes a `pbPublicKey` matriz.</span><span class="sxs-lookup"><span data-stu-id="da3c7-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="da3c7-107">[out] Um ponteiro para o número real de bytes gravados para o `pbPublicKey` matriz.</span><span class="sxs-lookup"><span data-stu-id="da3c7-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="da3c7-108">[out] Um ponteiro para uma matriz de bytes que contém a chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="da3c7-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da3c7-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="da3c7-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da3c7-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="da3c7-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da3c7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da3c7-111">Requirements</span></span>  
 <span data-ttu-id="da3c7-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da3c7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da3c7-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da3c7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da3c7-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da3c7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da3c7-115">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da3c7-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da3c7-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da3c7-116">See Also</span></span>  
 [<span data-ttu-id="da3c7-117">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="da3c7-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="da3c7-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="da3c7-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
