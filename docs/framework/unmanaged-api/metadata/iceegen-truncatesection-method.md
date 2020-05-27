---
title: Método ICeeGen::TruncateSection
ms.date: 03/30/2017
api_name:
- ICeeGen.TruncateSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::TruncateSection
helpviewer_keywords:
- TruncateSection method [.NET Framework metadata]
- ICeeGen::TruncateSection method [.NET Framework metadata]
ms.assetid: 0451d752-1e5c-4c9a-8bad-6cd35b7ba3df
topic_type:
- apiref
ms.openlocfilehash: 387f5f01f2d2589c0b34e50b69398e1feb0e77e0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008238"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="6c042-102">Método ICeeGen::TruncateSection</span><span class="sxs-lookup"><span data-stu-id="6c042-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="6c042-103">Trunca a seção de código especificada pelo comprimento especificado.</span><span class="sxs-lookup"><span data-stu-id="6c042-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="6c042-104">Este método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="6c042-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c042-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c042-105">Syntax</span></span>  
  
```cpp  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c042-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6c042-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="6c042-107">no A seção a ser truncada.</span><span class="sxs-lookup"><span data-stu-id="6c042-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="6c042-108">no O comprimento, em bytes, pelo qual truncar a seção.</span><span class="sxs-lookup"><span data-stu-id="6c042-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c042-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c042-109">Remarks</span></span>  
 <span data-ttu-id="6c042-110">Chame `TruncateSection` somente se você tiver requisitos de seção especiais que não são tratados por outros métodos.</span><span class="sxs-lookup"><span data-stu-id="6c042-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c042-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6c042-111">Requirements</span></span>  
 <span data-ttu-id="6c042-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c042-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c042-113">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6c042-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6c042-114">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6c042-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6c042-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c042-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c042-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="6c042-116">See also</span></span>

- [<span data-ttu-id="6c042-117">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="6c042-117">ICeeGen Interface</span></span>](iceegen-interface.md)
