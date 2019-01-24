---
title: Enumeração ILCodeKind
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0fa7d06f39dc05da6fd1657404f882c14c44ea9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505010"
---
# <a name="ilcodekind-enumeration"></a>Enumeração ILCodeKind
[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
 Fornece valores que especificam se o depurador é capaz de acessar variáveis locais ou o código incluído na instrumentação ReJIT do criador de perfis.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a>Membros  
  
|Nome do membro|Descrição|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|O depurador não tem acesso a informações de instrumentação ReJIT.|  
|`ILCODE_REJIT_IL`|O depurador tem acesso a informações de instrumentação ReJIT.|  
  
## <a name="remarks"></a>Comentários  
 Um membro do `ILCodeKind` enumeração pode ser passada para o [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) e [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) métodos para determinar se o depurador pode acessar variáveis adicionadas no criador de perfil Instrumentação ReJIT e para o [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) IL instrumentada do método para determinar se o depurador pode acessar.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Interface ICorDebugILFrame4](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [ReJIT: Um guia de instruções](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
