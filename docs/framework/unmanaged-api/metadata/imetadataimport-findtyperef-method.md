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
ms.openlocfilehash: 545fe1e1d9e641d2225ad92c11453558dc4b97d1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491492"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="5034a-102">Método IMetaDataImport::FindTypeRef</span><span class="sxs-lookup"><span data-stu-id="5034a-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="5034a-103">Obtém um ponteiro para o token TypeRef para a <xref:System.Type> referência que está no escopo especificado e que tem o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="5034a-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5034a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5034a-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5034a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5034a-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="5034a-106">no Um token ModuleRef, AssemblyRef ou TypeRef que especifica o módulo, o assembly ou o tipo, respectivamente, no qual a referência de tipo é definida.</span><span class="sxs-lookup"><span data-stu-id="5034a-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="5034a-107">no O nome da referência de tipo a ser pesquisada.</span><span class="sxs-lookup"><span data-stu-id="5034a-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="5034a-108">fora Um ponteiro para o token TypeRef correspondente.</span><span class="sxs-lookup"><span data-stu-id="5034a-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5034a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5034a-109">Requirements</span></span>  
 <span data-ttu-id="5034a-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5034a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5034a-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5034a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5034a-112">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5034a-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5034a-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5034a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5034a-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="5034a-114">See also</span></span>

- [<span data-ttu-id="5034a-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="5034a-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="5034a-116">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="5034a-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
