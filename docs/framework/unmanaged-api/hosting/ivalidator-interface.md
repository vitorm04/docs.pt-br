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
ms.openlocfilehash: 9f307ad5689602b030c609a51f6834bdbb0ec4f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717708"
---
# <a name="ivalidator-interface"></a><span data-ttu-id="5e272-102">Interface IValidator</span><span class="sxs-lookup"><span data-stu-id="5e272-102">IValidator Interface</span></span>
<span data-ttu-id="5e272-103">Fornece métodos para validar as imagens portáteis executáveis (PE) e relatando erros de validação.</span><span class="sxs-lookup"><span data-stu-id="5e272-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5e272-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="5e272-104">Methods</span></span>  
  
|<span data-ttu-id="5e272-105">Método</span><span class="sxs-lookup"><span data-stu-id="5e272-105">Method</span></span>|<span data-ttu-id="5e272-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e272-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5e272-107">Validar</span><span class="sxs-lookup"><span data-stu-id="5e272-107">Validate</span></span>|<span data-ttu-id="5e272-108">Valida o arquivo especificado de MSIL (linguagem intermediária) de PE ou o Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5e272-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="5e272-109">FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="5e272-109">FormatEventInfo</span></span>|<span data-ttu-id="5e272-110">Obtém a mensagem de erro correspondente ao erro de validação especificado.</span><span class="sxs-lookup"><span data-stu-id="5e272-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5e272-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5e272-111">Requirements</span></span>  
 <span data-ttu-id="5e272-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e272-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e272-113">**Cabeçalho:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="5e272-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="5e272-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5e272-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e272-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e272-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e272-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e272-116">See also</span></span>
- [<span data-ttu-id="5e272-117">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="5e272-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="5e272-118">Coclass CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="5e272-118">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
