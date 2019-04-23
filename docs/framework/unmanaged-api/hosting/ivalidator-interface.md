---
title: Interface IValidator
ms.date: 03/30/2017
api_name:
- IValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IValidator
helpviewer_keywords:
- IValidator interface [.NET Framework hosting]
ms.assetid: b297e3b0-20f9-478f-b707-5e2eecb2b5b2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f516bf1f19e4d4a77e2d6af834a1c3d4e34c327
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121908"
---
# <a name="ivalidator-interface"></a><span data-ttu-id="46fd3-102">Interface IValidator</span><span class="sxs-lookup"><span data-stu-id="46fd3-102">IValidator Interface</span></span>
<span data-ttu-id="46fd3-103">Fornece métodos para validar as imagens portáteis executáveis (PE) e relatando erros de validação.</span><span class="sxs-lookup"><span data-stu-id="46fd3-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="46fd3-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="46fd3-104">Methods</span></span>  
  
|<span data-ttu-id="46fd3-105">Método</span><span class="sxs-lookup"><span data-stu-id="46fd3-105">Method</span></span>|<span data-ttu-id="46fd3-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="46fd3-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="46fd3-107">Validar</span><span class="sxs-lookup"><span data-stu-id="46fd3-107">Validate</span></span>|<span data-ttu-id="46fd3-108">Valida o arquivo especificado de MSIL (linguagem intermediária) de PE ou o Microsoft.</span><span class="sxs-lookup"><span data-stu-id="46fd3-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="46fd3-109">FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="46fd3-109">FormatEventInfo</span></span>|<span data-ttu-id="46fd3-110">Obtém a mensagem de erro correspondente ao erro de validação especificado.</span><span class="sxs-lookup"><span data-stu-id="46fd3-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="46fd3-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="46fd3-111">Requirements</span></span>  
 <span data-ttu-id="46fd3-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46fd3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46fd3-113">**Cabeçalho:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="46fd3-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="46fd3-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="46fd3-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46fd3-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46fd3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46fd3-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46fd3-116">See also</span></span>

- [<span data-ttu-id="46fd3-117">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="46fd3-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="46fd3-118">Coclass CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="46fd3-118">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
