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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1036d6080bf17eea288724c7980ce53dfa2121f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116315"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="01880-102">Método ICeeGen::TruncateSection</span><span class="sxs-lookup"><span data-stu-id="01880-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="01880-103">Trunca a seção de código especificado pelo comprimento especificado.</span><span class="sxs-lookup"><span data-stu-id="01880-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="01880-104">Esse método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="01880-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01880-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="01880-105">Syntax</span></span>  
  
```  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01880-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="01880-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="01880-107">[in] A seção a ser truncado.</span><span class="sxs-lookup"><span data-stu-id="01880-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="01880-108">[in] O comprimento, em bytes, pelo qual a seção de truncar.</span><span class="sxs-lookup"><span data-stu-id="01880-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01880-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="01880-109">Remarks</span></span>  
 <span data-ttu-id="01880-110">Chamar `TruncateSection` somente se você tiver requisitos especiais de seção que não são manipulados por outros métodos.</span><span class="sxs-lookup"><span data-stu-id="01880-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01880-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="01880-111">Requirements</span></span>  
 <span data-ttu-id="01880-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01880-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01880-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="01880-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="01880-114">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="01880-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="01880-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="01880-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="01880-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01880-116">See also</span></span>

- [<span data-ttu-id="01880-117">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="01880-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
