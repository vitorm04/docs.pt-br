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
ms.openlocfilehash: 9587bbe8f087fd9a51bba67492af1d5acb53ae4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176091"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="f3098-102">Método ICeeGen::ComputePointer</span><span class="sxs-lookup"><span data-stu-id="f3098-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="f3098-103">Determina o buffer para a seção de código especificada.</span><span class="sxs-lookup"><span data-stu-id="f3098-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="f3098-104">Este método é obsoleto e não deve ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="f3098-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3098-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3098-105">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3098-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="f3098-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="f3098-107">[em] A seção de código para a qual retornar um buffer.</span><span class="sxs-lookup"><span data-stu-id="f3098-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="f3098-108">[em] O endereço virtual relativo do método para o qual obter um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="f3098-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="f3098-109">[fora] Um ponteiro para o buffer devolvido.</span><span class="sxs-lookup"><span data-stu-id="f3098-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3098-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f3098-110">Requirements</span></span>  
 <span data-ttu-id="f3098-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3098-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3098-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f3098-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3098-113">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f3098-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3098-114">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3098-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3098-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="f3098-115">See also</span></span>

- [<span data-ttu-id="f3098-116">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="f3098-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
