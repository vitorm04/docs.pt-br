---
title: Método IMetaDataImport::GetParamProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9d2c74adecdfb0201f9f0c08998feba674f9e0f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778929"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="53c6a-102">Método IMetaDataImport::GetParamProps</span><span class="sxs-lookup"><span data-stu-id="53c6a-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="53c6a-103">Obtém os valores de metadados para o parâmetro referenciado pelo ParamDef especificado token.</span><span class="sxs-lookup"><span data-stu-id="53c6a-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53c6a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53c6a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53c6a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="53c6a-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="53c6a-106">[in] Um token de ParamDef que representa o parâmetro para retornar metadados.</span><span class="sxs-lookup"><span data-stu-id="53c6a-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="53c6a-107">[out] Um ponteiro para um token MethodDef que representa o método que utiliza o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="53c6a-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="53c6a-108">[out] A posição ordinal do parâmetro na lista de argumentos de método.</span><span class="sxs-lookup"><span data-stu-id="53c6a-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="53c6a-109">[out] Um buffer para armazenar o nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="53c6a-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="53c6a-110">[in] O tamanho solicitado em caracteres largos da `szName`.</span><span class="sxs-lookup"><span data-stu-id="53c6a-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="53c6a-111">[out] O tamanho retornado em caracteres largos da `szName`.</span><span class="sxs-lookup"><span data-stu-id="53c6a-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="53c6a-112">[out] Um ponteiro para os sinalizadores de atributo associado ao parâmetro.</span><span class="sxs-lookup"><span data-stu-id="53c6a-112">[out] A pointer to any attribute flags associated with the parameter.</span></span> <span data-ttu-id="53c6a-113">Esse é um bitmask de `CorParamAttr` valores.</span><span class="sxs-lookup"><span data-stu-id="53c6a-113">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="53c6a-114">[out] Um ponteiro para um sinalizador que especifica que o parâmetro é um <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="53c6a-114">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="53c6a-115">[out] Um ponteiro para uma cadeia de caracteres constante retornado pelo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="53c6a-115">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="53c6a-116">[out] O tamanho de `ppValue` em caracteres largos ou zero se `ppValue` não mantém uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="53c6a-116">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53c6a-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="53c6a-117">Remarks</span></span>

<span data-ttu-id="53c6a-118">Os valores de sequência no `pulSequence` começam com 1 para parâmetros.</span><span class="sxs-lookup"><span data-stu-id="53c6a-118">The sequence values in `pulSequence` begin with 1 for parameters.</span></span> <span data-ttu-id="53c6a-119">Um valor de retorno tem um número de sequência igual a 0.</span><span class="sxs-lookup"><span data-stu-id="53c6a-119">A return value has a sequence number of 0.</span></span>

## <a name="requirements"></a><span data-ttu-id="53c6a-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="53c6a-120">Requirements</span></span>  
 <span data-ttu-id="53c6a-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53c6a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53c6a-122">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="53c6a-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="53c6a-123">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="53c6a-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="53c6a-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53c6a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53c6a-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53c6a-125">See also</span></span>

- [<span data-ttu-id="53c6a-126">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="53c6a-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="53c6a-127">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="53c6a-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
