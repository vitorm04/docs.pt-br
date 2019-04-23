---
title: Método IMetaDataImport::GetModuleFromScope
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f40e6bfdbebdadc41da52564348c6070c18372c8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59194669"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="c1072-102">Método IMetaDataImport::GetModuleFromScope</span><span class="sxs-lookup"><span data-stu-id="c1072-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="c1072-103">Obtém os metadados de um token para o módulo referenciado no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="c1072-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1072-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1072-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1072-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c1072-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="c1072-106">[out] Um ponteiro para o token que representa o módulo referenciado no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="c1072-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1072-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c1072-107">Requirements</span></span>  
 <span data-ttu-id="c1072-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1072-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1072-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c1072-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c1072-110">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c1072-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c1072-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1072-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1072-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1072-112">See also</span></span>

- [<span data-ttu-id="c1072-113">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c1072-113">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c1072-114">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c1072-114">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
