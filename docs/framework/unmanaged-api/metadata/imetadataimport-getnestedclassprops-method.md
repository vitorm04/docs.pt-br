---
title: Método IMetaDataImport::GetNestedClassProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNestedClassProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNestedClassProps
helpviewer_keywords:
- GetNestedClassProps method [.NET Framework metadata]
- IMetaDataImport::GetNestedClassProps method [.NET Framework metadata]
ms.assetid: 704d19f1-bdef-4745-af8c-6476eb246fb3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7dd59c1e0e8b28c557910da3fd9c6489370cc62
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778956"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="f3ff6-102">Método IMetaDataImport::GetNestedClassProps</span><span class="sxs-lookup"><span data-stu-id="f3ff6-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="f3ff6-103">Obtém o token de TypeDef para o pai <xref:System.Type> do tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="f3ff6-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3ff6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3ff6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3ff6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f3ff6-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="f3ff6-106">[in] Um TypeDef token que representa o <xref:System.Type> para retornar a classe pai token.</span><span class="sxs-lookup"><span data-stu-id="f3ff6-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="f3ff6-107">[out] Um ponteiro para o token de TypeDef para o <xref:System.Type> que `tdNestedClass` está aninhado no.</span><span class="sxs-lookup"><span data-stu-id="f3ff6-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3ff6-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f3ff6-108">Requirements</span></span>  
 <span data-ttu-id="f3ff6-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3ff6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3ff6-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f3ff6-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3ff6-111">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f3ff6-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3ff6-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3ff6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3ff6-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3ff6-113">See also</span></span>

- [<span data-ttu-id="f3ff6-114">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="f3ff6-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f3ff6-115">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="f3ff6-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
