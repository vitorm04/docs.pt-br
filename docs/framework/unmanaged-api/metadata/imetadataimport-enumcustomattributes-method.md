---
title: Método IMetaDataImport::EnumCustomAttributes
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c38b7f060c34f7408195484dec2c49305db422fe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781314"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="39838-102">Método IMetaDataImport::EnumCustomAttributes</span><span class="sxs-lookup"><span data-stu-id="39838-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="39838-103">Enumera os tokens de definição de atributo personalizado associados com o tipo especificado ou um membro.</span><span class="sxs-lookup"><span data-stu-id="39838-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39838-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39838-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes (   
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,   
   [in]  mdToken            tkType,   
   [out] mdCustomAttribute  rCustomAttributes[],   
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39838-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="39838-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="39838-106">[no, out] Um ponteiro para o enumerador retornado.</span><span class="sxs-lookup"><span data-stu-id="39838-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="39838-107">[in] Um token para o escopo da enumeração, ou zero para todos os atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="39838-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="39838-108">[in] Um token para o construtor do tipo dos atributos a serem enumerados, ou `null` para todos os tipos.</span><span class="sxs-lookup"><span data-stu-id="39838-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="39838-109">[out] Uma matriz de tokens de atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="39838-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="39838-110">[in] O tamanho máximo da `rCustomAttributes` matriz.</span><span class="sxs-lookup"><span data-stu-id="39838-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="39838-111">[out, opcional] O número real de valores do token retornado na `rCustomAttributes`.</span><span class="sxs-lookup"><span data-stu-id="39838-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39838-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="39838-112">Return Value</span></span>  
  
|<span data-ttu-id="39838-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="39838-113">HRESULT</span></span>|<span data-ttu-id="39838-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="39838-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="39838-115">`EnumCustomAttributes` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="39838-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="39838-116">Não há nenhum atributo personalizado para enumerar.</span><span class="sxs-lookup"><span data-stu-id="39838-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="39838-117">Nesse caso, `pcCustomAttributes` é zero.</span><span class="sxs-lookup"><span data-stu-id="39838-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="39838-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="39838-118">Requirements</span></span>  
 <span data-ttu-id="39838-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39838-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39838-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="39838-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="39838-121">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="39838-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="39838-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39838-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39838-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39838-123">See also</span></span>

- [<span data-ttu-id="39838-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="39838-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="39838-125">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="39838-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
