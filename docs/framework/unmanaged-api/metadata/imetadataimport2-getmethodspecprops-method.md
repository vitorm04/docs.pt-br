---
title: Método IMetaDataImport2::GetMethodSpecProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetMethodSpecProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetMethodSpecProps
helpviewer_keywords:
- GetMethodSpecProps method [.NET Framework metadata]
- IMetaDataImport2::GetMethodSpecProps method [.NET Framework metadata]
ms.assetid: 9544b711-e669-4eaf-8630-ee862e5e4489
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c35212e7d261a5b385823fdaa345f6fbd638571c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079338"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="5d969-102">Método IMetaDataImport2::GetMethodSpecProps</span><span class="sxs-lookup"><span data-stu-id="5d969-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="5d969-103">Obtém o token de assinatura de metadados do método referenciado pelo MethodSpec especificado.</span><span class="sxs-lookup"><span data-stu-id="5d969-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d969-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d969-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,   
   [out] ULONG            *pcbSigBlob  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="5d969-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5d969-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="5d969-106">[in] Um token MethodSpec que representa a instanciação do método.</span><span class="sxs-lookup"><span data-stu-id="5d969-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="5d969-107">[out] Um ponteiro para o token MethodDef ou MethodRef que representa a definição de método.</span><span class="sxs-lookup"><span data-stu-id="5d969-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="5d969-108">[out] Um ponteiro para a assinatura de metadados de binários do método.</span><span class="sxs-lookup"><span data-stu-id="5d969-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="5d969-109">[out] O tamanho, em bytes, do `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="5d969-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d969-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d969-110">Requirements</span></span>  
 <span data-ttu-id="5d969-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d969-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d969-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5d969-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5d969-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5d969-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="5d969-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="5d969-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5d969-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d969-115">See also</span></span>

- [<span data-ttu-id="5d969-116">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="5d969-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="5d969-117">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="5d969-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
