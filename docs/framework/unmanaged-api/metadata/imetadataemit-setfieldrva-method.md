---
title: Método IMetaDataEmit::SetFieldRVA
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldRVA
helpviewer_keywords:
- IMetaDataEmit::SetFieldRVA method [.NET Framework metadata]
- SetFieldRVA method [.NET Framework metadata]
ms.assetid: 6dc37f9d-87ee-4cb3-9216-ced600184ce8
topic_type:
- apiref
ms.openlocfilehash: d429995e41006798aee5f796150bedbd6ae87f6f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003861"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="48238-102">Método IMetaDataEmit::SetFieldRVA</span><span class="sxs-lookup"><span data-stu-id="48238-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="48238-103">Define um valor de variável global para o endereço virtual relativo do campo referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="48238-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48238-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48238-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldRVA (
    [in]  mdFieldDef  fd,
    [in]  ULONG       ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48238-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="48238-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="48238-106">no O token para o campo de destino.</span><span class="sxs-lookup"><span data-stu-id="48238-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="48238-107">no O endereço de um código ou área de dados.</span><span class="sxs-lookup"><span data-stu-id="48238-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48238-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48238-108">Requirements</span></span>  
 <span data-ttu-id="48238-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48238-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48238-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="48238-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="48238-111">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="48238-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="48238-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48238-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48238-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="48238-113">See also</span></span>

- [<span data-ttu-id="48238-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="48238-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="48238-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="48238-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
