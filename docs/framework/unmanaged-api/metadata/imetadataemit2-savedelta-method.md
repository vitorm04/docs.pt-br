---
title: "Método IMetaDataEmit2::SaveDelta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.SaveDelta
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::SaveDelta
helpviewer_keywords:
- IMetaDataEmit2::SaveDelta method [.NET Framework metadata]
- SaveDelta method [.NET Framework metadata]
ms.assetid: b95739fe-d2fa-4776-ae0d-31d9707ef799
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7f2e16d994c648f3c88a23488df75f04dbdaa47a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="cd803-102">Método IMetaDataEmit2::SaveDelta</span><span class="sxs-lookup"><span data-stu-id="cd803-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="cd803-103">Salva as alterações da sessão atual edit-and-continue para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="cd803-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd803-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd803-104">Syntax</span></span>  
  
```  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd803-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cd803-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="cd803-106">[in] O nome do arquivo no qual salvar as alterações.</span><span class="sxs-lookup"><span data-stu-id="cd803-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="cd803-107">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="cd803-107">[in] Reserved.</span></span> <span data-ttu-id="cd803-108">Deve ser zero.</span><span class="sxs-lookup"><span data-stu-id="cd803-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd803-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cd803-109">Requirements</span></span>  
 <span data-ttu-id="cd803-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd803-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd803-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cd803-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd803-112">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="cd803-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cd803-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd803-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd803-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd803-114">See Also</span></span>  
 [<span data-ttu-id="cd803-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="cd803-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="cd803-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="cd803-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
