---
title: "Enumeração COR_PRF_CLAUSE_TYPE"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_CLAUSE_TYPE
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_CLAUSE_TYPE
helpviewer_keywords: COR_PRF_CLAUSE_TYPE enumeration [.NET Framework profiling]
ms.assetid: f64c325a-ed3a-4aaf-b847-a88edbc4fefc
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8bd34422656432b9bf8939b81ca0a8583c9d08e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corprfclausetype-enumeration"></a>Enumeração COR_PRF_CLAUSE_TYPE
Indica o tipo de cláusula de exceção que o código acabou de inserir ou deixar.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|A cláusula de exceção não é válida.|  
|`COR_PRF_CLAUSE_FILTER`|A cláusula de exceção é uma expressão de filtro.|  
|`COR_PRF_CLAUSE_CATCH`|A cláusula de exceção é um `catch` instrução.|  
|`COR_PRF_CLAUSE_FINALLY`|A cláusula de exceção é um `finally` instrução.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
