---
title: 'Método ICorDebugMergedAssemblyRecord:: GetPublicKey'
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: 51724aa1ee6101c50c7cdb4b6071fb458814f483
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213537"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="4626d-102">Método ICorDebugMergedAssemblyRecord:: GetPublicKey</span><span class="sxs-lookup"><span data-stu-id="4626d-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="4626d-103">Obtém a chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="4626d-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4626d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4626d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,
   [out] ULONG32 *pcbPublicKey,
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4626d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4626d-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="4626d-106">no O número máximo de bytes na `pbPublicKey` matriz.</span><span class="sxs-lookup"><span data-stu-id="4626d-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="4626d-107">fora Um ponteiro para o número real de bytes gravados na `pbPublicKey` matriz.</span><span class="sxs-lookup"><span data-stu-id="4626d-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="4626d-108">fora Um ponteiro para uma matriz de bytes que contém a chave pública do assembly.</span><span class="sxs-lookup"><span data-stu-id="4626d-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4626d-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="4626d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4626d-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4626d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4626d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4626d-111">Requirements</span></span>  
 <span data-ttu-id="4626d-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4626d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4626d-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4626d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4626d-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4626d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4626d-115">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4626d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4626d-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="4626d-116">See also</span></span>

- [<span data-ttu-id="4626d-117">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="4626d-117">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="4626d-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4626d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
