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
ms.openlocfilehash: 3c7c3525f2f8753241c9a206e4cf5e552bf06efe
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503613"
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="3a154-102">Método IMetaDataImport::GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="3a154-102">IMetaDataImport::GetMethodProps Method</span></span>
<span data-ttu-id="3a154-103">Obtém os metadados associados ao método referenciado pelo token MethodDef especificado.</span><span class="sxs-lookup"><span data-stu-id="3a154-103">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a154-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a154-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3a154-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3a154-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="3a154-106">no O token MethodDef que representa o método para o qual retornar metadados.</span><span class="sxs-lookup"><span data-stu-id="3a154-106">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="3a154-107">fora Um ponteiro para um token de TypeDef que representa o tipo que implementa o método.</span><span class="sxs-lookup"><span data-stu-id="3a154-107">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="3a154-108">fora Um ponteiro para um buffer que tem o nome do método.</span><span class="sxs-lookup"><span data-stu-id="3a154-108">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="3a154-109">no O tamanho solicitado de `szMethod` .</span><span class="sxs-lookup"><span data-stu-id="3a154-109">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="3a154-110">fora Um ponteiro para o tamanho em caracteres largos de `szMethod` , ou no caso de truncamento, o número real de caracteres largos no nome do método.</span><span class="sxs-lookup"><span data-stu-id="3a154-110">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="3a154-111">fora Um ponteiro para todos os sinalizadores associados ao método.</span><span class="sxs-lookup"><span data-stu-id="3a154-111">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="3a154-112">fora Um ponteiro para a assinatura de metadados binários do método.</span><span class="sxs-lookup"><span data-stu-id="3a154-112">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="3a154-113">fora Um ponteiro para o tamanho em bytes de `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="3a154-113">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="3a154-114">fora Um ponteiro para o endereço virtual relativo do método.</span><span class="sxs-lookup"><span data-stu-id="3a154-114">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="3a154-115">fora Um ponteiro para qualquer sinalizador de implementação para o método.</span><span class="sxs-lookup"><span data-stu-id="3a154-115">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a154-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a154-116">Requirements</span></span>  
 <span data-ttu-id="3a154-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a154-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a154-118">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3a154-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3a154-119">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3a154-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3a154-120">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a154-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a154-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="3a154-121">See also</span></span>

- [<span data-ttu-id="3a154-122">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="3a154-122">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3a154-123">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="3a154-123">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
