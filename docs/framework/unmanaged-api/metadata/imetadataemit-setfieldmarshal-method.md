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
ms.openlocfilehash: 82675af85f049aeb288b3dcc18f222c0387a37b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050097"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="c7366-102">Método IMetaDataEmit::SetFieldMarshal</span><span class="sxs-lookup"><span data-stu-id="c7366-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="c7366-103">Define a informações de marshaling para o parâmetro de método, retorno de método ou campo referenciada pelo token especificado de PInvoke.</span><span class="sxs-lookup"><span data-stu-id="c7366-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7366-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7366-104">Syntax</span></span>  
  
```  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,   
    [in]  PCCOR_SIGNATURE  pvNativeType,   
    [in]  ULONG            cbNativeType   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7366-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c7366-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="c7366-106">[in] O token para o item de dados de destino.</span><span class="sxs-lookup"><span data-stu-id="c7366-106">[in] The token for target data item.</span></span> <span data-ttu-id="c7366-107">Isso é um `mdFieldDef` ou um `mdParamDef` token.</span><span class="sxs-lookup"><span data-stu-id="c7366-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="c7366-108">[in] A assinatura para o tipo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="c7366-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="c7366-109">[in] A contagem de bytes em `pvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="c7366-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7366-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c7366-110">Requirements</span></span>  
 <span data-ttu-id="c7366-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7366-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7366-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c7366-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7366-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c7366-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7366-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7366-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7366-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7366-115">See also</span></span>

- [<span data-ttu-id="c7366-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="c7366-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c7366-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="c7366-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
