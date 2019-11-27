---
title: Enumeração COR_PRF_MODULE_FLAGS
ms.date: 03/30/2017
api_name:
- COR_PRF_MODULE_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MODULE_FLAGS
helpviewer_keywords:
- COR_PRF_MODULE_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 7bc3a938-0df1-4739-9ff1-89cff454b704
topic_type:
- apiref
ms.openlocfilehash: bdbf93ba4df50cf26538f0e527fdc3c982bb274e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447327"
---
# <a name="cor_prf_module_flags-enumeration"></a>Enumeração COR_PRF_MODULE_FLAGS
Especifica as propriedades de um módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum  
{  
    COR_PRF_MODULE_DISK             = 0x00000001,  
    COR_PRF_MODULE_NGEN             = 0x00000002,  
    COR_PRF_MODULE_DYNAMIC          = 0x00000004,  
    COR_PRF_MODULE_COLLECTIBLE      = 0x00000008,  
    COR_PRF_MODULE_RESOURCE         = 0x00000010,  
    COR_PRF_MODULE_FLAT_LAYOUT      = 0x00000020,  
    COR_PRF_MODULE_WINDOWS_RUNTIME  = 0x00000040  
}   COR_PRF_MODULE_FLAGS;  
```  
  
## <a name="members"></a>Membros  
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|COR_PRF_MODULE_DISK|O módulo foi carregado do disco.|  
|COR_PRF_MODULE_NGEN|O módulo foi gerado pelo gerador de imagem nativa (NGen. exe).|  
|COR_PRF_MODULE_DYNAMIC|O módulo foi criado por métodos no namespace <xref:System.Reflection.Emit?displayProperty=nameWithType>.|  
|COR_PRF_MODULE_COLLECTIBLE|O tempo de vida do módulo é gerenciado pelo coletor de lixo.|  
|COR_PRF_MODULE_RESOURCE|O módulo não contém metadados e é usado estritamente como um recurso. O equivalente gerenciado desse bit é o método <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType>.|  
|COR_PRF_MODULE_FLAT_LAYOUT|O layout do módulo na memória é simples, não mapeado. Se um módulo tiver esse conjunto de bits, os infileres que lêem informações diretamente do cabeçalho do arquivo executável portátil (PE) precisarão ser cuidadosos ao interpretar RVAs (endereços virtuais relativos) no cabeçalho.|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|O sinalizador de tipo de conteúdo Windows Runtime é definido nos metadados para o assembly do módulo. Esse é o caso para todos os módulos de metadados do Windows (. winmd).|  
  
## <a name="remarks"></a>Comentários  
 Bits de COR_PRF_MODULE_FLAGS são retornados para o criador de perfil no parâmetro de saída `pdwModuleFlags` do método [ICorProfilerInfo3:: GetModuleInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md) . Algumas combinações de dois ou mais sinalizadores são possíveis, mas nem todas as combinações são possíveis.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Criando perfil de enumerações](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
