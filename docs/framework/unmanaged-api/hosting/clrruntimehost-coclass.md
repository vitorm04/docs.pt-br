---
title: Coclass CLRRuntimeHost
ms.date: 03/30/2017
api_name:
- CLRRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLRRuntimeHost
helpviewer_keywords:
- CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type:
- apiref
ms.openlocfilehash: 40766ce5837053493f2e3f1f25fe7d1d63ec695f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616792"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="6deeb-102">Coclass CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="6deeb-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="6deeb-103">Fornece interfaces para gerenciar a execução de código pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6deeb-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6deeb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6deeb-104">Syntax</span></span>  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="6deeb-105">Interfaces</span><span class="sxs-lookup"><span data-stu-id="6deeb-105">Interfaces</span></span>  
  
|<span data-ttu-id="6deeb-106">Interface</span><span class="sxs-lookup"><span data-stu-id="6deeb-106">Interface</span></span>|<span data-ttu-id="6deeb-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6deeb-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="6deeb-108">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="6deeb-108">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)|<span data-ttu-id="6deeb-109">Fornece métodos para controlar a execução de aplicativos pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6deeb-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="6deeb-110">Interface ICLRValidator</span><span class="sxs-lookup"><span data-stu-id="6deeb-110">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)|<span data-ttu-id="6deeb-111">Fornece métodos para validação de imagens executáveis portáteis e para relatórios detalhados de erros de validação.</span><span class="sxs-lookup"><span data-stu-id="6deeb-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6deeb-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6deeb-112">Requirements</span></span>  
 <span data-ttu-id="6deeb-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6deeb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6deeb-114">**Cabeçalho:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="6deeb-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="6deeb-115">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6deeb-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6deeb-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6deeb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6deeb-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="6deeb-117">See also</span></span>

- [<span data-ttu-id="6deeb-118">Hospedando coclasses</span><span class="sxs-lookup"><span data-stu-id="6deeb-118">Hosting Coclasses</span></span>](hosting-coclasses.md)
