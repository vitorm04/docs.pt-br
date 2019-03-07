---
title: Método ICeeGen::GetMethodBuffer
ms.date: 03/30/2017
api_name:
- ICeeGen.GetMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d8ccaa1b03ae1afc87eb7b0a66dd517bba8fcf8a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497464"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="77e6c-102">Método ICeeGen::GetMethodBuffer</span><span class="sxs-lookup"><span data-stu-id="77e6c-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="77e6c-103">Obtém um buffer de tamanho apropriado para o método no endereço virtual relativo especificado.</span><span class="sxs-lookup"><span data-stu-id="77e6c-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="77e6c-104">Esse método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="77e6c-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77e6c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77e6c-105">Syntax</span></span>  
  
```  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77e6c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="77e6c-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="77e6c-107">[in] O endereço virtual relativo do método para o qual retornar um buffer.</span><span class="sxs-lookup"><span data-stu-id="77e6c-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="77e6c-108">[out] Um ponteiro para o buffer retornado.</span><span class="sxs-lookup"><span data-stu-id="77e6c-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77e6c-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="77e6c-109">Requirements</span></span>  
 <span data-ttu-id="77e6c-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77e6c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77e6c-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="77e6c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="77e6c-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="77e6c-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="77e6c-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77e6c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77e6c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77e6c-114">See also</span></span>
- [<span data-ttu-id="77e6c-115">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="77e6c-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
