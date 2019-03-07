---
title: Método ICorProfilerInfo3::GetModuleInfo2
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 188517104d4163ad1b391c2bab3bc41a2697e63d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478070"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a>Método ICorProfilerInfo3::GetModuleInfo2
Dado um ID de módulo, retorna o nome do arquivo do módulo, a ID do pai do módulo de assembly e um bitmask que descreve as propriedades do módulo.  
  
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
  
 `pdwModuleFlags`  
 [out] Um bitmask de valores da [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) enumeração que especificam as propriedades do módulo.  
  
## <a name="remarks"></a>Comentários  
 Para módulos dinâmicos, o `szName` parâmetro é o nome de metadados do módulo e o endereço básico é 0 (zero). O nome de metadados é o valor na coluna Nome da tabela de módulo dentro de metadados. Isso também é exposto como o <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> propriedade para o código gerenciado e como o `szName` parâmetro do [imetadataimport:: Getscopeprops](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) método ao código de cliente de metadados não gerenciados.  
  
 Embora o `GetModuleInfo2` método pode ser chamado assim que a ID do módulo existe, a ID do assembly pai não estarão disponível até que o criador de perfil recebe as [ICorProfilerCallback:: Moduleattachedtoassembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) retorno de chamada.  
  
 Quando `GetModuleInfo2` é retornado, você deve verificar se o `szName` buffer era grande o suficiente para conter o nome completo do arquivo do módulo. Para fazer isso, o valor de comparação que `pcchName` aponta para com o valor da `cchName` parâmetro. Se `pcchName` aponta para um valor maior que `cchName`, alocar uma maior `szName` buffer, atualize `cchName` com o novo e maior tamanho e a chamada `GetModuleInfo2` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetModuleInfo2` com um comprimento de zero `szName` buffer para obter o tamanho do buffer correto. Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcchName` e chamar `GetModuleInfo2` novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
