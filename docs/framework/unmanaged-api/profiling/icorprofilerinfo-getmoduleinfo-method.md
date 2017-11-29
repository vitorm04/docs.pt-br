---
title: "Método ICorProfilerInfo::GetModuleInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetModuleInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 23dc0208b4537530f18c2c282fbe8c3495ba301f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a>Método ICorProfilerInfo::GetModuleInfo
Especificado um ID de módulo, retorna o nome do arquivo do módulo e a ID do assembly do pai do módulo.  
  
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
  
#### <a name="parameters"></a>Parâmetros  
 `moduleId`  
 [in] A ID do módulo para o qual as informações serão recuperadas.  
  
 `ppBaseLoadAddress`  
 [out] O endereço base no qual o módulo é carregado.  
  
 `cchName`  
 [in] O comprimento, em caracteres, do `szName` buffer de retorno.  
  
 `pcchName`  
 [out] Um ponteiro para o total de caracteres do nome de arquivo do módulo que é retornado.  
  
 `szName`  
 [out] Um buffer de caractere largo fornecida pelo chamador. Quando o método retorna, esse buffer contém o nome de arquivo do módulo.  
  
 `pAssemblyId`  
 [out] Um ponteiro para a ID do assembly do pai do módulo.  
  
## <a name="remarks"></a>Comentários  
 Para módulos dinâmicos, o `szName` parâmetro é uma cadeia de caracteres vazia, e o endereço base for 0 (zero).  
  
 Embora o `GetModuleInfo` método pode ser chamado como ID do módulo existe, a ID do assembly pai não estarão disponível até que o criador de perfil recebe o [: Moduleattachedtoassembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) retorno de chamada.  
  
 Quando `GetModuleInfo` retorna, você deve verificar se o `szName` buffer era grande o suficiente para conter o nome completo do arquivo do módulo. Para fazer isso, o valor de comparação que `pcchName` aponta para com o valor de `cchName` parâmetro. Se `pcchName` aponta para um valor que é maior do que `cchName`, alocar uma maior `szName` buffer, atualize `cchName` com o novo tamanho maior e chame `GetModuleInfo` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetModuleInfo` com um comprimento zero `szName` buffer para obter o tamanho do buffer correto. Você pode definir o tamanho do buffer para o valor retornado em `pcchName` e chame `GetModuleInfo` novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)  
 [Método GetModuleInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
