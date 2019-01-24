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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad04e90d1855e2de89aa6515bf16424de95ffa26
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696432"
---
# <a name="corprfmoduleflags-enumeration"></a>Enumeração COR_PRF_MODULE_FLAGS
Especifica as propriedades de um módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
  
|Membro|Descrição|  
|------------|-----------------|  
|COR_PRF_MODULE_DISK|O módulo foi carregado do disco.|  
|COR_PRF_MODULE_NGEN|O módulo foi gerado pelo gerador de imagem nativa (Ngen.exe).|  
|COR_PRF_MODULE_DYNAMIC|O módulo foi criado por métodos no <xref:System.Reflection.Emit?displayProperty=nameWithType> namespace.|  
|COR_PRF_MODULE_COLLECTIBLE|Tempo de vida do módulo é gerenciado pelo coletor de lixo.|  
|COR_PRF_MODULE_RESOURCE|O módulo não contém nenhum metadado e é usado estritamente como um recurso. O equivalente gerenciado esse bit é o <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType> método.|  
|COR_PRF_MODULE_FLAT_LAYOUT|Layout do módulo na memória é simples, não mapeada. Se um módulo tiver esse bit definido, os criadores de perfil que leem informações diretamente do cabeçalho de arquivo executável (PE) de portátil serão preciso ter cuidado ao interpretar endereços virtuais (relacionados RVAs) no cabeçalho.|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|O sinalizador de tipo de conteúdo de tempo de execução do Windows é definido nos metadados para esse assembly de módulos. Esse é o caso para todos os módulos de metadados do Windows (. winmd).|  
  
## <a name="remarks"></a>Comentários  
 Bits de COR_PRF_MODULE_FLAGS são retornados para o criador de perfil na `pdwModuleFlags` parâmetro de saída a [ICorProfilerInfo3::GetModuleInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md) método. Algumas combinações de duas ou mais sinalizadores são possíveis, mas nem todas as combinações são possíveis.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Criando perfil de enumerações](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
