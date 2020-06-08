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
ms.openlocfilehash: 4e2b2501b6b7117cefcfa43511ef20f25106bb42
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503573"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="92e3b-102">Método IMetaDataImport::GetModuleFromScope</span><span class="sxs-lookup"><span data-stu-id="92e3b-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="92e3b-103">Obtém um token de metadados para o módulo referenciado no escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="92e3b-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92e3b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92e3b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92e3b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="92e3b-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="92e3b-106">fora Um ponteiro para o token que representa o módulo referenciado no escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="92e3b-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92e3b-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="92e3b-107">Requirements</span></span>  
 <span data-ttu-id="92e3b-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92e3b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92e3b-109">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="92e3b-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="92e3b-110">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="92e3b-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="92e3b-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92e3b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92e3b-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="92e3b-112">See also</span></span>

- [<span data-ttu-id="92e3b-113">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="92e3b-113">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="92e3b-114">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="92e3b-114">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
