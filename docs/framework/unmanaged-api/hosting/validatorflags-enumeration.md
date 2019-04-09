---
title: Enumeração ValidatorFlags
ms.date: 03/30/2017
api_name:
- ValidatorFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ValidatorFlags
helpviewer_keywords:
- ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa10ae1cf67339a6719210f3162f19ac648e8ee5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127407"
---
# <a name="validatorflags-enumeration"></a><span data-ttu-id="8aeb5-102">Enumeração ValidatorFlags</span><span class="sxs-lookup"><span data-stu-id="8aeb5-102">ValidatorFlags Enumeration</span></span>
<span data-ttu-id="8aeb5-103">Contém valores que indicam o tipo de validação que deve ser executada em uma chamada para o [iclrvalidator:: Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="8aeb5-103">Contains values that indicate the type of validation that should be performed in a call to the [ICLRValidator::Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aeb5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8aeb5-104">Syntax</span></span>  
  
```  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a><span data-ttu-id="8aeb5-105">Membros</span><span class="sxs-lookup"><span data-stu-id="8aeb5-105">Members</span></span>  
  
|<span data-ttu-id="8aeb5-106">Membro</span><span class="sxs-lookup"><span data-stu-id="8aeb5-106">Member</span></span>|<span data-ttu-id="8aeb5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8aeb5-107">Description</span></span>|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|<span data-ttu-id="8aeb5-108">Especifica que somente o Microsoft intermediate language (MSIL no arquivo executável) deve ser validada.</span><span class="sxs-lookup"><span data-stu-id="8aeb5-108">Specifies that only the Microsoft intermediate language (MSIL) in the executable file should be validated.</span></span>|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|<span data-ttu-id="8aeb5-109">Especifica que somente o formato do arquivo executável deve ser validado.</span><span class="sxs-lookup"><span data-stu-id="8aeb5-109">Specifies that only the format of the executable file should be validated.</span></span>|  
|`VALIDATOR_EXTRA_VERBOSE`|<span data-ttu-id="8aeb5-110">Especifica que todos os tipos de validação devem ser executados e relatados.</span><span class="sxs-lookup"><span data-stu-id="8aeb5-110">Specifies that all types of validation should be performed and reported on.</span></span>|  
|`VALIDATOR_NOCHECK_PEFORMAT`|<span data-ttu-id="8aeb5-111">Especifica que o formato do arquivo executável não deve ser validado.</span><span class="sxs-lookup"><span data-stu-id="8aeb5-111">Specifies that the format of the executable file should not be validated.</span></span>|  
|`VALIDATOR_SHOW_SOURCE_LINES`|<span data-ttu-id="8aeb5-112">Especifica que as mensagens de erro de validação devem incluir as linhas de código-fonte que geram erros de validação.</span><span class="sxs-lookup"><span data-stu-id="8aeb5-112">Specifies that validation error messages should include the lines of source code that raise validation errors.</span></span> <span data-ttu-id="8aeb5-113">Esse valor de campo não é válido no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="8aeb5-113">This field value is not valid in the .NET Framework version 2.0.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8aeb5-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8aeb5-114">Requirements</span></span>  
 <span data-ttu-id="8aeb5-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8aeb5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aeb5-116">**Cabeçalho:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="8aeb5-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="8aeb5-117">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8aeb5-117">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="8aeb5-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="8aeb5-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8aeb5-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8aeb5-119">See also</span></span>

- [<span data-ttu-id="8aeb5-120">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="8aeb5-120">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="8aeb5-121">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="8aeb5-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
