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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121908"
---
# <a name="ivalidator-interface"></a><span data-ttu-id="ccc9a-102">Interface IValidator</span><span class="sxs-lookup"><span data-stu-id="ccc9a-102">IValidator Interface</span></span>
<span data-ttu-id="ccc9a-103">Fornece métodos para validar as imagens portáteis executáveis (PE) e relatando erros de validação.</span><span class="sxs-lookup"><span data-stu-id="ccc9a-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ccc9a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ccc9a-104">Methods</span></span>  
  
|<span data-ttu-id="ccc9a-105">Método</span><span class="sxs-lookup"><span data-stu-id="ccc9a-105">Method</span></span>|<span data-ttu-id="ccc9a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ccc9a-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ccc9a-107">Validar</span><span class="sxs-lookup"><span data-stu-id="ccc9a-107">Validate</span></span>|<span data-ttu-id="ccc9a-108">Valida o arquivo especificado de MSIL (linguagem intermediária) de PE ou o Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ccc9a-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="ccc9a-109">FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="ccc9a-109">FormatEventInfo</span></span>|<span data-ttu-id="ccc9a-110">Obtém a mensagem de erro correspondente ao erro de validação especificado.</span><span class="sxs-lookup"><span data-stu-id="ccc9a-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ccc9a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ccc9a-111">Requirements</span></span>  
 <span data-ttu-id="ccc9a-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccc9a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccc9a-113">**Cabeçalho:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="ccc9a-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="ccc9a-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ccc9a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="ccc9a-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="ccc9a-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ccc9a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ccc9a-116">See also</span></span>

- [<span data-ttu-id="ccc9a-117">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="ccc9a-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="ccc9a-118">Coclass CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="ccc9a-118">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
