---
title: Estrutura COR_GC_REFERENCE
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_REFERENCE
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_GC_REFERENCE
helpviewer_keywords: COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 11be45743bd215315139fb77f016e85bc9b592c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="corgcreference-structure"></a>Estrutura COR_GC_REFERENCE
Contém informações sobre um objeto que será coletado como lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
|`domain`|Um ponteiro para o domínio do aplicativo ao qual pertence o identificador ou um objeto. Seu valor pode ser `null`.|  
|`location`|Um ICorDebugValue ou uma interface ICorDebugReferenceValue que corresponde ao objeto a ser coletado como lixo.|  
|`type`|Um [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) valor de enumeração que indica o local de origem raiz. Para obter mais informações, consulte a seção Comentários.|  
|`extraData`|Dados adicionais sobre o objeto a ser coletado como lixo. Essas informações dependem da origem do objeto, conforme indicado pelo `type` campo. Para obter mais informações, consulte a seção Comentários.|  
  
## <a name="remarks"></a>Comentários  
 O `type` campo é um [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) valor de enumeração que indica onde veio a referência. Um determinado `COR_GC_REFERENCE` valor pode refletir qualquer um dos seguintes tipos de objetos gerenciados:  
  
-   Objetos de todas as pilhas gerenciadas (`CorGCReferenceType.CorReferenceStack`). Isso inclui referências ao vivo em código gerenciado, bem como os objetos criados pelo common language runtime.  
  
-   Objetos da tabela de identificador (`CorGCReferenceType.CorHandle*`). Isso inclui referências fortes (`HNDTYPE_STRONG` e `HNDTYPE_REFCOUNT`) e variáveis estáticas em um módulo.  
  
-   Objetos de fila do finalizador (`CorGCReferenceType.CorReferenceFinalizer`). Fila do finalizador raízes objetos até que tenha executado o finalizador.  
  
 O `extraData` campo contém dados extras dependendo da origem (ou tipo) da referência. Os possíveis valores são:  
  
-   `DependentSource`. Se o `type` é `CorGCREferenceType.CorHandleStrongDependent`, este campo é o objeto que, se estiver ativo, raízes do objeto para o coletor de lixo em `COR_GC_REFERENCE.Location`.  
  
-   `RefCount`. Se o `type` é `CorGCREferenceType.CorHandleStrongRefCount`, esse campo é a contagem de referência do identificador.  
  
-   `Size`. Se o `type` é `CorGCREferenceType.CorHandleStrongSizedByref`, esse campo é o último tamanho da árvore de objetos para o qual o coletor de lixo calculado as raízes de objeto. Observe que esse cálculo não é necessariamente atualizado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
