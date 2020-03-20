---
title: ICorDebugMergeDRecord::GetPublicKey Method
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: 632e990899346493d5a7df08d293e25b83ed7ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178735"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="d49aa-102">ICorDebugMergeDRecord::GetPublicKey Method</span><span class="sxs-lookup"><span data-stu-id="d49aa-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="d49aa-103">Fica com a chave pública da assembléia.</span><span class="sxs-lookup"><span data-stu-id="d49aa-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d49aa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d49aa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,
   [out] ULONG32 *pcbPublicKey,
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d49aa-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="d49aa-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="d49aa-106">[em] O número máximo de bytes na `pbPublicKey` matriz.</span><span class="sxs-lookup"><span data-stu-id="d49aa-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="d49aa-107">[fora] Um ponteiro para o número real de `pbPublicKey` bytes escritos para a matriz.</span><span class="sxs-lookup"><span data-stu-id="d49aa-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="d49aa-108">[fora] Um ponteiro para uma matriz de bytes que contém a chave pública da assembléia.</span><span class="sxs-lookup"><span data-stu-id="d49aa-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d49aa-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="d49aa-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d49aa-110">Este método está disponível apenas com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d49aa-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d49aa-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d49aa-111">Requirements</span></span>  
 <span data-ttu-id="d49aa-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d49aa-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d49aa-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d49aa-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d49aa-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d49aa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d49aa-115">**.NET Framework Versions:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d49aa-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d49aa-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="d49aa-116">See also</span></span>

- [<span data-ttu-id="d49aa-117">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="d49aa-117">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="d49aa-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d49aa-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
