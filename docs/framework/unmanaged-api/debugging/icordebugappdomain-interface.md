---
title: Método ICorDebugAppDomain
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12753ab65f9339e8f6c3049bb72755e87464eb1a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963103"
---
# <a name="icordebugappdomain-interface"></a>Método ICorDebugAppDomain

Fornece métodos para depurar domínios de aplicativo. Essa interface é uma subclasse de ICorDebugController.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Attach](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|Anexa o depurador ao domínio do aplicativo.|  
|[Método EnumerateAssemblies](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|Obtém um enumerador para os assemblies no domínio do aplicativo.|  
|[Método EnumerateBreakpoints](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|Obtém um enumerador para todos os pontos de interrupção ativos no domínio do aplicativo.|  
|[Método EnumerateSteppers](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|Obtém um enumerador para todos os percorridos ativos no domínio do aplicativo.|  
|[Método GetId](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|Obtém a ID exclusiva do domínio do aplicativo.|  
|[Método GetModuleFromMetaDataInterface](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|Obtém o objeto ICorDebugModule com a interface de metadados fornecida.|  
|[Método GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|Obtém o nome do domínio do aplicativo.|  
|[Método GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|Obtém um ponteiro de interface para o domínio do aplicativo Common Language Runtime (CLR).|  
|[Método GetProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|Obtém o processo que contém o domínio do aplicativo.|  
|[Método IsAttached](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|Determina se o depurador está anexado ao domínio do aplicativo.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
