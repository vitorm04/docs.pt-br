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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b49b63049d33c41757db1abae82ed2a4e266b42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572208"
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
|`LegacyCompatPolicy`|Manter a compatibilidade com versões anteriores do .NET Framework ao fazer atualizações na memória para metadados visíveis. Consulte a seção Comentários para obter mais informações.|  
|`AlwaysShowUpdates`|Fazer atualizações na memória para metadados visíveis para o depurador.|  
  
## <a name="remarks"></a>Comentários  
 Um membro do `WriteableMetadataUpdateMode` enumeração pode ser passada para o [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) método para controlar se as atualizações de na memória para metadados no processo de destino são visíveis para o depurador.  
  
 O `LegacyCompatPolicy` opção aplica o mesmo comportamento de versões do .NET Framework antes de 4.5.2. Geralmente, isso significa que os metadados de atualizações não estiver visível. No entanto, chamadas para um número de métodos de depuração implicitamente forçar o depurador para fazer atualizações visíveis. Por exemplo, se o depurador passa [icordebugilframe:: Getlocalvariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) o índice de uma variável não encontrado nos metadados de original do método, todos os metadados para o módulo é atualizado para um instantâneo de correspondência o estado atual das processo. Em outras palavras, com o `LegacyCompatPolicy` opção, o depurador poderá ver nenhum, algumas ou todas as atualizações de metadados disponíveis, dependendo de como usar outras partes da API de depuração não gerenciada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Método SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
