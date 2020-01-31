---
title: Estrutura COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: 4fdc8e1074bf45de3a8ab85500a85b124ce34fa1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867328"
---
# <a name="cor_prf_assembly_reference_info-structure"></a>Estrutura COR_PRF_ASSEMBLY_REFERENCE_INFO
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
  
|{1&gt;Membro&lt;1}|Descrição|  
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
  
 Se o criador de perfil se registrar para o método de retorno de chamada [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) , o tempo de execução passará o caminho e o nome do assembly a ser carregado, juntamente com um ponteiro para um objeto de interface [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) para esse método. O criador de perfil pode então chamar o método [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) com um objeto `COR_PRF_ASSEMBLY_REFERENCE_INFO` para cada assembly de destino que planeja fazer referência a partir do assembly especificado no retorno de chamada [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) .  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Estruturas de criação de perfil](profiling-structures.md)
- [Método GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)
- [Método AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
