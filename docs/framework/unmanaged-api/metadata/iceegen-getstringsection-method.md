---
title: Método ICeeGen::GetStringSection
ms.date: 03/30/2017
api_name:
- ICeeGen.GetStringSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetStringSection
helpviewer_keywords:
- ICeeGen::GetStringSection method [.NET Framework metadata]
- GetStringSection method [.NET Framework metadata]
ms.assetid: a2267d39-69d1-4de1-bf37-f752cafacc71
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68dc80c657c3794a416f6e142f70cfb05bee2c77
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745900"
---
# <a name="iceegengetstringsection-method"></a><span data-ttu-id="bc014-102">Método ICeeGen::GetStringSection</span><span class="sxs-lookup"><span data-stu-id="bc014-102">ICeeGen::GetStringSection Method</span></span>
<span data-ttu-id="bc014-103">Obtém uma representação de cadeia de caracteres da seção de código referenciada pelo identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="bc014-103">Gets a string representation of the code section referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="bc014-104">Esse método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="bc014-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc014-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bc014-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringSection (  
    [in, out] HCEESECTION     *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc014-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bc014-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="bc014-107">[no, out] O identificador para a seção de código.</span><span class="sxs-lookup"><span data-stu-id="bc014-107">[in, out] The handle to the code section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc014-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bc014-108">Requirements</span></span>  
 <span data-ttu-id="bc014-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc014-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc014-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bc014-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bc014-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="bc014-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bc014-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc014-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc014-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc014-113">See also</span></span>

- [<span data-ttu-id="bc014-114">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="bc014-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
