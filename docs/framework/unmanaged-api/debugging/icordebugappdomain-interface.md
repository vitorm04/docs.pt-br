---
title: ICorDebugAppDomain Interface1
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
ms.openlocfilehash: 84a11b6264ac0e241c1975eea5626edbdddce206
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugappdomain-interface1"></a>ICorDebugAppDomain Interface1
Fornece métodos para depurar domínios de aplicativo. Esta interface é uma subclasse de ICorDebugController.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Attach](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|Anexa o depurador ao domínio do aplicativo.|  
|[Método EnumerateAssemblies](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|Obtém um enumerador para os assemblies no domínio do aplicativo.|  
|[Método EnumerateBreakpoints](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|Obtém um enumerador para todos os pontos de interrupção ativos no domínio do aplicativo.|  
|[Método EnumerateSteppers](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|Obtém um enumerador para todos os steppers ativos no domínio do aplicativo.|  
|[Método GetId](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|Obtém a ID exclusiva do domínio do aplicativo.|  
|[Método GetModuleFromMetaDataInterface](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|Obtém o objeto ICorDebugModule com a interface de metadados fornecidos.|  
|[Método GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|Obtém o nome do domínio do aplicativo.|  
|[Método GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|Obtém um ponteiro de interface para o domínio de aplicativo do common language runtime (CLR).|  
|[Método GetProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|Obtém o processo que contém o domínio de aplicativo.|  
|[Método IsAttached](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|Determina se o depurador é anexado ao domínio do aplicativo.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
