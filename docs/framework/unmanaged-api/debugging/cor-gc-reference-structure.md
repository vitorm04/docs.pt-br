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
ms.openlocfilehash: e22269b76c230f702f4712298fddcd0df1fde50d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179324"
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
|`domain`|Um ponteiro para o domínio do aplicativo ao qual a alça ou objeto pertence. Seu valor `null`pode ser.|  
|`location`|Uma interface ICorDebugValue ou ICorDebugReferenceValue que corresponde ao objeto a ser coletado em lixo.|  
|`type`|Um valor de enumeração [CorGCReferenceType](corgcreferencetype-enumeration.md) que indica de onde a raiz veio. Para obter mais informações, consulte a seção Comentários.|  
|`extraData`|Dados adicionais sobre o objeto a ser coletado. Essa informação depende da origem do objeto, conforme `type` indicado pelo campo. Para obter mais informações, consulte a seção Comentários.|  
  
## <a name="remarks"></a>Comentários  
 O `type` campo é um valor de enumeração [CorGCReferenceType](corgcreferencetype-enumeration.md) que indica de onde veio a referência. Um `COR_GC_REFERENCE` valor específico pode refletir qualquer um dos seguintes tipos de objetos gerenciados:  
  
- Objetos de todas as`CorGCReferenceType.CorReferenceStack`pilhas gerenciadas (). Isso inclui referências ao vivo em código gerenciado, bem como objetos criados pelo tempo de execução do idioma comum.  
  
- Objetos da mesa`CorGCReferenceType.CorHandle*`de punho ( ). Isso inclui referências`HNDTYPE_STRONG` fortes `HNDTYPE_REFCOUNT`( e ) e variáveis estáticas em um módulo.  
  
- Objetos da fila do`CorGCReferenceType.CorReferenceFinalizer`finalizador ( ). A fila de finalizador enraiza objetos até que o finalizador seja executado.  
  
 O `extraData` campo contém dados extras dependendo da origem (ou tipo) da referência. Os valores possíveis são:  
  
- `DependentSource`. Se `type` o `CorGCREferenceType.CorHandleStrongDependent`é , este campo é o objeto que, se `COR_GC_REFERENCE.Location`vivo, enraiza o objeto a ser coletado lixo em .  
  
- `RefCount`. Se `type` `CorGCREferenceType.CorHandleStrongRefCount`for, este campo é a contagem de referência da alça.  
  
- `Size`. Se `type` `CorGCREferenceType.CorHandleStrongSizedByref`for, este campo é o último tamanho da árvore de objetos para a qual o coletor de lixo calculou as raízes do objeto. Observe que este cálculo não está necessariamente atualizado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Estruturas de depuração](debugging-structures.md)
- [Depuração](index.md)
