---
title: Enumeração COINITIEE
ms.date: 03/30/2017
api_name:
- COINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COINITIEE
helpviewer_keywords:
- COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4a84fdfdba96c58671302c723b8a56848b70eb60
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180005"
---
# <a name="coinitiee-enumeration"></a>Enumeração COINITIEE
Especifica as constantes usadas pelo [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) ao inicializar o common language runtime.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|Modo de inicialização padrão. Isso inicializa o tempo de execução e cria o padrão <xref:System.AppDomain>.|  
|`COINITEE_DLL`|Inicializa para executar uma DLL gerenciada.|  
|`COINITEE_MAIN`|Inicializa para executar um arquivo EXE gerenciado. Isso inicializa o tempo de execução, mas não cria o padrão <xref:System.AppDomain>, que é criado depois de inserir a rotina do EXE principal.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
