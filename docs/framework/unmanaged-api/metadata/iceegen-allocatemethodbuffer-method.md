---
title: "Método ICeeGen::AllocateMethodBuffer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.AllocateMethodBuffer
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: be288bedf12649b4356c68135868b9415840c4d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="cfe2b-102">Método ICeeGen::AllocateMethodBuffer</span><span class="sxs-lookup"><span data-stu-id="cfe2b-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="cfe2b-103">Cria um buffer do tamanho especificado para um método e obtém o endereço virtual relativo do método.</span><span class="sxs-lookup"><span data-stu-id="cfe2b-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="cfe2b-104">Esse método está obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="cfe2b-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfe2b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cfe2b-105">Syntax</span></span>  
  
```  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cfe2b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cfe2b-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="cfe2b-107">[in] O comprimento do buffer para criar.</span><span class="sxs-lookup"><span data-stu-id="cfe2b-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="cfe2b-108">[out] O buffer retornado.</span><span class="sxs-lookup"><span data-stu-id="cfe2b-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="cfe2b-109">[out] O endereço virtual relativo do método.</span><span class="sxs-lookup"><span data-stu-id="cfe2b-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfe2b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cfe2b-110">Requirements</span></span>  
 <span data-ttu-id="cfe2b-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfe2b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfe2b-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cfe2b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cfe2b-113">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="cfe2b-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cfe2b-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfe2b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfe2b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cfe2b-115">See Also</span></span>  
 [<span data-ttu-id="cfe2b-116">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="cfe2b-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
