---
title: Enumeração WriteableMetadataUpdateMode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- WriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6758f4d3-6bc7-4c99-8582-e9be00566784
topic_type:
- apiref
ms.openlocfilehash: 98566176ff33000fc4b4587b5669a037c90268f5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139102"
---
# <a name="writeablemetadataupdatemode-enumeration"></a>Enumeração WriteableMetadataUpdateMode
[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
 Fornece valores que especificam se as atualizações na memória para metadados estão visíveis para um depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a>Membros  
  
|Nome do membro|Descrição|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|Mantenha a compatibilidade com as versões anteriores do .NET Framework ao fazer atualizações na memória para os metadados visíveis. Consulte a seção Comentários para obter mais informações.|  
|`AlwaysShowUpdates`|Faça atualizações na memória para os metadados visíveis para o depurador.|  
  
## <a name="remarks"></a>Comentários  
 Um membro da enumeração `WriteableMetadataUpdateMode` pode ser passado para o método [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) para controlar se as atualizações na memória para os metadados no processo de destino são visíveis para o depurador.  
  
 A opção `LegacyCompatPolicy` impõe o mesmo comportamento das versões do .NET Framework antes de 4.5.2. Isso geralmente significa que os metadados de atualizações não são visíveis. No entanto, as chamadas para vários métodos de depuração convertem implicitamente o depurador para tornar as atualizações visíveis. Por exemplo, se o depurador passar [ICorDebugILFrame:: GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) o índice de uma variável não for encontrado nos metadados originais do método, todos os metadados do módulo serão atualizados para um instantâneo que corresponde ao estado atual do processo. Em outras palavras, com a opção `LegacyCompatPolicy`, o depurador pode ver nenhuma, algumas ou todas as atualizações de metadados disponíveis, dependendo de como ela usa outras partes da API de depuração não gerenciada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Método SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
