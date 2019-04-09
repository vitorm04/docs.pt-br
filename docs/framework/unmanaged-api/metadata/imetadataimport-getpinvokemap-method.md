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
ms.openlocfilehash: 99aea385cf5e3c8bcf7cf39b7cc5618f99f8a631
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121700"
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="4d914-102">Método IMetaDataImport::GetPinvokeMap</span><span class="sxs-lookup"><span data-stu-id="4d914-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="4d914-103">Obtém um ModuleRef token para representar o assembly de destino de uma chamada de PInvoke.</span><span class="sxs-lookup"><span data-stu-id="4d914-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d914-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4d914-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4d914-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4d914-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="4d914-106">[in] Um token para obter os metadados de mapeamento de PInvoke para FieldDef ou MethodDef.</span><span class="sxs-lookup"><span data-stu-id="4d914-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="4d914-107">[out] Um ponteiro para os sinalizadores usados para mapeamento.</span><span class="sxs-lookup"><span data-stu-id="4d914-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="4d914-108">Esse valor é um bitmask do [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="4d914-108">This value is a bitmask from the [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="4d914-109">[out] O nome da DLL de destino não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="4d914-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="4d914-110">[in] O tamanho em caracteres largos da `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="4d914-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="4d914-111">[out] O número de caracteres largos retornado no `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="4d914-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="4d914-112">[out] Um ponteiro para um token de ModuleRef que representa a biblioteca de objeto de destino não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="4d914-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d914-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4d914-113">Requirements</span></span>  
 <span data-ttu-id="4d914-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d914-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d914-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4d914-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4d914-116">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="4d914-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="4d914-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="4d914-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4d914-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d914-118">See also</span></span>

- [<span data-ttu-id="4d914-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="4d914-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4d914-120">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="4d914-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
