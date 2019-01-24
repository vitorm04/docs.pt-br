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
ms.openlocfilehash: 27d9b891475d0fb45c9ec34f3363b0d76fe394c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493198"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="955b1-102">Método IMetaDataEmit2::SaveDelta</span><span class="sxs-lookup"><span data-stu-id="955b1-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="955b1-103">Salva as alterações da sessão atual de editar e continuar para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="955b1-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="955b1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="955b1-104">Syntax</span></span>  
  
```  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="955b1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="955b1-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="955b1-106">[in] O nome do arquivo no qual salvar as alterações.</span><span class="sxs-lookup"><span data-stu-id="955b1-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="955b1-107">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="955b1-107">[in] Reserved.</span></span> <span data-ttu-id="955b1-108">Deve ser zero.</span><span class="sxs-lookup"><span data-stu-id="955b1-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="955b1-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="955b1-109">Requirements</span></span>  
 <span data-ttu-id="955b1-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="955b1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="955b1-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="955b1-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="955b1-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="955b1-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="955b1-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="955b1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="955b1-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="955b1-114">See also</span></span>
- [<span data-ttu-id="955b1-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="955b1-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="955b1-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="955b1-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
