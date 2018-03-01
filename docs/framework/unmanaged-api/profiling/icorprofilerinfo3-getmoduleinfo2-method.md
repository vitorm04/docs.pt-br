---
title: "Método ICorProfilerInfo3::GetModuleInfo2"
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
- ICorProfilerInfo3.GetModuleInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetModuleInfo2
helpviewer_keywords:
- ICorProfilerInfo3::GetModuleInfo2 method [.NET Framework profiling]
- GetModuleInfo2 method [.NET Framework profiling]
ms.assetid: f1f6b8f3-dcfc-49e8-be76-ea50ea90d5a7
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 325db939c692a5dc7740e6cf813644ebffe9fc12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a>Método ICorProfilerInfo3::GetModuleInfo2
Especificado um ID de módulo, retorna o nome do arquivo do módulo, a ID do pai do módulo assembly e uma máscara de bits que descreve as propriedades do módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetModuleInfo2(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, annotation("__out_ecount_part(cchName, *pcchName)")]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
    [out] DWORD                 *pdwModuleFlags);  
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
  
 `pdwModuleFlags`  
 [out] Um bitmask de valores da [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) enumeração que especifica as propriedades do módulo.  
  
## <a name="remarks"></a>Comentários  
 Para módulos dinâmicos, o `szName` parâmetro é o nome de metadados do módulo e o endereço base for 0 (zero). O nome de metadados é o valor na coluna Nome da tabela de módulo dentro de metadados. Isso também é exposto como o <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> propriedade para código gerenciado e como o `szName` parâmetro o [: Getscopeprops](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) método ao código do cliente não gerenciado de metadados.  
  
 Embora o `GetModuleInfo2` método pode ser chamado como ID do módulo existe, a ID do assembly pai não estarão disponível até que o criador de perfil recebe o [: Moduleattachedtoassembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) retorno de chamada.  
  
 Quando `GetModuleInfo2` retorna, você deve verificar se o `szName` buffer era grande o suficiente para conter o nome completo do arquivo do módulo. Para fazer isso, o valor de comparação que `pcchName` aponta para com o valor de `cchName` parâmetro. Se `pcchName` aponta para um valor que é maior do que `cchName`, alocar uma maior `szName` buffer, atualize `cchName` com o novo tamanho maior e chame `GetModuleInfo2` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetModuleInfo2` com um comprimento zero `szName` buffer para obter o tamanho do buffer correto. Você pode definir o tamanho do buffer para o valor retornado em `pcchName` e chame `GetModuleInfo2` novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
