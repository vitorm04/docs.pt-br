---
title: "Enumeração COR_PRF_MODULE_FLAGS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 727816a674d2357c8a9ba1f19679c57669e92f50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
|COR_PRF_MODULE_DYNAMIC|O módulo foi criado por métodos de <xref:System.Reflection.Emit?displayProperty=nameWithType> namespace.|  
|COR_PRF_MODULE_COLLECTIBLE|Tempo de vida do módulo é gerenciado pelo coletor de lixo.|  
|COR_PRF_MODULE_RESOURCE|O módulo não contém nenhum metadado e é usado unicamente como um recurso. O equivalente gerenciado esse bit é o <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType> método.|  
|COR_PRF_MODULE_FLAT_LAYOUT|Layout do módulo na memória é simples, não mapeado. Se um módulo tiver esse bit definido, criadores de perfil que leia informações diretamente no cabeçalho do arquivo executável (PE) portátil precisará ter cuidado ao interpretar endereços virtuais relativos (RVAs) no cabeçalho.|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|O sinalizador de tipo de conteúdo de tempo de execução do Windows está definido nos metadados para esse assembly de módulos. Esse é o caso para todos os módulos de metadados do Windows (. winmd).|  
  
## <a name="remarks"></a>Comentários  
 Bits de COR_PRF_MODULE_FLAGS são retornados para o criador de perfil no `pdwModuleFlags` parâmetro de saída a [ICorProfilerInfo3::GetModuleInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md) método. Algumas combinações de duas ou mais sinalizadores são possíveis, mas nem todas as combinações são possíveis.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Criando perfil de enumerações](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
