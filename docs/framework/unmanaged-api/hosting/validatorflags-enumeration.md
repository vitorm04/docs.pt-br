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
ms.openlocfilehash: d5eb225241f597baf7a0a5584f4aaf8bf8411ea2
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009464"
---
# <a name="validatorflags-enumeration"></a><span data-ttu-id="d428a-102">Enumeração ValidatorFlags</span><span class="sxs-lookup"><span data-stu-id="d428a-102">ValidatorFlags Enumeration</span></span>
<span data-ttu-id="d428a-103">Contém valores que indicam o tipo de validação que deve ser executado em uma chamada para o método [ICLRValidator:: Validate](iclrvalidator-validate-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d428a-103">Contains values that indicate the type of validation that should be performed in a call to the [ICLRValidator::Validate](iclrvalidator-validate-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d428a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d428a-104">Syntax</span></span>  
  
```cpp  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a><span data-ttu-id="d428a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d428a-105">Members</span></span>  
  
|<span data-ttu-id="d428a-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d428a-106">Member</span></span>|<span data-ttu-id="d428a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d428a-107">Description</span></span>|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|<span data-ttu-id="d428a-108">Especifica que somente a MSIL (Microsoft Intermediate Language) no arquivo executável deve ser validada.</span><span class="sxs-lookup"><span data-stu-id="d428a-108">Specifies that only the Microsoft intermediate language (MSIL) in the executable file should be validated.</span></span>|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|<span data-ttu-id="d428a-109">Especifica que somente o formato do arquivo executável deve ser validado.</span><span class="sxs-lookup"><span data-stu-id="d428a-109">Specifies that only the format of the executable file should be validated.</span></span>|  
|`VALIDATOR_EXTRA_VERBOSE`|<span data-ttu-id="d428a-110">Especifica que todos os tipos de validação devem ser executados e relatados em.</span><span class="sxs-lookup"><span data-stu-id="d428a-110">Specifies that all types of validation should be performed and reported on.</span></span>|  
|`VALIDATOR_NOCHECK_PEFORMAT`|<span data-ttu-id="d428a-111">Especifica que o formato do arquivo executável não deve ser validado.</span><span class="sxs-lookup"><span data-stu-id="d428a-111">Specifies that the format of the executable file should not be validated.</span></span>|  
|`VALIDATOR_SHOW_SOURCE_LINES`|<span data-ttu-id="d428a-112">Especifica que as mensagens de erro de validação devem incluir as linhas do código-fonte que geram erros de validação.</span><span class="sxs-lookup"><span data-stu-id="d428a-112">Specifies that validation error messages should include the lines of source code that raise validation errors.</span></span> <span data-ttu-id="d428a-113">Esse valor de campo não é válido na versão .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="d428a-113">This field value is not valid in the .NET Framework version 2.0.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d428a-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d428a-114">Requirements</span></span>  
 <span data-ttu-id="d428a-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d428a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d428a-116">**Cabeçalho:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="d428a-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="d428a-117">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d428a-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d428a-118">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d428a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d428a-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="d428a-119">See also</span></span>

- [<span data-ttu-id="d428a-120">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="d428a-120">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="d428a-121">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="d428a-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
