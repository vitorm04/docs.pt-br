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
ms.openlocfilehash: a093b18f72cc99c53951b3dc588ce0cff3c7fefd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442602"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="a2b91-102">Método ICeeGen::GetMethodBuffer</span><span class="sxs-lookup"><span data-stu-id="a2b91-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="a2b91-103">Obtém um buffer de tamanho apropriado para o método no endereço virtual relativo especificado.</span><span class="sxs-lookup"><span data-stu-id="a2b91-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="a2b91-104">Esse método está obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="a2b91-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2b91-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a2b91-105">Syntax</span></span>  
  
```  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2b91-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a2b91-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="a2b91-107">[in] O endereço virtual relativo do método para o qual retornar um buffer.</span><span class="sxs-lookup"><span data-stu-id="a2b91-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="a2b91-108">[out] Um ponteiro para o buffer retornado.</span><span class="sxs-lookup"><span data-stu-id="a2b91-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2b91-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a2b91-109">Requirements</span></span>  
 <span data-ttu-id="a2b91-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2b91-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2b91-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a2b91-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2b91-112">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a2b91-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a2b91-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2b91-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2b91-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2b91-114">See Also</span></span>  
 [<span data-ttu-id="a2b91-115">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="a2b91-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
