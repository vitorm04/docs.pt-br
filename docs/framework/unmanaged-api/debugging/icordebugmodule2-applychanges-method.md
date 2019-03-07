---
title: Método ICorDebugModule2::ApplyChanges
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ApplyChanges
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ApplyChanges
helpviewer_keywords:
- ApplyChanges method [.NET Framework debugging]
- ICorDebugModule2::ApplyChanges method [.NET Framework debugging]
ms.assetid: 96fa3406-6a6f-41a1-88c6-d9bc5d1a16d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab0e28bd21b66f370a1a1e82359fe474574fd7bb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481567"
---
# <a name="icordebugmodule2applychanges-method"></a>Método ICorDebugModule2::ApplyChanges
Aplica as alterações nos metadados e as alterações no código Microsoft intermediate language (MSIL) para o processo em execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cbMetadata`  
 [in] Tamanho, em bytes, dos metadados do delta.  
  
 `pbMetadata`  
 [in] Buffer que contém os metadados de delta. O endereço do buffer é retornado do [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) método.  
  
 Os endereços virtuais (relacionados RVAs) nos metadados devem ser relativo ao início do código MSIL.  
  
 `cbIL`  
 [in] Tamanho, em bytes, do código MSIL delta.  
  
 `pbIL`  
 [in] Buffer que contém o código MSIL atualizado.  
  
## <a name="remarks"></a>Comentários  
 O `pbMetadata` parâmetro está em um formato de metadados de delta especiais (como saída pelo [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)). `pbMetadata` usa metadados anterior como base e descreve as alterações individuais se aplicam a essa base.  
  
 Em contraste, o `pbIL[`] parâmetro contém o novo MSIL para o método atualizado e é usado para substituir completamente o MSIL para o método anterior  
  
 Quando o delta MSIL e os metadados foram criados na memória do depurador, o depurador chama `ApplyChanges` para enviar as alterações para o common language runtime (CLR). O tempo de execução atualiza suas tabelas de metadados, coloca o MSIL de novo no processo e configura uma compilação de (JIT) just-in-time do novo MSIL. Quando as alterações tiverem sido aplicadas, o depurador deve chamar [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) para se preparar para a próxima sessão de edição. O depurador pode, em seguida, continue o processo.  
  
 Sempre que o depurador chama `ApplyChanges` em um módulo que tem metadados de delta, ele também deve chamar [imetadataemit:: Applyeditandcontinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) com os mesmos metadados delta em todas as cópias dos metadados do módulo, exceto a cópia de usado para emitir as alterações. Se uma cópia dos metadados de alguma forma ficar fora de sincronia com os metadados reais, o depurador sempre pode jogar fora essa cópia e obter uma nova cópia.  
  
 Se o `ApplyChanges` método falhar, a depuração sessão estiver em um estado inválido e deve ser reiniciado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
