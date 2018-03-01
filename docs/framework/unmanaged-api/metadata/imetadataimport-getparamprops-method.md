---
title: "Método IMetaDataImport::GetParamProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f393ccd6296cb06498b30a29c7ea55f088e0a393
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="28663-102">Método IMetaDataImport::GetParamProps</span><span class="sxs-lookup"><span data-stu-id="28663-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="28663-103">Obtém os valores de metadados para o parâmetro referenciado pelo ParamDef especificado token.</span><span class="sxs-lookup"><span data-stu-id="28663-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28663-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28663-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="28663-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="28663-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="28663-106">[in] Um token de ParamDef que representa o parâmetro para retornar metadados.</span><span class="sxs-lookup"><span data-stu-id="28663-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="28663-107">[out] Um ponteiro para um token MethodDef que representa o método que utiliza o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="28663-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="28663-108">[out] A posição ordinal do parâmetro na lista de argumentos de método.</span><span class="sxs-lookup"><span data-stu-id="28663-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="28663-109">[out] Um buffer para armazenar o nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="28663-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="28663-110">[in] O tamanho solicitado em caracteres largos de `szName`.</span><span class="sxs-lookup"><span data-stu-id="28663-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="28663-111">[out] O tamanho retornado em caracteres largos de `szName`.</span><span class="sxs-lookup"><span data-stu-id="28663-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="28663-112">[out] Um ponteiro para os sinalizadores do atributo associado ao parâmetro.</span><span class="sxs-lookup"><span data-stu-id="28663-112">[out] A pointer to any attribute flags associated with the parameter.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="28663-113">[out] Um ponteiro para um sinalizador que especifica que o parâmetro é um <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="28663-113">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="28663-114">[out] Um ponteiro para uma cadeia de caracteres constante retornado pelo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="28663-114">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="28663-115">[out] O tamanho de `ppValue` em caracteres largos ou zero se `ppValue` não tem uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="28663-115">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28663-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="28663-116">Requirements</span></span>  
 <span data-ttu-id="28663-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28663-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28663-118">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="28663-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="28663-119">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="28663-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="28663-120">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28663-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28663-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28663-121">See Also</span></span>  
 [<span data-ttu-id="28663-122">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="28663-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="28663-123">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="28663-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
