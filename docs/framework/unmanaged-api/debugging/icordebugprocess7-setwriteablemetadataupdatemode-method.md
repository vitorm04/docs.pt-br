---
title: ICorDebugProcess7::Método SetWriteableMetadataUpdateMode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a67f93a3f3f75b89bc3f0240995471bc0bf44992
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419751"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a><span data-ttu-id="d406e-102">ICorDebugProcess7::Método SetWriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="d406e-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode Method</span></span>
<span data-ttu-id="d406e-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="d406e-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d406e-104">Configura como o depurador lida com atualizações em memória para metadados dentro do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="d406e-104">Configures how the debugger handles in-memory updates to metadata within the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d406e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d406e-105">Syntax</span></span>  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d406e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d406e-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="d406e-107">Um [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) valor de enumeração que especifica se as atualizações aos metadados no processo de destino na memória são visíveis (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) ou não visível (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) para o depurador.</span><span class="sxs-lookup"><span data-stu-id="d406e-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) enumeration value that specifies whether in-memory updates to metadata in the target process are visible (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) or not visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) to the debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d406e-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="d406e-108">Remarks</span></span>  
 <span data-ttu-id="d406e-109">As atualizações para metadados do processo de destino podem ser obtidas de Editar e Continuar, um criador de perfil ou <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d406e-109">Updates to the metadata of the target process can come from Edit and Continue, a profiler, or <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d406e-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d406e-110">Requirements</span></span>  
 <span data-ttu-id="d406e-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d406e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d406e-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d406e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d406e-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d406e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d406e-114">**Versões do .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d406e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d406e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d406e-115">See Also</span></span>  
 [<span data-ttu-id="d406e-116">Interface ICorDebugProcess7</span><span class="sxs-lookup"><span data-stu-id="d406e-116">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 [<span data-ttu-id="d406e-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d406e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
