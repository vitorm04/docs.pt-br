---
title: Método IMetaDataEmit2::SaveDelta
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDelta
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDelta
helpviewer_keywords:
- IMetaDataEmit2::SaveDelta method [.NET Framework metadata]
- SaveDelta method [.NET Framework metadata]
ms.assetid: b95739fe-d2fa-4776-ae0d-31d9707ef799
topic_type:
- apiref
ms.openlocfilehash: afb0c09c09236267be2a999ce5c130feebb52b6f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447899"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="95cab-102">Método IMetaDataEmit2::SaveDelta</span><span class="sxs-lookup"><span data-stu-id="95cab-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="95cab-103">Salva as alterações da sessão de edição e continuação atual para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="95cab-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95cab-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95cab-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95cab-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="95cab-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="95cab-106">no O nome do arquivo sob o qual salvar as alterações.</span><span class="sxs-lookup"><span data-stu-id="95cab-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="95cab-107">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="95cab-107">[in] Reserved.</span></span> <span data-ttu-id="95cab-108">Deve ser zero.</span><span class="sxs-lookup"><span data-stu-id="95cab-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95cab-109">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="95cab-109">Requirements</span></span>  
 <span data-ttu-id="95cab-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95cab-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95cab-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="95cab-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="95cab-112">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="95cab-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="95cab-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95cab-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95cab-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95cab-114">See also</span></span>

- [<span data-ttu-id="95cab-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="95cab-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="95cab-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="95cab-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
