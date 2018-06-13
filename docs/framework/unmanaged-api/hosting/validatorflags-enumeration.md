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
ms.openlocfilehash: 20ce52108c1024ad3e07051b226aa65612580e2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441381"
---
# <a name="validatorflags-enumeration"></a>Enumeração ValidatorFlags
Contém valores que indicam o tipo de validação que deve ser executada em uma chamada para o [Iclrvalidator](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|Especifica que somente o Microsoft intermediate language (MSIL no arquivo executável) deve ser validado.|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|Especifica que somente o formato do arquivo executável deve ser validado.|  
|`VALIDATOR_EXTRA_VERBOSE`|Especifica que todos os tipos de validação devem ser executados e relatados.|  
|`VALIDATOR_NOCHECK_PEFORMAT`|Especifica que o formato do arquivo executável não deve ser validado.|  
|`VALIDATOR_SHOW_SOURCE_LINES`|Especifica que as mensagens de erro de validação devem incluir as linhas do código-fonte que geram erros de validação. Esse valor de campo não é válido no .NET Framework versão 2.0.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** IValidator.idl, IValidator.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
