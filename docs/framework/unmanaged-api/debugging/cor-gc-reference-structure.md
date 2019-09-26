---
title: Estrutura COR_GC_REFERENCE
ms.date: 03/30/2017
api_name:
- COR_GC_REFERENCE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_GC_REFERENCE
helpviewer_keywords:
- COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc0b67621f77c0741e0b63b84ab1794530d6280b
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274234"
---
# <a name="cor_gc_reference-structure"></a>Estrutura COR_GC_REFERENCE
Contém informações sobre um objeto que será coletado como lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`domain`|Um ponteiro para o domínio do aplicativo ao qual o identificador ou objeto pertence. Seu valor pode ser `null`.|  
|`location`|Uma interface ICorDebugValue ou ICorDebugReferenceValue que corresponde ao objeto a ser coletado como lixo.|  
|`type`|Um valor de enumeração [CorGCReferenceType](corgcreferencetype-enumeration.md) que indica de onde veio a raiz. Para obter mais informações, consulte a seção Comentários.|  
|`extraData`|Dados adicionais sobre o objeto a ser coletado pelo lixo. Essas informações dependem da origem do objeto, conforme indicado pelo `type` campo. Para obter mais informações, consulte a seção Comentários.|  
  
## <a name="remarks"></a>Comentários  
 O `type` campo é um valor de enumeração [CorGCReferenceType](corgcreferencetype-enumeration.md) que indica de onde veio a referência. Um valor `COR_GC_REFERENCE` específico pode refletir qualquer um dos seguintes tipos de objetos gerenciados:  
  
- Objetos de todas as pilhas gerenciadas`CorGCReferenceType.CorReferenceStack`(). Isso inclui referências dinâmicas em código gerenciado, bem como objetos criados pelo Common Language Runtime.  
  
- Objetos da tabela de identificadores`CorGCReferenceType.CorHandle*`(). Isso inclui referências fortes (`HNDTYPE_STRONG` e `HNDTYPE_REFCOUNT`) e variáveis estáticas em um módulo.  
  
- Objetos da fila do finalizador (`CorGCReferenceType.CorReferenceFinalizer`). O finalizador enfileira objetos de raízes até que o finalizador tenha sido executado.  
  
 O `extraData` campo contém dados extras dependendo da origem (ou tipo) da referência. Os possíveis valores são:  
  
- `DependentSource`. `type` Se for `CorGCREferenceType.CorHandleStrongDependent`, esse campo será o objeto que, se estiver ativo, faz a raiz do objeto a `COR_GC_REFERENCE.Location`ser coletado como lixo.  
  
- `RefCount`. `type` Se for `CorGCREferenceType.CorHandleStrongRefCount`, esse campo será a contagem de referência do identificador.  
  
- `Size`. `type` Se for `CorGCREferenceType.CorHandleStrongSizedByref`, esse campo será o último tamanho da árvore de objetos para a qual o coletor de lixo calculou as raízes de objeto. Observe que esse cálculo não está necessariamente atualizado.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de depuração](debugging-structures.md)
- [Depuração](index.md)
