---
title: Método ICeeGen::AllocateMethodBuffer
ms.date: 03/30/2017
api_name:
- ICeeGen.AllocateMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type:
- apiref
ms.openlocfilehash: 38b9ea2ffab439f55f0a6d34d7f42c7669629168
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177923"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="fcc3a-102">Método ICeeGen::AllocateMethodBuffer</span><span class="sxs-lookup"><span data-stu-id="fcc3a-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="fcc3a-103">Cria um buffer do tamanho especificado para um método e obtém o endereço virtual relativo do método.</span><span class="sxs-lookup"><span data-stu-id="fcc3a-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="fcc3a-104">Este método é obsoleto e não deve ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="fcc3a-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcc3a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fcc3a-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (
    [in]  ULONG    cchBuffer,
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcc3a-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="fcc3a-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="fcc3a-107">[em] O comprimento do buffer para criar.</span><span class="sxs-lookup"><span data-stu-id="fcc3a-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="fcc3a-108">[fora] O tampão devolvido.</span><span class="sxs-lookup"><span data-stu-id="fcc3a-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="fcc3a-109">[fora] O endereço virtual relativo do método.</span><span class="sxs-lookup"><span data-stu-id="fcc3a-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcc3a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fcc3a-110">Requirements</span></span>  
 <span data-ttu-id="fcc3a-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcc3a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcc3a-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fcc3a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fcc3a-113">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fcc3a-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fcc3a-114">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcc3a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcc3a-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="fcc3a-115">See also</span></span>

- [<span data-ttu-id="fcc3a-116">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="fcc3a-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
