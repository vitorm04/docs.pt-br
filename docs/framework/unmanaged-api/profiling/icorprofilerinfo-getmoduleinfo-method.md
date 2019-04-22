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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69db53c03d68e30507ff3ab2b11b663970d59af0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090804"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a>Método ICorProfilerInfo::GetModuleInfo
Dado um ID de módulo, retorna o nome do arquivo do módulo e a ID do assembly do pai do módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
 [in] A ID do módulo para o qual as informações serão recuperadas.  
  
 `ppBaseLoadAddress`  
 [out] O endereço básico no qual o módulo é carregado.  
  
 `cchName`  
 [in] O comprimento, em caracteres, da `szName` buffer de retorno.  
  
 `pcchName`  
 [out] Um ponteiro para o total de caracteres do nome de arquivo do módulo que é retornado.  
  
 `szName`  
 [out] Um buffer de caractere largo fornecido pelo chamador. Quando o método retorna, esse buffer contém o nome do arquivo do módulo.  
  
 `pAssemblyId`  
 [out] Um ponteiro para a ID do assembly do pai do módulo.  
  
## <a name="remarks"></a>Comentários  
 Para módulos dinâmicos, o `szName` parâmetro é uma cadeia de caracteres vazia, e o endereço básico é 0 (zero).  
  
 Embora o `GetModuleInfo` método pode ser chamado assim que a ID do módulo existe, a ID do assembly pai não estarão disponível até que o criador de perfil recebe as [ICorProfilerCallback:: Moduleattachedtoassembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) retorno de chamada.  
  
 Quando `GetModuleInfo` é retornado, você deve verificar se o `szName` buffer era grande o suficiente para conter o nome completo do arquivo do módulo. Para fazer isso, o valor de comparação que `pcchName` aponta para com o valor da `cchName` parâmetro. Se `pcchName` aponta para um valor maior que `cchName`, alocar uma maior `szName` buffer, atualize `cchName` com o novo e maior tamanho e a chamada `GetModuleInfo` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetModuleInfo` com um comprimento de zero `szName` buffer para obter o tamanho do buffer correto. Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcchName` e chamar `GetModuleInfo` novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
- [Método GetModuleInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
