---
title: Método ICorProfilerInfo::GetAppDomainInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAppDomainInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af83fbeb64ad33910b45d49f987ffae130a2179e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455377"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a>Método ICorProfilerInfo::GetAppDomainInfo
Aceita uma ID de domínio de aplicativo. Retorna um nome de domínio de aplicativo e a ID do processo que o contém.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `appDomainId`  
 [in] A ID do domínio do aplicativo.  
  
 `cchName`  
 [in] O comprimento, em caracteres, do `szName` buffer de retorno.  
  
 `pcchName`  
 [out] Um ponteiro para o total de caracteres do nome de domínio do aplicativo.  
  
 `szName`  
 [out] Um buffer de caractere largo fornecida pelo chamador. Quando o método retorna, `szName` conterá o nome de domínio de aplicativo completo ou parcial.  
  
 `pProcessId`  
 [out] Um ponteiro para a ID do processo que contém o domínio de aplicativo.  
  
## <a name="remarks"></a>Comentários  
 Depois que este método retorna, você deve verificar se o `szName` buffer era grande o suficiente para conter o nome completo do domínio do aplicativo. Para fazer isso, o valor de comparação que `pcchName` aponta para com o valor de `cchName` parâmetro. Se `pcchName` aponta para um valor que é maior do que `cchName`, alocar uma maior `szName` buffer, atualize `cchName` com o novo tamanho maior e chame `GetAppDomainInfo` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetAppDomainInfo` com um comprimento zero `szName` buffer para obter o tamanho do buffer correto. Você pode definir o tamanho do buffer para o valor retornado em `pcchName` e chame `GetAppDomainInfo` novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
