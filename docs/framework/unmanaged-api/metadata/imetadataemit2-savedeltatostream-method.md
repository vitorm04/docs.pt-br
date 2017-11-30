---
title: "Método IMetaDataEmit2::SaveDeltaToStream"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.SaveDeltaToStream
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4bab7bd9035c0746b7f789925e23b74e2caade6a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="adcf8-102">Método IMetaDataEmit2::SaveDeltaToStream</span><span class="sxs-lookup"><span data-stu-id="adcf8-102">IMetaDataEmit2::SaveDeltaToStream Method</span></span>
<span data-ttu-id="adcf8-103">Salva as alterações da sessão atual de editar e continuar o fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="adcf8-103">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adcf8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="adcf8-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="adcf8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="adcf8-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="adcf8-106">[in] Um ponteiro de interface para o fluxo gravável no qual salvar as alterações.</span><span class="sxs-lookup"><span data-stu-id="adcf8-106">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="adcf8-107">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="adcf8-107">[in] Reserved.</span></span> <span data-ttu-id="adcf8-108">Esse valor deve ser zero.</span><span class="sxs-lookup"><span data-stu-id="adcf8-108">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adcf8-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="adcf8-109">Requirements</span></span>  
 <span data-ttu-id="adcf8-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adcf8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adcf8-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="adcf8-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="adcf8-112">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="adcf8-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="adcf8-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adcf8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adcf8-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="adcf8-114">See Also</span></span>  
 [<span data-ttu-id="adcf8-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="adcf8-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="adcf8-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="adcf8-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
