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
ms.openlocfilehash: 83468e13e1e028b031c31791910c4dd2d792f232
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168760"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a>Método ICorProfilerInfo::GetAppDomainInfo
Aceita uma ID de domínio do aplicativo. Retorna um nome de domínio do aplicativo e a ID do processo que o contém.  
  
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
  
## <a name="parameters"></a>Parâmetros  
 `appDomainId`  
 [in] A ID do domínio do aplicativo.  
  
 `cchName`  
 [in] O comprimento, em caracteres, da `szName` buffer de retorno.  
  
 `pcchName`  
 [out] Um ponteiro para o total de caracteres do nome de domínio do aplicativo.  
  
 `szName`  
 [out] Um buffer de caractere largo fornecido pelo chamador. Quando o método retorna, `szName` conterá o nome de domínio do aplicativo completo ou parcial.  
  
 `pProcessId`  
 [out] Um ponteiro para a ID do processo que contém o domínio do aplicativo.  
  
## <a name="remarks"></a>Comentários  
 Após esse método retornar, você deve verificar se o `szName` buffer era grande o suficiente para conter o nome completo do domínio do aplicativo. Para fazer isso, o valor de comparação que `pcchName` aponta para com o valor da `cchName` parâmetro. Se `pcchName` aponta para um valor maior que `cchName`, alocar uma maior `szName` buffer, atualize `cchName` com o novo e maior tamanho e a chamada `GetAppDomainInfo` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetAppDomainInfo` com um comprimento de zero `szName` buffer para obter o tamanho do buffer correto. Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcchName` e chamar `GetAppDomainInfo` novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Criação de perfil de interfaces](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
