---
title: Método ICorDebugModule::GetToken
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetToken
helpviewer_keywords:
- ICorDebugModule::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: f759f87a-18ae-4c1a-8300-29b803432d0a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30097ff0cd92253897a366a5a18f305eddb06b5b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763521"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="e451b-102">Método ICorDebugModule::GetToken</span><span class="sxs-lookup"><span data-stu-id="e451b-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="e451b-103">Obtém o token para a entrada da tabela para esse módulo.</span><span class="sxs-lookup"><span data-stu-id="e451b-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e451b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e451b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e451b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e451b-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="e451b-106">[out] Um ponteiro para o `mdModule` token que faz referência a metadados do módulo.</span><span class="sxs-lookup"><span data-stu-id="e451b-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e451b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e451b-107">Remarks</span></span>  
 <span data-ttu-id="e451b-108">O token pode ser passado para o [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), e [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfaces de importação de metadados.</span><span class="sxs-lookup"><span data-stu-id="e451b-108">The token can be passed to the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e451b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e451b-109">Requirements</span></span>  
 <span data-ttu-id="e451b-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e451b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e451b-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e451b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e451b-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e451b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e451b-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e451b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e451b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e451b-114">See also</span></span>

- [<span data-ttu-id="e451b-115">Metadados</span><span class="sxs-lookup"><span data-stu-id="e451b-115">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
