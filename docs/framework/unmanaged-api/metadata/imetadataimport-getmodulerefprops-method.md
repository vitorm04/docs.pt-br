---
title: Método IMetaDataImport::GetModuleRefProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type:
- apiref
ms.openlocfilehash: f46033b9e643ef6b4a0063c4995b8c024b8c1f7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175350"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="4748c-102">Método IMetaDataImport::GetModuleRefProps</span><span class="sxs-lookup"><span data-stu-id="4748c-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="4748c-103">Obtém o nome do módulo referenciado pelo token de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="4748c-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4748c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4748c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,
   [in]  ULONG               cchName,
   [out] ULONG               *pchName
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4748c-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="4748c-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="4748c-106">[em] O token de metadados ModuleRef que faz referência ao módulo para obter informações de metadados.</span><span class="sxs-lookup"><span data-stu-id="4748c-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="4748c-107">[fora] Um buffer para segurar o nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="4748c-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="4748c-108">[em] O tamanho solicitado `szName` de em caracteres largos.</span><span class="sxs-lookup"><span data-stu-id="4748c-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="4748c-109">[fora] O tamanho devolvido `szName` de em caracteres largos.</span><span class="sxs-lookup"><span data-stu-id="4748c-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4748c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4748c-110">Requirements</span></span>  
 <span data-ttu-id="4748c-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4748c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4748c-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4748c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4748c-113">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4748c-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4748c-114">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4748c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4748c-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="4748c-115">See also</span></span>

- [<span data-ttu-id="4748c-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="4748c-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4748c-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="4748c-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
