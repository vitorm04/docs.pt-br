---
title: Método ICorProfilerInfo::GetModuleInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type:
- apiref
ms.openlocfilehash: aae6d33166a7685e07c4d82f654f803600e37eec
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438896"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a>Método ICorProfilerInfo::GetModuleInfo
Dada uma ID de módulo, retorna o nome do arquivo do módulo e a ID do assembly pai do módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `moduleId`  
 no A ID do módulo para o qual as informações serão recuperadas.  
  
 `ppBaseLoadAddress`  
 fora O endereço base no qual o módulo é carregado.  
  
 `cchName`  
 no O comprimento, em caracteres, do `szName` buffer de retorno.  
  
 `pcchName`  
 fora Um ponteiro para o comprimento total do caractere do nome de arquivo do módulo que é retornado.  
  
 `szName`  
 fora Um buffer de caracteres largo fornecido pelo chamador. Quando o método retorna, esse buffer contém o nome do arquivo do módulo.  
  
 `pAssemblyId`  
 fora Um ponteiro para a ID do assembly pai do módulo.  
  
## <a name="remarks"></a>Comentários  
 Para módulos dinâmicos, o parâmetro `szName` é uma cadeia de caracteres vazia e o endereço base é 0 (zero).  
  
 Embora o método `GetModuleInfo` possa ser chamado assim que a ID do módulo existir, a ID do assembly pai não estará disponível até que o criador de perfil receba o retorno de chamada [ICorProfilerCallback:: ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) .  
  
 Quando `GetModuleInfo` retorna, você deve verificar se o buffer de `szName` era grande o suficiente para conter o nome de arquivo completo do módulo. Para fazer isso, compare o valor que `pcchName` aponta com o valor do parâmetro `cchName`. Se `pcchName` apontar para um valor maior que `cchName`, aloque um buffer de `szName` maior, atualize `cchName` com o tamanho novo, maior e chame `GetModuleInfo` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetModuleInfo` com um buffer de `szName` de comprimento zero para obter o tamanho de buffer correto. Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcchName` e chamar `GetModuleInfo` novamente.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
- [Método GetModuleInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
