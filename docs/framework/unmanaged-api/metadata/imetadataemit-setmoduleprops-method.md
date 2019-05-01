---
title: Método IMetaDataEmit::SetModuleProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetModuleProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 651659a48ba9950cdd837889c4491c66fe40b507
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042960"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="1d56a-102">Método IMetaDataEmit::SetModuleProps</span><span class="sxs-lookup"><span data-stu-id="1d56a-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="1d56a-103">Atualiza as referências a um módulo definido por uma chamada anterior ao [imetadataemit:: Definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="1d56a-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d56a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d56a-104">Syntax</span></span>  
  
```  
HRESULT SetModuleProps (   
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d56a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1d56a-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="1d56a-106">[in] O nome do módulo em Unicode.</span><span class="sxs-lookup"><span data-stu-id="1d56a-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="1d56a-107">Isso é apenas o nome do arquivo e não o nome de caminho completo.</span><span class="sxs-lookup"><span data-stu-id="1d56a-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d56a-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1d56a-108">Requirements</span></span>  
 <span data-ttu-id="1d56a-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d56a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d56a-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1d56a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1d56a-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="1d56a-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d56a-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d56a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d56a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d56a-113">See also</span></span>

- [<span data-ttu-id="1d56a-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="1d56a-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="1d56a-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="1d56a-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
