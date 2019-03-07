---
title: Método ICeeGen::ComputePointer
ms.date: 03/30/2017
api_name:
- ICeeGen.ComputePointer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::ComputePointer
helpviewer_keywords:
- ICeeGen::ComputePointer method [.NET Framework metadata]
- ComputePointer method [.NET Framework metadata]
ms.assetid: b6b95c04-0f2c-4fcc-a8bc-3b1dcbdba731
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5fb63d4fe1e736ca1ff0c729d8d83cfe092eaaf5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465524"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="f3533-102">Método ICeeGen::ComputePointer</span><span class="sxs-lookup"><span data-stu-id="f3533-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="f3533-103">Determina o buffer para a seção de código especificada.</span><span class="sxs-lookup"><span data-stu-id="f3533-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="f3533-104">Esse método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="f3533-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3533-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3533-105">Syntax</span></span>  
  
```  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,   
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3533-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f3533-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="f3533-107">[in] A seção de código para o qual retornar um buffer.</span><span class="sxs-lookup"><span data-stu-id="f3533-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="f3533-108">[in] O endereço virtual relativo do método para o qual obter um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="f3533-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="f3533-109">[out] Um ponteiro para o buffer retornado.</span><span class="sxs-lookup"><span data-stu-id="f3533-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3533-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f3533-110">Requirements</span></span>  
 <span data-ttu-id="f3533-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3533-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3533-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f3533-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3533-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f3533-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3533-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3533-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3533-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3533-115">See also</span></span>
- [<span data-ttu-id="f3533-116">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="f3533-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
