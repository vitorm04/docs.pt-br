---
title: Método IMetaDataImport::GetTypeRefProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 25482ee81d5210e5ab69007767aecf01435602d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448590"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="18243-102">Método IMetaDataImport::GetTypeRefProps</span><span class="sxs-lookup"><span data-stu-id="18243-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="18243-103">Obtém os metadados associados a <xref:System.Type> referenciada pelo token de TypeRef especificado.</span><span class="sxs-lookup"><span data-stu-id="18243-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18243-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="18243-104">Syntax</span></span>  
  
```  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="18243-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="18243-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="18243-106">[in] O token TypeRef que representa o tipo para retornar metadados.</span><span class="sxs-lookup"><span data-stu-id="18243-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="18243-107">[out] Um ponteiro para o escopo no qual a referência é feita.</span><span class="sxs-lookup"><span data-stu-id="18243-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="18243-108">Esse valor é um token AssemblyRef ou ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="18243-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="18243-109">[out] Um buffer que contém o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="18243-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="18243-110">[in] O tamanho solicitado em caracteres largos de `szName`.</span><span class="sxs-lookup"><span data-stu-id="18243-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="18243-111">[out] O tamanho retornado em caracteres largos de `szName`.</span><span class="sxs-lookup"><span data-stu-id="18243-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18243-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="18243-112">Requirements</span></span>  
 <span data-ttu-id="18243-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18243-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18243-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="18243-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="18243-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="18243-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="18243-116">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18243-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18243-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18243-117">See Also</span></span>  
 [<span data-ttu-id="18243-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="18243-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="18243-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="18243-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
