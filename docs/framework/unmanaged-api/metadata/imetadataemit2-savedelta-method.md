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
ms.openlocfilehash: 0ebcab7a759b64bfbb254df1c1aa339cde77d054
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175558"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="ab1fd-102">Método IMetaDataEmit2::SaveDelta</span><span class="sxs-lookup"><span data-stu-id="ab1fd-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="ab1fd-103">Salva alterações da sessão de edição e continuação atual para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="ab1fd-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab1fd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab1fd-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab1fd-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="ab1fd-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="ab1fd-106">[em] O nome do arquivo o qual salvar alterações.</span><span class="sxs-lookup"><span data-stu-id="ab1fd-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="ab1fd-107">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="ab1fd-107">[in] Reserved.</span></span> <span data-ttu-id="ab1fd-108">Deve ser zero.</span><span class="sxs-lookup"><span data-stu-id="ab1fd-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab1fd-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ab1fd-109">Requirements</span></span>  
 <span data-ttu-id="ab1fd-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab1fd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab1fd-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ab1fd-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab1fd-112">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ab1fd-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ab1fd-113">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab1fd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab1fd-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="ab1fd-114">See also</span></span>

- [<span data-ttu-id="ab1fd-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="ab1fd-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="ab1fd-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="ab1fd-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
