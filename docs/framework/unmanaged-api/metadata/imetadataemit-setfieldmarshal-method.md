---
title: Método IMetaDataEmit::SetFieldMarshal
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a55a8575a3f8ae04bcc4a148b588cd2361f81cf6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751502"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="f6865-102">Método IMetaDataEmit::SetFieldMarshal</span><span class="sxs-lookup"><span data-stu-id="f6865-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="f6865-103">Define a informações de marshaling para o parâmetro de método, retorno de método ou campo referenciada pelo token especificado de PInvoke.</span><span class="sxs-lookup"><span data-stu-id="f6865-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6865-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6865-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,   
    [in]  PCCOR_SIGNATURE  pvNativeType,   
    [in]  ULONG            cbNativeType   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6865-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f6865-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="f6865-106">[in] O token para o item de dados de destino.</span><span class="sxs-lookup"><span data-stu-id="f6865-106">[in] The token for target data item.</span></span> <span data-ttu-id="f6865-107">Isso é um `mdFieldDef` ou um `mdParamDef` token.</span><span class="sxs-lookup"><span data-stu-id="f6865-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="f6865-108">[in] A assinatura para o tipo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f6865-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="f6865-109">[in] A contagem de bytes em `pvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="f6865-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6865-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f6865-110">Requirements</span></span>  
 <span data-ttu-id="f6865-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6865-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6865-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f6865-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f6865-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f6865-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6865-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6865-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6865-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6865-115">See also</span></span>

- [<span data-ttu-id="f6865-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f6865-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f6865-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="f6865-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
