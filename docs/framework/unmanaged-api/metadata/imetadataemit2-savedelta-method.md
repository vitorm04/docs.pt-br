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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7098bceee6bf60cd7781606ffc889b6af9c3e3cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445329"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="de619-102">Método IMetaDataEmit2::SaveDelta</span><span class="sxs-lookup"><span data-stu-id="de619-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="de619-103">Salva as alterações da sessão atual edit-and-continue para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="de619-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de619-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de619-104">Syntax</span></span>  
  
```  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de619-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="de619-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="de619-106">[in] O nome do arquivo no qual salvar as alterações.</span><span class="sxs-lookup"><span data-stu-id="de619-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="de619-107">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="de619-107">[in] Reserved.</span></span> <span data-ttu-id="de619-108">Deve ser zero.</span><span class="sxs-lookup"><span data-stu-id="de619-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de619-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="de619-109">Requirements</span></span>  
 <span data-ttu-id="de619-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de619-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de619-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="de619-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="de619-112">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="de619-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="de619-113">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de619-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de619-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de619-114">See Also</span></span>  
 [<span data-ttu-id="de619-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="de619-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="de619-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="de619-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
