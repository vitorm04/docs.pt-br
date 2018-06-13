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
ms.openlocfilehash: 5a406e945a67352bc7f126b40bd56f4a11dd693b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419537"
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
  
#### <a name="parameters"></a>Parâmetros  
 `cbMetadata`  
 [in] Tamanho, em bytes, dos metadados do delta.  
  
 `pbMetadata`  
 [in] Buffer que contém os metadados de delta. O endereço do buffer é retornado do [Imetadataemit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) método.  
  
 Os endereços virtuais relativos (RVAs) nos metadados devem ser relativo ao início do código MSIL.  
  
 `cbIL`  
 [in] Tamanho, em bytes, de delta código MSIL.  
  
 `pbIL`  
 [in] Buffer que contém o código MSIL atualizado.  
  
## <a name="remarks"></a>Comentários  
 O `pbMetadata` parâmetro está em um formato de metadados de delta especiais (como saída pelo [Imetadataemit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)). `pbMetadata` usa metadados anterior como base e descreve as alterações individuais para aplicar a essa base.  
  
 Em contraste, o `pbIL[`] parâmetro contém o MSIL novo para o método de atualização e é usado para substituir completamente o MSIL anterior para o método  
  
 Quando o delta MSIL e os metadados foram criadas na memória do depurador, o depurador chama `ApplyChanges` para enviar as alterações para o common language runtime (CLR). O tempo de execução suas tabelas de metadados de atualizações, coloca o novo MSIL no processo e configura uma just-in-time compilação JIT () do novo MSIL. Quando as alterações tiverem sido aplicadas, o depurador deve chamar [Imetadataemit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) para se preparar para a próxima sessão de edição. O depurador pode então continuar o processo.  
  
 Sempre que o depurador chama `ApplyChanges` em um módulo que tem metadados de delta, ele também deve chamar [: Applyeditandcontinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) com os mesmos metadados delta em todas as cópias dos metadados do módulo, exceto a cópia usado para emitir as alterações. Se uma cópia dos metadados de alguma forma ficar fora de sincronia com os metadados, o depurador sempre pode descartar essa cópia e obtenha uma nova cópia.  
  
 Se o `ApplyChanges` método falhar, a depuração sessão está em um estado inválido e deve ser reiniciada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
