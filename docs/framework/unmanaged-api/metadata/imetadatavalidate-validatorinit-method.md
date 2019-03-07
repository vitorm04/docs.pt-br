---
title: Método IMetaDataValidate::ValidatorInit
ms.date: 03/30/2017
api_name:
- IMetaDataValidate.ValidatorInit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataValidate::ValidatorInit
helpviewer_keywords:
- IMetaDataValidate::ValidatorInit method [.NET Framework metadata]
- ValidatorInit method [.NET Framework metadata]
ms.assetid: 6bafd75a-e2d0-4aea-aed1-074374d5dff6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d2018be28cbfe72bb7c989634374b8ab43693e6f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491952"
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="1345a-102">Método IMetaDataValidate::ValidatorInit</span><span class="sxs-lookup"><span data-stu-id="1345a-102">IMetaDataValidate::ValidatorInit Method</span></span>
<span data-ttu-id="1345a-103">Define um sinalizador que especifica o tipo de módulo no escopo atual de metadados e registra o método de retorno de chamada especificados para erros de validação.</span><span class="sxs-lookup"><span data-stu-id="1345a-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1345a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1345a-104">Syntax</span></span>  
  
```  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1345a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1345a-105">Parameters</span></span>  
 `dwModule`  
 <span data-ttu-id="1345a-106">[in] Um valor igual a [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) enumeração que especifica o tipo do módulo no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="1345a-106">[in] A value of the [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="1345a-107">[in] Um ponteiro para um [IUnknown](/cpp/atl/iunknown) instância que serve como um retorno de chamada de função para erros de validação.</span><span class="sxs-lookup"><span data-stu-id="1345a-107">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1345a-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1345a-108">Requirements</span></span>  
 <span data-ttu-id="1345a-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1345a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1345a-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1345a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1345a-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="1345a-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1345a-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1345a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1345a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1345a-113">See also</span></span>
- [<span data-ttu-id="1345a-114">Interface IMetaDataValidate</span><span class="sxs-lookup"><span data-stu-id="1345a-114">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)
