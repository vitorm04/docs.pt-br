---
title: Método IMetaDataImport::GetPinvokeMap
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2aed3367e20e32a387c8a1c58ead2899fbf0dcb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521433"
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="08db6-102">Método IMetaDataImport::GetPinvokeMap</span><span class="sxs-lookup"><span data-stu-id="08db6-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="08db6-103">Obtém um ModuleRef token para representar o assembly de destino de uma chamada de PInvoke.</span><span class="sxs-lookup"><span data-stu-id="08db6-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08db6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08db6-104">Syntax</span></span>  
  
```  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08db6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="08db6-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="08db6-106">[in] Um token para obter os metadados de mapeamento de PInvoke para FieldDef ou MethodDef.</span><span class="sxs-lookup"><span data-stu-id="08db6-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="08db6-107">[out] Um ponteiro para os sinalizadores usados para mapeamento.</span><span class="sxs-lookup"><span data-stu-id="08db6-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="08db6-108">Esse valor é um bitmask do [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="08db6-108">This value is a bitmask from the [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="08db6-109">[out] O nome da DLL de destino não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="08db6-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="08db6-110">[in] O tamanho em caracteres largos da `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="08db6-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="08db6-111">[out] O número de caracteres largos retornado no `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="08db6-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="08db6-112">[out] Um ponteiro para um token de ModuleRef que representa a biblioteca de objeto de destino não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="08db6-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08db6-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="08db6-113">Requirements</span></span>  
 <span data-ttu-id="08db6-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08db6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08db6-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="08db6-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08db6-116">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="08db6-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="08db6-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08db6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08db6-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08db6-118">See also</span></span>
- [<span data-ttu-id="08db6-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="08db6-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="08db6-120">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="08db6-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
