---
title: "Enumeração ValidatorFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ValidatorFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: ValidatorFlags
helpviewer_keywords: ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f283beb79ec47454185800bd772904c3c696c7c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="validatorflags-enumeration"></a><span data-ttu-id="caab6-102">Enumeração ValidatorFlags</span><span class="sxs-lookup"><span data-stu-id="caab6-102">ValidatorFlags Enumeration</span></span>
<span data-ttu-id="caab6-103">Contém valores que indicam o tipo de validação que deve ser executada em uma chamada para o [Iclrvalidator](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="caab6-103">Contains values that indicate the type of validation that should be performed in a call to the [ICLRValidator::Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caab6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="caab6-104">Syntax</span></span>  
  
```  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a><span data-ttu-id="caab6-105">Membros</span><span class="sxs-lookup"><span data-stu-id="caab6-105">Members</span></span>  
  
|<span data-ttu-id="caab6-106">Membro</span><span class="sxs-lookup"><span data-stu-id="caab6-106">Member</span></span>|<span data-ttu-id="caab6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="caab6-107">Description</span></span>|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|<span data-ttu-id="caab6-108">Especifica que somente o Microsoft intermediate language (MSIL no arquivo executável) deve ser validado.</span><span class="sxs-lookup"><span data-stu-id="caab6-108">Specifies that only the Microsoft intermediate language (MSIL) in the executable file should be validated.</span></span>|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|<span data-ttu-id="caab6-109">Especifica que somente o formato do arquivo executável deve ser validado.</span><span class="sxs-lookup"><span data-stu-id="caab6-109">Specifies that only the format of the executable file should be validated.</span></span>|  
|`VALIDATOR_EXTRA_VERBOSE`|<span data-ttu-id="caab6-110">Especifica que todos os tipos de validação devem ser executados e relatados.</span><span class="sxs-lookup"><span data-stu-id="caab6-110">Specifies that all types of validation should be performed and reported on.</span></span>|  
|`VALIDATOR_NOCHECK_PEFORMAT`|<span data-ttu-id="caab6-111">Especifica que o formato do arquivo executável não deve ser validado.</span><span class="sxs-lookup"><span data-stu-id="caab6-111">Specifies that the format of the executable file should not be validated.</span></span>|  
|`VALIDATOR_SHOW_SOURCE_LINES`|<span data-ttu-id="caab6-112">Especifica que as mensagens de erro de validação devem incluir as linhas do código-fonte que geram erros de validação.</span><span class="sxs-lookup"><span data-stu-id="caab6-112">Specifies that validation error messages should include the lines of source code that raise validation errors.</span></span> <span data-ttu-id="caab6-113">Esse valor de campo não é válido no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="caab6-113">This field value is not valid in the .NET Framework version 2.0.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="caab6-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="caab6-114">Requirements</span></span>  
 <span data-ttu-id="caab6-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caab6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caab6-116">**Cabeçalho:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="caab6-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="caab6-117">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="caab6-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="caab6-118">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caab6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caab6-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="caab6-119">See Also</span></span>  
 [<span data-ttu-id="caab6-120">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="caab6-120">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="caab6-121">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="caab6-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
