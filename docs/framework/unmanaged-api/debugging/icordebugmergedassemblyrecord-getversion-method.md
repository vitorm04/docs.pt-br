---
title: Método ICorDebugMergedAssemblyRecord::GetVersion
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36cf8647b3caafeaae2db3c2fd53471496e922fa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109533"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="2fd41-102">Método ICorDebugMergedAssemblyRecord::GetVersion</span><span class="sxs-lookup"><span data-stu-id="2fd41-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="2fd41-103">Obtém informações de versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="2fd41-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fd41-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2fd41-104">Syntax</span></span>  
  
```  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fd41-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2fd41-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="2fd41-106">[out] Um ponteiro para o número de versão principal.</span><span class="sxs-lookup"><span data-stu-id="2fd41-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="2fd41-107">[out] Um ponteiro para o número de versão secundária.</span><span class="sxs-lookup"><span data-stu-id="2fd41-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="2fd41-108">[out] Um ponteiro para o número da compilação.</span><span class="sxs-lookup"><span data-stu-id="2fd41-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="2fd41-109">[out] Um ponteiro para o número de revisão.</span><span class="sxs-lookup"><span data-stu-id="2fd41-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fd41-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="2fd41-110">Remarks</span></span>  
 <span data-ttu-id="2fd41-111">Para obter informações sobre números de versão do assembly, consulte o <xref:System.Version> tópico da classe.</span><span class="sxs-lookup"><span data-stu-id="2fd41-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2fd41-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2fd41-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fd41-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2fd41-113">Requirements</span></span>  
 <span data-ttu-id="2fd41-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fd41-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fd41-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fd41-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fd41-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fd41-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fd41-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fd41-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fd41-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fd41-118">See also</span></span>

- [<span data-ttu-id="2fd41-119">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="2fd41-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="2fd41-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2fd41-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
