---
title: Método IMetaDataEmit::SaveToStream
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
ms.openlocfilehash: 23f6186b2561cbcd52db767616d986084f33860b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435936"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="ea698-102">Método IMetaDataEmit::SaveToStream</span><span class="sxs-lookup"><span data-stu-id="ea698-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="ea698-103">Salva todos os metadados no escopo atual para o `IStream`especificado.</span><span class="sxs-lookup"><span data-stu-id="ea698-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea698-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea698-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea698-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ea698-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="ea698-106">no O fluxo gravável no qual salvar.</span><span class="sxs-lookup"><span data-stu-id="ea698-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="ea698-107">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="ea698-107">[in] Reserved.</span></span> <span data-ttu-id="ea698-108">Deve ser zero.</span><span class="sxs-lookup"><span data-stu-id="ea698-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea698-109">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="ea698-109">Requirements</span></span>  
 <span data-ttu-id="ea698-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea698-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea698-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ea698-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ea698-112">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ea698-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea698-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea698-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea698-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea698-114">See also</span></span>

- [<span data-ttu-id="ea698-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="ea698-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ea698-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="ea698-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
