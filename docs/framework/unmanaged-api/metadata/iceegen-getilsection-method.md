---
title: Método ICeeGen::GetIlSection
ms.date: 03/30/2017
api_name:
- ICeeGen.GetIlSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetIlSection
helpviewer_keywords:
- GetIlSection method [.NET Framework metadata]
- ICeeGen::GetIlSection method [.NET Framework metadata]
ms.assetid: 6f2db2ca-203f-4ac3-9530-208642ca385e
topic_type:
- apiref
ms.openlocfilehash: 7ef944fd06d07dc8c4e49061a5e72d8acc4d0465
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436350"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="1d02f-102">Método ICeeGen::GetIlSection</span><span class="sxs-lookup"><span data-stu-id="1d02f-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="1d02f-103">Obtém a seção da base de código de linguagem intermediária referenciada pelo identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="1d02f-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="1d02f-104">Este método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="1d02f-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d02f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d02f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d02f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1d02f-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="1d02f-107">no O identificador para a seção a ser obtido.</span><span class="sxs-lookup"><span data-stu-id="1d02f-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d02f-108">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="1d02f-108">Requirements</span></span>  
 <span data-ttu-id="1d02f-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d02f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d02f-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1d02f-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1d02f-111">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1d02f-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1d02f-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d02f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d02f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d02f-113">See also</span></span>

- [<span data-ttu-id="1d02f-114">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="1d02f-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
