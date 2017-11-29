---
title: "Enumeração WriteableMetadataUpdateMode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: WriteableMetadataUpdateMode
api_location: mscordbi.dll
api_type: COM
ms.assetid: 6758f4d3-6bc7-4c99-8582-e9be00566784
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 001d80a2232f5b6fbfb43b9de5deafb3317e426d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
|`LegacyCompatPolicy`|Manter a compatibilidade com versões anteriores do .NET Framework ao fazer atualizações na memória visível nos metadados. Consulte a seção Comentários para obter mais informações.|  
|`AlwaysShowUpdates`|Tornar visível o depurador atualizações na memória para metadados.|  
  
## <a name="remarks"></a>Comentários  
 Membro de `WriteableMetadataUpdateMode` enumeração pode ser passada para o [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) método para controlar se as atualizações de na memória para metadados no processo de destino estão visíveis para o depurador.  
  
 O `LegacyCompatPolicy` opção impõe o mesmo comportamento de versões do .NET Framework antes de 4.5.2. Isso geralmente significa que os metadados de atualizações não estiver visível. No entanto, chamadas para um número de métodos de depuração implicitamente forçar o depurador para fazer atualizações visíveis. Por exemplo, se o depurador passa [Icordebugilframe](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) o índice de uma variável não encontrado no metadados originais do método, todos os metadados para o módulo é atualizado para um instantâneo correspondência o estado atual das processo. Em outras palavras, com o `LegacyCompatPolicy` opção, o depurador pode ver nenhum, algumas ou todas as atualizações de metadados disponíveis, dependendo de como ele usa a outras partes da API de depuração não gerenciada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [Método SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
