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
ms.openlocfilehash: 05f39befa8966046cd71db82da37c44f20992cff
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008799"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="fc9f1-102">Método ICeeGen::GetIlSection</span><span class="sxs-lookup"><span data-stu-id="fc9f1-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="fc9f1-103">Obtém a seção da base de código de linguagem intermediária referenciada pelo identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="fc9f1-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="fc9f1-104">Este método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="fc9f1-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc9f1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc9f1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc9f1-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fc9f1-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="fc9f1-107">no O identificador para a seção a ser obtido.</span><span class="sxs-lookup"><span data-stu-id="fc9f1-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc9f1-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc9f1-108">Requirements</span></span>  
 <span data-ttu-id="fc9f1-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc9f1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc9f1-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fc9f1-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc9f1-111">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fc9f1-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fc9f1-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc9f1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc9f1-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="fc9f1-113">See also</span></span>

- [<span data-ttu-id="fc9f1-114">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="fc9f1-114">ICeeGen Interface</span></span>](iceegen-interface.md)
