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
ms.openlocfilehash: 99824e9a7fd759fb30bfa377156fc28eb934a2b4
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212211"
---
# <a name="icordebugmodule2applychanges-method"></a>Método ICorDebugModule2::ApplyChanges
Aplica as alterações nos metadados e as alterações no código MSIL (Microsoft Intermediate Language) para o processo em execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cbMetadata`  
 no Tamanho, em bytes, dos metadados delta.  
  
 `pbMetadata`  
 no Buffer que contém os metadados delta. O endereço do buffer é retornado do método [IMetaDataEmit2:: SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md) .  
  
 Os endereços virtuais relativos (RVAs) nos metadados devem ser relativos ao início do código MSIL.  
  
 `cbIL`  
 no Tamanho, em bytes, do código MSIL do Delta.  
  
 `pbIL`  
 no Buffer que contém o código MSIL atualizado.  
  
## <a name="remarks"></a>Comentários  
 O `pbMetadata` parâmetro está em um formato de metadados delta especial (como a saída de [IMetaDataEmit2:: SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md)). `pbMetadata`usa os metadados anteriores como base e descreve as alterações individuais a serem aplicadas a essa base.  
  
 Em contraste, o `pbIL[` parâmetro] contém o novo MSIL para o método atualizado e destina-se a substituir completamente o MSIL anterior para esse método  
  
 Quando o MSIL do Delta e os metadados tiverem sido criados na memória do depurador, o depurador chamará `ApplyChanges` para enviar as alterações para o Common Language Runtime (CLR). O tempo de execução atualiza suas tabelas de metadados, coloca o novo MSIL no processo e configura uma compilação JIT (just-in-time) do novo MSIL. Quando as alterações tiverem sido aplicadas, o depurador deverá chamar [IMetaDataEmit2:: ResetENCLog](../metadata/imetadataemit2-resetenclog-method.md) para se preparar para a próxima sessão de edição. O depurador pode continuar o processo.  
  
 Sempre que o depurador chama `ApplyChanges` um módulo que tem metadados delta, ele também deve chamar [IMetaDataEmit:: ApplyEditAndContinue](../metadata/imetadataemit-applyeditandcontinue-method.md) com os mesmos metadados delta em todas as suas cópias dos metadados desse módulo, exceto para a cópia usada para emitir as alterações. Se uma cópia dos metadados de alguma forma estiver fora de sincronia com os metadados reais, o depurador sempre poderá acabar com a cópia e obter uma nova cópia.  
  
 Se o `ApplyChanges` método falhar, a sessão de depuração estará em um estado inválido e deverá ser reiniciada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
