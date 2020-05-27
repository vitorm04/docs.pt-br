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
ms.openlocfilehash: 87e00a69643b6bc403188fb0fdb6f9e3f3d82115
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003865"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="59c81-102">Método IMetaDataEmit::SaveToStream</span><span class="sxs-lookup"><span data-stu-id="59c81-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="59c81-103">Salva todos os metadados no escopo atual para o especificado `IStream` .</span><span class="sxs-lookup"><span data-stu-id="59c81-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59c81-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59c81-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToStream (
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59c81-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="59c81-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="59c81-106">no O fluxo gravável no qual salvar.</span><span class="sxs-lookup"><span data-stu-id="59c81-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="59c81-107">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="59c81-107">[in] Reserved.</span></span> <span data-ttu-id="59c81-108">Deve ser zero.</span><span class="sxs-lookup"><span data-stu-id="59c81-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59c81-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="59c81-109">Requirements</span></span>  
 <span data-ttu-id="59c81-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59c81-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59c81-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="59c81-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="59c81-112">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="59c81-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="59c81-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59c81-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59c81-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="59c81-114">See also</span></span>

- [<span data-ttu-id="59c81-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="59c81-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="59c81-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="59c81-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
