---
title: "Método ICorDebugMergedAssemblyRecord::GetVersion"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6a3865a82efec63aa85f4a0eee286bf8b79bd00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="8ce0d-102">Método ICorDebugMergedAssemblyRecord::GetVersion</span><span class="sxs-lookup"><span data-stu-id="8ce0d-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="8ce0d-103">Obtém informações de versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="8ce0d-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ce0d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ce0d-104">Syntax</span></span>  
  
```  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ce0d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8ce0d-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="8ce0d-106">[out] Um ponteiro para o número de versão principal.</span><span class="sxs-lookup"><span data-stu-id="8ce0d-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="8ce0d-107">[out] Um ponteiro para o número de versão secundária.</span><span class="sxs-lookup"><span data-stu-id="8ce0d-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="8ce0d-108">[out] Um ponteiro para o número de compilação.</span><span class="sxs-lookup"><span data-stu-id="8ce0d-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="8ce0d-109">[out] Um ponteiro para o número de revisão.</span><span class="sxs-lookup"><span data-stu-id="8ce0d-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ce0d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="8ce0d-110">Remarks</span></span>  
 <span data-ttu-id="8ce0d-111">Para obter informações sobre números de versão do assembly, consulte o <xref:System.Version> tópico sobre a classe.</span><span class="sxs-lookup"><span data-stu-id="8ce0d-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ce0d-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8ce0d-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ce0d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8ce0d-113">Requirements</span></span>  
 <span data-ttu-id="8ce0d-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ce0d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ce0d-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ce0d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ce0d-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ce0d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ce0d-117">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ce0d-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ce0d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ce0d-118">See Also</span></span>  
 [<span data-ttu-id="8ce0d-119">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="8ce0d-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="8ce0d-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8ce0d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
