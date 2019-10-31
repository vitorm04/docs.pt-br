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
ms.openlocfilehash: 453486c9e3d98ffd6f0dcfa08e7a0a9a1c1d3342
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123398"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a><span data-ttu-id="8a6ac-102">ICorDebugProcess7::Método SetWriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="8a6ac-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode Method</span></span>
<span data-ttu-id="8a6ac-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="8a6ac-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="8a6ac-104">Configura como o depurador lida com atualizações em memória para metadados dentro do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="8a6ac-104">Configures how the debugger handles in-memory updates to metadata within the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a6ac-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a6ac-105">Syntax</span></span>  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a6ac-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8a6ac-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="8a6ac-107">Um valor de enumeração [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) que especifica se as atualizações na memória para os metadados no processo de destino são visíveis (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) ou não visíveis (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) para o depurador.</span><span class="sxs-lookup"><span data-stu-id="8a6ac-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) enumeration value that specifies whether in-memory updates to metadata in the target process are visible (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) or not visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) to the debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a6ac-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8a6ac-108">Remarks</span></span>  
 <span data-ttu-id="8a6ac-109">As atualizações para metadados do processo de destino podem ser obtidas de Editar e Continuar, um criador de perfil ou <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8a6ac-109">Updates to the metadata of the target process can come from Edit and Continue, a profiler, or <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a6ac-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8a6ac-110">Requirements</span></span>  
 <span data-ttu-id="8a6ac-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a6ac-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a6ac-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a6ac-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a6ac-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a6ac-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a6ac-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a6ac-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a6ac-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a6ac-115">See also</span></span>

- [<span data-ttu-id="8a6ac-116">Interface ICorDebugProcess7</span><span class="sxs-lookup"><span data-stu-id="8a6ac-116">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)
- [<span data-ttu-id="8a6ac-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8a6ac-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
