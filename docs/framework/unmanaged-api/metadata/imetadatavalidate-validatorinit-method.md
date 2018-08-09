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
ms.openlocfilehash: 053c94bc540b130510f155506b6fad32f032a475
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449540"
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="0487f-102">Método IMetaDataValidate::ValidatorInit</span><span class="sxs-lookup"><span data-stu-id="0487f-102">IMetaDataValidate::ValidatorInit Method</span></span>
<span data-ttu-id="0487f-103">Define um sinalizador que especifica o tipo de módulo no escopo atual de metadados e registra o método de retorno de chamada especificada para erros de validação.</span><span class="sxs-lookup"><span data-stu-id="0487f-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0487f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0487f-104">Syntax</span></span>  
  
```  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0487f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0487f-105">Parameters</span></span>  
 `dwModule`  
 <span data-ttu-id="0487f-106">[in] Um valor de [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) enumeração que especifica o tipo de módulo no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="0487f-106">[in] A value of the [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="0487f-107">[in] Um ponteiro para um <<!--zzxref:IUnknown --> `IUnknown`> instância que serve como um retorno de chamada de função para erros de validação.</span><span class="sxs-lookup"><span data-stu-id="0487f-107">[in] A pointer to an <<!--zzxref:IUnknown --> `IUnknown`> instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0487f-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0487f-108">Requirements</span></span>  
 <span data-ttu-id="0487f-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0487f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0487f-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0487f-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0487f-111">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="0487f-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0487f-112">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0487f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0487f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0487f-113">See Also</span></span>  
 [<span data-ttu-id="0487f-114">Interface IMetaDataValidate</span><span class="sxs-lookup"><span data-stu-id="0487f-114">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)
