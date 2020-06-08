---
title: Método IMetaDataEmit2::GetDeltaSaveSize
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.GetDeltaSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type:
- apiref
ms.openlocfilehash: 24fe8fd65b36e133b767cd07c8602aa1ea7b9dfc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493063"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="73e05-102">Método IMetaDataEmit2::GetDeltaSaveSize</span><span class="sxs-lookup"><span data-stu-id="73e05-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="73e05-103">Obtém um valor que indica qualquer alteração no tamanho dos metadados que resulta da sessão de edição e continuação atual.</span><span class="sxs-lookup"><span data-stu-id="73e05-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73e05-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73e05-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73e05-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="73e05-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="73e05-106">no Um dos valores de [CorSaveSize](corsavesize-enumeration.md) , indicando o nível de precisão desejado.</span><span class="sxs-lookup"><span data-stu-id="73e05-106">[in] One of the [CorSaveSize](corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="73e05-107">Para o .NET Framework versão 2,0, esse parâmetro é ignorado.</span><span class="sxs-lookup"><span data-stu-id="73e05-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="73e05-108">fora A alteração no tamanho dos metadados.</span><span class="sxs-lookup"><span data-stu-id="73e05-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73e05-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="73e05-109">Requirements</span></span>  
 <span data-ttu-id="73e05-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73e05-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73e05-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="73e05-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="73e05-112">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="73e05-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="73e05-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73e05-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73e05-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="73e05-114">See also</span></span>

- [<span data-ttu-id="73e05-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="73e05-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="73e05-116">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="73e05-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
