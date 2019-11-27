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
ms.openlocfilehash: 87a70587027f283ef5976089b3f2daf1204e68ec
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426110"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="bea98-102">Método ICeeGen::TruncateSection</span><span class="sxs-lookup"><span data-stu-id="bea98-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="bea98-103">Trunca a seção de código especificada pelo comprimento especificado.</span><span class="sxs-lookup"><span data-stu-id="bea98-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="bea98-104">Este método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="bea98-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bea98-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bea98-105">Syntax</span></span>  
  
```cpp  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bea98-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bea98-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="bea98-107">no A seção a ser truncada.</span><span class="sxs-lookup"><span data-stu-id="bea98-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="bea98-108">no O comprimento, em bytes, pelo qual truncar a seção.</span><span class="sxs-lookup"><span data-stu-id="bea98-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bea98-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="bea98-109">Remarks</span></span>  
 <span data-ttu-id="bea98-110">Chame `TruncateSection` somente se você tiver requisitos de seção especiais que não são tratados por outros métodos.</span><span class="sxs-lookup"><span data-stu-id="bea98-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bea98-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="bea98-111">Requirements</span></span>  
 <span data-ttu-id="bea98-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bea98-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bea98-113">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bea98-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bea98-114">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bea98-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bea98-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bea98-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bea98-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bea98-116">See also</span></span>

- [<span data-ttu-id="bea98-117">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="bea98-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
