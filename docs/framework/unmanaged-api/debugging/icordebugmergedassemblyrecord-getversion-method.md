---
title: ICorDebugMergeDRecord::GetVersion Method
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 5dc9995e88086da854d2e9382cef81b229ff9dc9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178680"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="2143b-102">ICorDebugMergeDRecord::GetVersion Method</span><span class="sxs-lookup"><span data-stu-id="2143b-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="2143b-103">Obtém informações da versão da assembléia.</span><span class="sxs-lookup"><span data-stu-id="2143b-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2143b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2143b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,
   [out] USHORT *pMinor,
   [out] USHORT *pBuild,
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2143b-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="2143b-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="2143b-106">[fora] Um ponteiro para o número da versão principal.</span><span class="sxs-lookup"><span data-stu-id="2143b-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="2143b-107">[fora] Um ponteiro para o número da versão menor.</span><span class="sxs-lookup"><span data-stu-id="2143b-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="2143b-108">[fora] Um ponteiro para o número de compilação.</span><span class="sxs-lookup"><span data-stu-id="2143b-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="2143b-109">[fora] Um ponteiro para o número de revisão.</span><span class="sxs-lookup"><span data-stu-id="2143b-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2143b-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="2143b-110">Remarks</span></span>  
 <span data-ttu-id="2143b-111">Para obter informações sobre números <xref:System.Version> de versão de montagem, consulte o tópico da classe.</span><span class="sxs-lookup"><span data-stu-id="2143b-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2143b-112">Este método está disponível apenas com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2143b-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2143b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2143b-113">Requirements</span></span>  
 <span data-ttu-id="2143b-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2143b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2143b-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2143b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2143b-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2143b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2143b-117">**.NET Framework Versions:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2143b-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2143b-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="2143b-118">See also</span></span>

- [<span data-ttu-id="2143b-119">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="2143b-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="2143b-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2143b-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
