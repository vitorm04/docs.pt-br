---
title: Método ICLRStrongName::StrongNameHashSize
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameHashSize
helpviewer_keywords:
- ICLRStrongName::StrongNameHashSize method [.NET Framework hosting]
- StrongNameHashSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 4a05ee56-08e4-4f3a-86a9-9b52083d5c0f
topic_type:
- apiref
ms.openlocfilehash: 0f4fdcbdfb9db7664920a42b9406a58f9c2de0b8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763105"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="2f8e2-102">Método ICLRStrongName::StrongNameHashSize</span><span class="sxs-lookup"><span data-stu-id="2f8e2-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="2f8e2-103">Obtém o tamanho do buffer necessário para um hash, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="2f8e2-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f8e2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2f8e2-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f8e2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2f8e2-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="2f8e2-106">no O algoritmo de hash usado para calcular o tamanho do buffer.</span><span class="sxs-lookup"><span data-stu-id="2f8e2-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="2f8e2-107">fora O tamanho do buffer retornado, em bytes.</span><span class="sxs-lookup"><span data-stu-id="2f8e2-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f8e2-108">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="2f8e2-108">Return Value</span></span>  
 <span data-ttu-id="2f8e2-109">`S_OK`Se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="2f8e2-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f8e2-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2f8e2-110">Requirements</span></span>  
 <span data-ttu-id="2f8e2-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f8e2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f8e2-112">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="2f8e2-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2f8e2-113">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2f8e2-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f8e2-114">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f8e2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f8e2-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="2f8e2-115">See also</span></span>

- [<span data-ttu-id="2f8e2-116">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="2f8e2-116">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
