---
title: "Método IMetaDataImport::GetPinvokeMap"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetPinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a28d628040a35d309515703563239a5f802dc4a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="a95bb-102">Método IMetaDataImport::GetPinvokeMap</span><span class="sxs-lookup"><span data-stu-id="a95bb-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="a95bb-103">Obtém um ModuleRef token para representar o assembly de destino de uma chamada de PInvoke.</span><span class="sxs-lookup"><span data-stu-id="a95bb-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a95bb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a95bb-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="a95bb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a95bb-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a95bb-106">[in] Um token para obter os metadados de mapeamento de PInvoke para FieldDef ou MethodDef.</span><span class="sxs-lookup"><span data-stu-id="a95bb-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="a95bb-107">[out] Um ponteiro para sinalizadores usados para mapeamento.</span><span class="sxs-lookup"><span data-stu-id="a95bb-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="a95bb-108">Esse valor é um bitmask do [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="a95bb-108">This value is a bitmask from the [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="a95bb-109">[out] O nome do DLL não gerenciada de destino.</span><span class="sxs-lookup"><span data-stu-id="a95bb-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="a95bb-110">[in] O tamanho em caracteres largos de `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="a95bb-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="a95bb-111">[out] O número de caracteres largos retornados em `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="a95bb-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="a95bb-112">[out] Um ponteiro para um token de ModuleRef que representa a biblioteca de objeto de destino não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="a95bb-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a95bb-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a95bb-113">Requirements</span></span>  
 <span data-ttu-id="a95bb-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a95bb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a95bb-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a95bb-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a95bb-116">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a95bb-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a95bb-117">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a95bb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a95bb-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a95bb-118">See Also</span></span>  
 [<span data-ttu-id="a95bb-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="a95bb-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a95bb-120">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="a95bb-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
