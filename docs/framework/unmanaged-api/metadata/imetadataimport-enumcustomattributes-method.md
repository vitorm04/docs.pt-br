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
ms.openlocfilehash: a43c1883038e41cac1b58c78bc26f20d436ebbd1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440243"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="75142-102">Método IMetaDataImport::EnumCustomAttributes</span><span class="sxs-lookup"><span data-stu-id="75142-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="75142-103">Enumera os tokens de definição de atributo personalizados associados ao tipo ou membro especificado.</span><span class="sxs-lookup"><span data-stu-id="75142-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75142-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="75142-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="75142-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75142-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="75142-106">[entrada, saída] Um ponteiro para o enumerador retornado.</span><span class="sxs-lookup"><span data-stu-id="75142-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="75142-107">no Um token para o escopo da enumeração ou zero para todos os atributos personalizados.</span><span class="sxs-lookup"><span data-stu-id="75142-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="75142-108">no Um token para o construtor do tipo dos atributos a serem enumerados ou `null` para todos os tipos.</span><span class="sxs-lookup"><span data-stu-id="75142-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="75142-109">fora Uma matriz de tokens de atributo personalizados.</span><span class="sxs-lookup"><span data-stu-id="75142-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="75142-110">no O tamanho máximo da matriz de `rCustomAttributes`.</span><span class="sxs-lookup"><span data-stu-id="75142-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="75142-111">[saída, opcional] O número real de valores de token retornados em `rCustomAttributes`.</span><span class="sxs-lookup"><span data-stu-id="75142-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75142-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="75142-112">Return Value</span></span>  
  
|<span data-ttu-id="75142-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="75142-113">HRESULT</span></span>|<span data-ttu-id="75142-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="75142-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="75142-115">`EnumCustomAttributes` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="75142-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="75142-116">Não há atributos personalizados para enumerar.</span><span class="sxs-lookup"><span data-stu-id="75142-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="75142-117">Nesse caso, `pcCustomAttributes` é zero.</span><span class="sxs-lookup"><span data-stu-id="75142-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="75142-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="75142-118">Requirements</span></span>  
 <span data-ttu-id="75142-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75142-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75142-120">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="75142-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75142-121">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="75142-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="75142-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75142-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75142-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75142-123">See also</span></span>

- [<span data-ttu-id="75142-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="75142-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="75142-125">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="75142-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
