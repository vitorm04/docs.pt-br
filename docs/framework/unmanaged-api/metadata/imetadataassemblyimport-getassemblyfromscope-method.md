---
title: Método IMetaDataAssemblyImport::GetAssemblyFromScope
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope method [.NET Framework metadata]
- GetAssemblyFromScope method [.NET Framework metadata]
ms.assetid: 0b437f70-561d-48c7-abe0-0cb9ace10c08
topic_type:
- apiref
ms.openlocfilehash: adcaac02526c7d72ffb75ba6c7552632173032cf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009035"
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="f12c1-102">Método IMetaDataAssemblyImport::GetAssemblyFromScope</span><span class="sxs-lookup"><span data-stu-id="f12c1-102">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>
<span data-ttu-id="f12c1-103">Obtém um ponteiro para o assembly no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="f12c1-103">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f12c1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f12c1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f12c1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f12c1-105">Parameters</span></span>  
 `ptkAssembly`  
 <span data-ttu-id="f12c1-106">fora Um ponteiro para o `mdAssembly` token recuperado que identifica o assembly.</span><span class="sxs-lookup"><span data-stu-id="f12c1-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f12c1-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f12c1-107">Requirements</span></span>  
 <span data-ttu-id="f12c1-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f12c1-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f12c1-109">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f12c1-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f12c1-110">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f12c1-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f12c1-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f12c1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f12c1-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="f12c1-112">See also</span></span>

- [<span data-ttu-id="f12c1-113">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="f12c1-113">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
