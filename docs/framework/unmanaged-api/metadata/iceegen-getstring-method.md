---
title: Método ICeeGen::GetString
ms.date: 03/30/2017
api_name:
- ICeeGen.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type:
- apiref
ms.openlocfilehash: ada126b41f1c634f7d8daa58480406ac26f92377
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177900"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="8b42c-102">Método ICeeGen::GetString</span><span class="sxs-lookup"><span data-stu-id="8b42c-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="8b42c-103">Obtém a seqüência armazenada no endereço virtual relativo especificado.</span><span class="sxs-lookup"><span data-stu-id="8b42c-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="8b42c-104">Este método é obsoleto e não deve ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="8b42c-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b42c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b42c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b42c-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="8b42c-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="8b42c-107">[em] O endereço virtual relativo da string para retornar.</span><span class="sxs-lookup"><span data-stu-id="8b42c-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="8b42c-108">[fora] A corda devolvida.</span><span class="sxs-lookup"><span data-stu-id="8b42c-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b42c-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8b42c-109">Requirements</span></span>  
 <span data-ttu-id="8b42c-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b42c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b42c-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8b42c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b42c-112">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8b42c-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8b42c-113">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b42c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b42c-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="8b42c-114">See also</span></span>

- [<span data-ttu-id="8b42c-115">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="8b42c-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
