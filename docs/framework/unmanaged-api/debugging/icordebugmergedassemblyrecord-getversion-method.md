---
title: 'Método ICorDebugMergedAssemblyRecord:: GetVersion'
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d9133ab1b7d3985d3a383bb36dcbea315548c00
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939922"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="3fd97-102">Método ICorDebugMergedAssemblyRecord:: GetVersion</span><span class="sxs-lookup"><span data-stu-id="3fd97-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="3fd97-103">Obtém as informações de versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="3fd97-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fd97-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3fd97-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fd97-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3fd97-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="3fd97-106">fora Um ponteiro para o número de versão principal.</span><span class="sxs-lookup"><span data-stu-id="3fd97-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="3fd97-107">fora Um ponteiro para o número de versão secundária.</span><span class="sxs-lookup"><span data-stu-id="3fd97-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="3fd97-108">fora Um ponteiro para o número da compilação.</span><span class="sxs-lookup"><span data-stu-id="3fd97-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="3fd97-109">fora Um ponteiro para o número de revisão.</span><span class="sxs-lookup"><span data-stu-id="3fd97-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fd97-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="3fd97-110">Remarks</span></span>  
 <span data-ttu-id="3fd97-111">Para obter informações sobre números de versão do assembly <xref:System.Version> , consulte o tópico classe.</span><span class="sxs-lookup"><span data-stu-id="3fd97-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3fd97-112">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3fd97-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fd97-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3fd97-113">Requirements</span></span>  
 <span data-ttu-id="3fd97-114">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fd97-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fd97-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3fd97-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fd97-116">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fd97-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fd97-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fd97-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fd97-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3fd97-118">See also</span></span>

- [<span data-ttu-id="3fd97-119">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="3fd97-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="3fd97-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3fd97-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
