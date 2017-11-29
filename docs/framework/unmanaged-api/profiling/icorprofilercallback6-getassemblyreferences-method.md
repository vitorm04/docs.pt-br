---
title: "ICorProfilerCallback6::Método GetAssemblyReferences"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorProfilerCallback6.GetAssemblyReferences
api_location:
- mscorwks.dll
- corprof.idl
api_type: COM
ms.assetid: 8b391afb-d79f-41bd-94ce-43ce62c6b5fc
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3682f40c9c49ea15ac9f084b6d5db274bfcaa8d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a>ICorProfilerCallback6::Método GetAssemblyReferences
[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
 Notifica o criador de perfis de que um assembly está em um estágio inicial de carregamento, quando o Common Language Runtime realiza um exame de fechamento da referência do assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `wszAssemblyPath`  
 [in] O caminho e o nome do assembly cujos metadados serão modificados.  
  
 `pAsmRefProvider`  
 [in] Um ponteiro para o endereço de um [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) faz referência a interface que especifica o assembly para adicionar.  
  
## <a name="return-value"></a>Valor de retorno  
 Os valores retornados desse retorno de chamada são ignorados.  
  
## <a name="remarks"></a>Comentários  
 Esse retorno de chamada é controlado pela configuração de [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) sinalizador de máscara de evento ao chamar o [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) método. Se o criador de perfil registra o [Icorprofilercallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) método de retorno de chamada, o tempo de execução passa o caminho e o nome do assembly a ser carregado, junto com um ponteiro para um [ ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) o objeto de interface para esse método. O criador de perfil, em seguida, pode chamar o [Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) método com um `COR_PRF_ASSEMBLY_REFERENCE_INFO` objeto para cada assembly de destino, ela planeja fazer referência do assembly especificado no `GetAssemblyReferences` retorno de chamada.  
  
 Use o retorno de chamada `GetAssemblyReferences` apenas se for necessário ao criador de perfis modificar os metadados de um assembly para adicionar referências de assembly. (Mas observe que a modificação real de metadados de um assembly é feita na [: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)método de retorno de chamada.) O criador de perfis deve implementar o método de retorno de chamada `GetAssemblyReferences` para informar o tempo de execução de linguagem comum (CLR) que referências de assembly serão adicionadas quando o módulo estiver carregado.  Isso ajuda a garantir que decisões de compartilhamento de assembly tomadas pelo CLR durante esse estágio inicial permanecem válidas apesar de o criador de perfis planejar modificar as referências de metadados do assembly mais tarde.  Isso pode evitar algumas instâncias nas quais as modificações de metadados do criador de perfis causam um erro de `SECURITY_E_INCOMPATIBLE_SHARE`.  
  
 O criador de perfil usa a [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) objeto fornecido por esse método para adicionar referências de assembly para o movimentador de fechamento de referência de assembly CLR.  O [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) objeto deve ser usado apenas nesse retorno de chamada. Chamadas para o [Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) método desse retorno de chamada não resulta em metadados modificados, mas apenas em uma passagem de fechamento de referência de assembly modificado. O criador de perfil ainda terá que usar um [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) objeto explicitamente adicionar referências de assembly de dentro do [: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) retorno de chamada para a referência assembly, mesmo se ele implementa o `GetAssemblyReferences` retorno de chamada.  
  
 O criador de perfil deve estar preparado para receber chamadas duplicadas para esse retorno de chamada para o mesmo assembly e responder identicamente para cada chamada tal duplicada (fazendo o mesmo conjunto de [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) chamadas).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 [Método ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)  
 [Estrutura COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)  
 [Interface ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
