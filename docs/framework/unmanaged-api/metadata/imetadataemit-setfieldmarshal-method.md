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
ms.openlocfilehash: cdbcdb9359d295ad9bed2050ed36499feba74d9e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442278"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="8ce92-102">Método IMetaDataEmit::SetFieldMarshal</span><span class="sxs-lookup"><span data-stu-id="8ce92-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="8ce92-103">Define as informações de marshaling do PInvoke para o campo, o retorno do método ou o parâmetro do método referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="8ce92-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ce92-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ce92-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,   
    [in]  PCCOR_SIGNATURE  pvNativeType,   
    [in]  ULONG            cbNativeType   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ce92-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8ce92-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="8ce92-106">no O token para o item de dados de destino.</span><span class="sxs-lookup"><span data-stu-id="8ce92-106">[in] The token for target data item.</span></span> <span data-ttu-id="8ce92-107">Este é um `mdFieldDef` ou um token de `mdParamDef`.</span><span class="sxs-lookup"><span data-stu-id="8ce92-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="8ce92-108">no A assinatura para o tipo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8ce92-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="8ce92-109">no A contagem de bytes em `pvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="8ce92-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ce92-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8ce92-110">Requirements</span></span>  
 <span data-ttu-id="8ce92-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ce92-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ce92-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8ce92-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8ce92-113">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8ce92-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ce92-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ce92-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ce92-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ce92-115">See also</span></span>

- [<span data-ttu-id="8ce92-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="8ce92-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="8ce92-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="8ce92-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
