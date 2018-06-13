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
ms.openlocfilehash: 1c77f946b14fcb5ddc786488ab42e37eb868fbc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448273"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="05c80-102">Método IMetaDataImport::GetNestedClassProps</span><span class="sxs-lookup"><span data-stu-id="05c80-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="05c80-103">Obtém o token do TypeDef pai <xref:System.Type> do tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="05c80-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05c80-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="05c80-104">Syntax</span></span>  
  
```  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05c80-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="05c80-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="05c80-106">[in] Um token de TypeDef representando o <xref:System.Type> para retornar a classe pai token para.</span><span class="sxs-lookup"><span data-stu-id="05c80-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="05c80-107">[out] Um ponteiro para o token de TypeDef para a <xref:System.Type> que `tdNestedClass` é aninhado em.</span><span class="sxs-lookup"><span data-stu-id="05c80-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05c80-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="05c80-108">Requirements</span></span>  
 <span data-ttu-id="05c80-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05c80-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05c80-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="05c80-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05c80-111">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="05c80-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05c80-112">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05c80-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05c80-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05c80-113">See Also</span></span>  
 [<span data-ttu-id="05c80-114">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="05c80-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="05c80-115">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="05c80-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
