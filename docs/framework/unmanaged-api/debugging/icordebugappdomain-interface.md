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
ms.openlocfilehash: da7c0fb472df89d94fa702a13eff968a4c7e68e3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785038"
---
# <a name="icordebugappdomain-interface"></a>Método ICorDebugAppDomain

Fornece métodos para depurar domínios de aplicativo. Essa interface é uma subclasse de ICorDebugController.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Attach](icordebugappdomain-attach-method.md)|Anexa o depurador ao domínio do aplicativo.|  
|[Método EnumerateAssemblies](icordebugappdomain-enumerateassemblies-method.md)|Obtém um enumerador para os assemblies no domínio do aplicativo.|  
|[Método EnumerateBreakpoints](icordebugappdomain-enumeratebreakpoints-method.md)|Obtém um enumerador para todos os pontos de interrupção ativos no domínio do aplicativo.|  
|[Método EnumerateSteppers](icordebugappdomain-enumeratesteppers-method.md)|Obtém um enumerador para todos os percorridos ativos no domínio do aplicativo.|  
|[Método GetId](icordebugappdomain-getid-method.md)|Obtém a ID exclusiva do domínio do aplicativo.|  
|[Método GetModuleFromMetaDataInterface](icordebugappdomain-getmodulefrommetadatainterface-method.md)|Obtém o objeto ICorDebugModule com a interface de metadados fornecida.|  
|[Método GetName](icordebugappdomain-getname-method.md)|Obtém o nome do domínio do aplicativo.|  
|[Método GetObject](icordebugappdomain-getobject-method.md)|Obtém um ponteiro de interface para o domínio do aplicativo Common Language Runtime (CLR).|  
|[Método GetProcess](icordebugappdomain-getprocess-method.md)|Obtém o processo que contém o domínio do aplicativo.|  
|[Método IsAttached](icordebugappdomain-isattached-method.md)|Determina se o depurador está anexado ao domínio do aplicativo.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
