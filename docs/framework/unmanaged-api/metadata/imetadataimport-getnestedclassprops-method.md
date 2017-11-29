---
title: "Método IMetaDataImport::GetNestedClassProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetNestedClassProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetNestedClassProps
helpviewer_keywords:
- GetNestedClassProps method [.NET Framework metadata]
- IMetaDataImport::GetNestedClassProps method [.NET Framework metadata]
ms.assetid: 704d19f1-bdef-4745-af8c-6476eb246fb3
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8a538cea5267b32790a9c656df9584d5ea31f54c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="87c48-102">Método IMetaDataImport::GetNestedClassProps</span><span class="sxs-lookup"><span data-stu-id="87c48-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="87c48-103">Obtém o token do TypeDef pai <xref:System.Type> do tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="87c48-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87c48-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87c48-104">Syntax</span></span>  
  
```  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87c48-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="87c48-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="87c48-106">[in] Um token de TypeDef representando o <xref:System.Type> para retornar a classe pai token para.</span><span class="sxs-lookup"><span data-stu-id="87c48-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="87c48-107">[out] Um ponteiro para o token de TypeDef para a <xref:System.Type> que `tdNestedClass` é aninhado em.</span><span class="sxs-lookup"><span data-stu-id="87c48-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87c48-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="87c48-108">Requirements</span></span>  
 <span data-ttu-id="87c48-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87c48-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87c48-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="87c48-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="87c48-111">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="87c48-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="87c48-112">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87c48-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87c48-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87c48-113">See Also</span></span>  
 [<span data-ttu-id="87c48-114">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="87c48-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="87c48-115">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="87c48-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
