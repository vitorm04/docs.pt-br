---
title: Método ICorProfilerInfo3::GetRuntimeInformation
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67e1d20f7faf38fa37083f1a5b1cc0c1060b7a32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a>Método ICorProfilerInfo3::GetRuntimeInformation
Fornece informações de versão sobre o common language runtime (CLR) que está sendo analisado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pClrInstanceId`  
 [out] A ID do representante de uma instância do CLR em execução em um processo. Isso é o mesmo que o `ClrInstanceID` que informa que o rastreamento de eventos do evento de inicialização do Windows (ETW).  
  
 `pRuntimeType`  
 [out] O tipo de tempo de execução. Este parâmetro retorna `COR_PRF_DESKTOP_CLR` para a versão da área de trabalho do CLR, ou `COR_PRF_CORE_CLR` para a versão principal do CLR usado no Silverlight.  
  
 `pMajorVersion`  
 [out] O número de versão principal do CLR.  
  
 `pMinorVersion`  
 [out] O número de versão secundária do CLR.  
  
 `pBuildVersion`  
 [out] O número de versão de compilação do CLR.  
  
 `pQFEVersion`  
 [out] O número de versão do CLR que está associado uma atualização de software.  
  
 `cchVersionString`  
 [in] O comprimento, em caracteres, do buffer que `szVersionString` aponta para.  
  
 `pcchVersionString`  
 [out] O comprimento, em caracteres, de `szVersionString`.  
  
 `szVersionString`  
 [out] A cadeia de caracteres de versão do CLR.  
  
## <a name="remarks"></a>Comentários  
 Você pode passar null para qualquer parâmetro. No entanto, `pcchVersionString` não pode ser nulo, a menos que `szVersionString` também será null.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
