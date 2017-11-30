---
title: "ICorDebugProcess7::Método SetWriteableMetadataUpdateMode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location: mscordbi.dll
api_type: COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 635792962e259f181a1ff3e0c46438951e4223db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a><span data-ttu-id="45522-102">ICorDebugProcess7::Método SetWriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="45522-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode Method</span></span>
<span data-ttu-id="45522-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="45522-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="45522-104">Configura como o depurador lida com atualizações em memória para metadados dentro do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="45522-104">Configures how the debugger handles in-memory updates to metadata within the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45522-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45522-105">Syntax</span></span>  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45522-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="45522-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="45522-107">Um [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) valor de enumeração que especifica se as atualizações aos metadados no processo de destino na memória são visíveis (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) ou não visível (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) para o depurador.</span><span class="sxs-lookup"><span data-stu-id="45522-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) enumeration value that specifies whether in-memory updates to metadata in the target process are visible (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) or not visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) to the debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45522-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="45522-108">Remarks</span></span>  
 <span data-ttu-id="45522-109">As atualizações para metadados do processo de destino podem ser obtidas de Editar e Continuar, um criador de perfil ou <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="45522-109">Updates to the metadata of the target process can come from Edit and Continue, a profiler, or <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45522-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="45522-110">Requirements</span></span>  
 <span data-ttu-id="45522-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45522-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45522-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45522-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45522-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45522-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45522-114">**Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45522-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45522-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45522-115">See Also</span></span>  
 [<span data-ttu-id="45522-116">Interface ICorDebugProcess7</span><span class="sxs-lookup"><span data-stu-id="45522-116">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 [<span data-ttu-id="45522-117">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="45522-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
