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
ms.openlocfilehash: c0aea6185095a30aae9197c875aa9b9ac581d406
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121531"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="f3a4e-102">Método ICeeGen::GetMethodBuffer</span><span class="sxs-lookup"><span data-stu-id="f3a4e-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="f3a4e-103">Obtém um buffer de tamanho apropriado para o método no endereço virtual relativo especificado.</span><span class="sxs-lookup"><span data-stu-id="f3a4e-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="f3a4e-104">Esse método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="f3a4e-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3a4e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3a4e-105">Syntax</span></span>  
  
```  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3a4e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f3a4e-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="f3a4e-107">[in] O endereço virtual relativo do método para o qual retornar um buffer.</span><span class="sxs-lookup"><span data-stu-id="f3a4e-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="f3a4e-108">[out] Um ponteiro para o buffer retornado.</span><span class="sxs-lookup"><span data-stu-id="f3a4e-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3a4e-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f3a4e-109">Requirements</span></span>  
 <span data-ttu-id="f3a4e-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3a4e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3a4e-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f3a4e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3a4e-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f3a4e-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="f3a4e-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="f3a4e-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f3a4e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3a4e-114">See also</span></span>

- [<span data-ttu-id="f3a4e-115">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="f3a4e-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
