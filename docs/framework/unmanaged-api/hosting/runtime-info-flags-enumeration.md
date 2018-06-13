---
title: Enumeração RUNTIME_INFO_FLAGS
ms.date: 03/30/2017
api_name:
- RUNTIME_INFO_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RUNTIME_INFO_FLAGS
helpviewer_keywords:
- RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e544db23abf89a20bd2f7763cfdb1256ea4a326c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441358"
---
# <a name="runtimeinfoflags-enumeration"></a>Enumeração RUNTIME_INFO_FLAGS
Contém valores que indicam quais informações sobre o common language runtime (CLR) devem ser retornadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|Indica que as informações de diretório não devem ser incluídas.|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|Indica que as informações de versão não devem ser incluídas.|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|Indica que uma caixa de diálogo de erro não deve ser mostrada em caso de falha.|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|Indica que os efeitos de chamar o [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) função com o sinalizador SEM_FAILCRITICALERRORS deve ser substituída. Ou seja, uma caixa de diálogo de instalação deve ser mostrada após a falha, em vez de ser suprimida.|  
|`RUNTIME_INFO_REQUEST_AMD64`|Indica uma solicitação para obter informações sobre uma versão compatível com 64 AMD do tempo de execução.|  
|`RUNTIME_INFO_REQUEST_IA64`|Indica uma solicitação para obter informações sobre uma versão compatível do IA-64 do tempo de execução.|  
|`RUNTIME_INFO_REQUEST_X86`|Indica uma solicitação para obter informações sobre uma versão compatível com x86 do tempo de execução.|  
|`RUNTIME_INFO_UPGRADE_VERSION`|Indica que as informações de atualização de versão devem ser incluídas.|  
  
## <a name="remarks"></a>Comentários  
 Os seguintes sinalizadores de arquitetura de plataforma podem ser especificada apenas uma por vez e não podem ser combinados:  
  
-   RUNTIME_INFO_REQUEST_IA64  
  
-   RUNTIME_INFO_REQUEST_AMD64  
  
-   RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
