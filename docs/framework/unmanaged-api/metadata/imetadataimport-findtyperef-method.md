---
title: Método IMetaDataImport::FindTypeRef
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type:
- apiref
ms.openlocfilehash: 21a69d120cc732ca6659f77abc9f8ea0c993271e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437791"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="87ef5-102">Método IMetaDataImport::FindTypeRef</span><span class="sxs-lookup"><span data-stu-id="87ef5-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="87ef5-103">Obtém um ponteiro para o token TypeRef para a referência de <xref:System.Type> que está no escopo especificado e que tem o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="87ef5-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87ef5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87ef5-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87ef5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="87ef5-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="87ef5-106">no Um token ModuleRef, AssemblyRef ou TypeRef que especifica o módulo, o assembly ou o tipo, respectivamente, no qual a referência de tipo é definida.</span><span class="sxs-lookup"><span data-stu-id="87ef5-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="87ef5-107">no O nome da referência de tipo a ser pesquisada.</span><span class="sxs-lookup"><span data-stu-id="87ef5-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="87ef5-108">fora Um ponteiro para o token TypeRef correspondente.</span><span class="sxs-lookup"><span data-stu-id="87ef5-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87ef5-109">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="87ef5-109">Requirements</span></span>  
 <span data-ttu-id="87ef5-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87ef5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87ef5-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="87ef5-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="87ef5-112">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="87ef5-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="87ef5-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87ef5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87ef5-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87ef5-114">See also</span></span>

- [<span data-ttu-id="87ef5-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="87ef5-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="87ef5-116">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="87ef5-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
