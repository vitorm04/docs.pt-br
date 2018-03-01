---
title: Estrutura COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4b5889f8e0b0dc8faab76f637e2fcf03853709bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="corprfassemblyreferenceinfo-structure"></a>Estrutura COR_PRF_ASSEMBLY_REFERENCE_INFO
[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
 Fornece ao Common Language Runtime informações sobre uma referência de assembly que deve ser considerada ao realizar um exame de fechamento de referência de assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _COR_PRF_ASSEMBLY_REFERENCE_INFO {  
    void* pbPublicKeyOrToken;  
    ULONG cbPublicKeyOrToken;  
    LPCWSTR szName;  
    ASSEMBLYMETADATA* pMetaData;  
    void* pbHashValue;  
    ULONG cbHashValue;  
    DWORD dwAssemblyRefFlags;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|Um ponteiro para a chave pública ou token do assembly.|  
|`cbPublicKeyOrToken`|O número de bytes na chave pública ou token.|  
|`szName`|O nome do assembly referenciado.|  
|`pMetaData`|Um ponteiro para os metadados do assembly.|  
|`pbHashValue`|Um ponteiro para um BLOB (objeto binário grande) de hash.|  
|`cbHashValue`|O número de bytes no BLOB de hash.|  
|`dwAssemblyRefFlags`|Os sinalizadores do assembly.|  
  
## <a name="remarks"></a>Comentários  
 A estrutura `COR_PRF_EX_CLAUSE_INFO` é preenchida pelo criador de perfil ao declarar as referências adicionais de assembly que o Common Language Runtime deve considerar quando realiza um exame de fechamento de referência de assembly.  
  
 Se o criador de perfil registra o [Icorprofilercallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) método de retorno de chamada, o tempo de execução passa o caminho e o nome do assembly a ser carregado, junto com um ponteiro para um [ ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) o objeto de interface para esse método. O criador de perfil, em seguida, pode chamar o [Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) método com um `COR_PRF_ASSEMBLY_REFERENCE_INFO` objeto para cada assembly de destino, ela planeja fazer referência do assembly especificado no [ Icorprofilercallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) retorno de chamada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)  
 [Método GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)  
 [Método AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
