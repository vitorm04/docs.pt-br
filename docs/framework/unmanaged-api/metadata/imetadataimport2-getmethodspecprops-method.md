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
ms.openlocfilehash: 6b5b3b3b5a3613668f4470f48083ae010cc9d336
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445247"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="9c19c-102">Método IMetaDataImport2::GetMethodSpecProps</span><span class="sxs-lookup"><span data-stu-id="9c19c-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="9c19c-103">Obtém a assinatura de metadados do método referenciado pelo token de MethodSpec especificado.</span><span class="sxs-lookup"><span data-stu-id="9c19c-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c19c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c19c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,   
   [out] ULONG            *pcbSigBlob  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="9c19c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9c19c-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="9c19c-106">no Um token de MethodSpec que representa a instanciação do método.</span><span class="sxs-lookup"><span data-stu-id="9c19c-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="9c19c-107">fora Um ponteiro para o token MethodDef ou MethodRef que representa a definição do método.</span><span class="sxs-lookup"><span data-stu-id="9c19c-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="9c19c-108">fora Um ponteiro para a assinatura de metadados binários do método.</span><span class="sxs-lookup"><span data-stu-id="9c19c-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="9c19c-109">fora O tamanho, em bytes, de `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="9c19c-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c19c-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9c19c-110">Requirements</span></span>  
 <span data-ttu-id="9c19c-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c19c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c19c-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9c19c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c19c-113">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9c19c-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c19c-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c19c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c19c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c19c-115">See also</span></span>

- [<span data-ttu-id="9c19c-116">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="9c19c-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="9c19c-117">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="9c19c-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
