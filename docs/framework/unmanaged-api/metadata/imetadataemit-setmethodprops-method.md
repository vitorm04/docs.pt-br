---
title: Método IMetaDataEmit::SetMethodProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodProps
helpviewer_keywords:
- SetMethodProps method [.NET Framework metadata]
- IMetaDataEmit::SetMethodProps method [.NET Framework metadata]
ms.assetid: e0c6ac12-22ea-43f5-b799-8cda0faf3336
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 534afdd5990435c6b4db5ef8ea27a8065b199496
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183593"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="3157e-102">Método IMetaDataEmit::SetMethodProps</span><span class="sxs-lookup"><span data-stu-id="3157e-102">IMetaDataEmit::SetMethodProps Method</span></span>
<span data-ttu-id="3157e-103">Define ou atualiza o recurso, armazenado do endereço virtual relativo especificado, de um método definido por uma chamada anterior a [imetadataemit:: Definemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="3157e-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3157e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3157e-104">Syntax</span></span>  
  
```  
HRESULT SetMethodProps (   
    [in]  mdMethodDef md,   
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,   
    [in]  DWORD       dwImplFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3157e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3157e-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="3157e-106">[in] O token para o método a ser alterado.</span><span class="sxs-lookup"><span data-stu-id="3157e-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="3157e-107">[in] Os atributos de membro.</span><span class="sxs-lookup"><span data-stu-id="3157e-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="3157e-108">[in] O endereço do código.</span><span class="sxs-lookup"><span data-stu-id="3157e-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="3157e-109">[in] Os sinalizadores de implementação para o método.</span><span class="sxs-lookup"><span data-stu-id="3157e-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3157e-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3157e-110">Requirements</span></span>  
 <span data-ttu-id="3157e-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3157e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3157e-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3157e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3157e-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3157e-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="3157e-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="3157e-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3157e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3157e-115">See also</span></span>

- [<span data-ttu-id="3157e-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="3157e-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3157e-117">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="3157e-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
