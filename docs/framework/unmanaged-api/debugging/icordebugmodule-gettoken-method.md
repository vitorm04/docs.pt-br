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
ms.openlocfilehash: 683c2853ea2ed43e61eb666ec56619cb58cde273
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129490"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="cce06-102">Método ICorDebugModule::GetToken</span><span class="sxs-lookup"><span data-stu-id="cce06-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="cce06-103">Obtém o token para a entrada de tabela deste módulo.</span><span class="sxs-lookup"><span data-stu-id="cce06-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cce06-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cce06-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cce06-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cce06-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="cce06-106">fora Um ponteiro para o token de `mdModule` que faz referência aos metadados do módulo.</span><span class="sxs-lookup"><span data-stu-id="cce06-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cce06-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="cce06-107">Remarks</span></span>  
 <span data-ttu-id="cce06-108">O token pode ser passado para as interfaces de importação de metadados [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)e [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="cce06-108">The token can be passed to the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cce06-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cce06-109">Requirements</span></span>  
 <span data-ttu-id="cce06-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cce06-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cce06-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cce06-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cce06-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cce06-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cce06-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cce06-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cce06-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cce06-114">See also</span></span>

- [<span data-ttu-id="cce06-115">Metadados</span><span class="sxs-lookup"><span data-stu-id="cce06-115">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
