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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 080c16d3a7baceaa277b3418ac2e17391090f00c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750601"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="08741-102">Método ICeeGen::AllocateMethodBuffer</span><span class="sxs-lookup"><span data-stu-id="08741-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="08741-103">Cria um buffer do tamanho especificado para um método e obtém o endereço virtual relativo do método.</span><span class="sxs-lookup"><span data-stu-id="08741-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="08741-104">Esse método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="08741-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08741-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08741-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08741-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="08741-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="08741-107">[in] O comprimento do buffer para criar.</span><span class="sxs-lookup"><span data-stu-id="08741-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="08741-108">[out] O buffer retornado.</span><span class="sxs-lookup"><span data-stu-id="08741-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="08741-109">[out] O endereço virtual relativo do método.</span><span class="sxs-lookup"><span data-stu-id="08741-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08741-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="08741-110">Requirements</span></span>  
 <span data-ttu-id="08741-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08741-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08741-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="08741-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08741-113">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="08741-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="08741-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08741-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08741-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08741-115">See also</span></span>

- [<span data-ttu-id="08741-116">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="08741-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
