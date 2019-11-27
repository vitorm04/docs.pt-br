---
title: Método IMetaDataImport::GetMethodProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
ms.openlocfilehash: 4a258ce9121a287929ca5bc39c480f1ca2596e78
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437467"
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="81391-102">Método IMetaDataImport::GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="81391-102">IMetaDataImport::GetMethodProps Method</span></span>
<span data-ttu-id="81391-103">Obtém os metadados associados ao método referenciado pelo token MethodDef especificado.</span><span class="sxs-lookup"><span data-stu-id="81391-103">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81391-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81391-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81391-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="81391-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="81391-106">no O token MethodDef que representa o método para o qual retornar metadados.</span><span class="sxs-lookup"><span data-stu-id="81391-106">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="81391-107">fora Um ponteiro para um token de TypeDef que representa o tipo que implementa o método.</span><span class="sxs-lookup"><span data-stu-id="81391-107">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="81391-108">fora Um ponteiro para um buffer que tem o nome do método.</span><span class="sxs-lookup"><span data-stu-id="81391-108">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="81391-109">no O tamanho solicitado de `szMethod`.</span><span class="sxs-lookup"><span data-stu-id="81391-109">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="81391-110">fora Um ponteiro para o tamanho em caracteres largos de `szMethod`ou, no caso de truncamento, o número real de caracteres largos no nome do método.</span><span class="sxs-lookup"><span data-stu-id="81391-110">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="81391-111">fora Um ponteiro para todos os sinalizadores associados ao método.</span><span class="sxs-lookup"><span data-stu-id="81391-111">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="81391-112">fora Um ponteiro para a assinatura de metadados binários do método.</span><span class="sxs-lookup"><span data-stu-id="81391-112">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="81391-113">fora Um ponteiro para o tamanho em bytes de `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="81391-113">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="81391-114">fora Um ponteiro para o endereço virtual relativo do método.</span><span class="sxs-lookup"><span data-stu-id="81391-114">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="81391-115">fora Um ponteiro para qualquer sinalizador de implementação para o método.</span><span class="sxs-lookup"><span data-stu-id="81391-115">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81391-116">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="81391-116">Requirements</span></span>  
 <span data-ttu-id="81391-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81391-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81391-118">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="81391-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="81391-119">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="81391-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="81391-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81391-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81391-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81391-121">See also</span></span>

- [<span data-ttu-id="81391-122">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="81391-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="81391-123">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="81391-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
