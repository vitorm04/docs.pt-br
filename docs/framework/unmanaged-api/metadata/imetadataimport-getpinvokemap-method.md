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
ms.openlocfilehash: c458fef77b49f522ca21dd5487731f4d43588cea
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437103"
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="83732-102">Método IMetaDataImport::GetPinvokeMap</span><span class="sxs-lookup"><span data-stu-id="83732-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="83732-103">Obtém um token ModuleRef para representar o assembly de destino de uma chamada PInvoke.</span><span class="sxs-lookup"><span data-stu-id="83732-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83732-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83732-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83732-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="83732-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="83732-106">no Um token FieldDef ou MethodDef para obter os metadados de mapeamento do PInvoke.</span><span class="sxs-lookup"><span data-stu-id="83732-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="83732-107">fora Um ponteiro para sinalizadores usados para mapeamento.</span><span class="sxs-lookup"><span data-stu-id="83732-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="83732-108">Esse valor é um bitmask da enumeração [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="83732-108">This value is a bitmask from the [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="83732-109">fora O nome da DLL de destino não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="83732-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="83732-110">no O tamanho em caracteres largos de `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="83732-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="83732-111">fora O número de caracteres largos retornados em `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="83732-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="83732-112">fora Um ponteiro para um token de ModuleRef que representa a biblioteca de objetos de destino não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="83732-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83732-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="83732-113">Requirements</span></span>  
 <span data-ttu-id="83732-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83732-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83732-115">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="83732-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83732-116">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="83732-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="83732-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83732-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83732-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83732-118">See also</span></span>

- [<span data-ttu-id="83732-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="83732-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="83732-120">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="83732-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
