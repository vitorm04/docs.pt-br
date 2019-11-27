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
ms.openlocfilehash: 6ea7605e062eb77e0488b3a9561c4d83be16fa7d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436716"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="27406-102">Método IMetaDataImport::GetTypeRefProps</span><span class="sxs-lookup"><span data-stu-id="27406-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="27406-103">Obtém os metadados associados ao <xref:System.Type> referenciados pelo token TypeRef especificado.</span><span class="sxs-lookup"><span data-stu-id="27406-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27406-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27406-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27406-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="27406-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="27406-106">no O token TypeRef que representa o tipo para o qual retornar metadados.</span><span class="sxs-lookup"><span data-stu-id="27406-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="27406-107">fora Um ponteiro para o escopo no qual a referência é feita.</span><span class="sxs-lookup"><span data-stu-id="27406-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="27406-108">Esse valor é um token AssemblyRef ou ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="27406-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="27406-109">fora Um buffer que contém o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="27406-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="27406-110">no O tamanho solicitado em caracteres largos de `szName`.</span><span class="sxs-lookup"><span data-stu-id="27406-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="27406-111">fora O tamanho retornado em caracteres largos de `szName`.</span><span class="sxs-lookup"><span data-stu-id="27406-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27406-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="27406-112">Requirements</span></span>  
 <span data-ttu-id="27406-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27406-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27406-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="27406-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="27406-115">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="27406-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="27406-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27406-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27406-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27406-117">See also</span></span>

- [<span data-ttu-id="27406-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="27406-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="27406-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="27406-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
