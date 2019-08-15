---
title: Função GetTypeLibInfo
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7da0986269189ba5c2dfa0f10d509bf51deb446d
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040202"
---
# <a name="gettypelibinfo-function"></a>Função GetTypeLibInfo
Retorna informações sobre a biblioteca de tipos especificada examinando sua estrutura [TLIBATTR](https://docs.microsoft.com/windows/win32/api/oaidl/ns-oaidl-tlibattr) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `szFile`  
 no O nome do arquivo da biblioteca de tipos.  
  
 `pTypeLibID`  
 fora O GUID da biblioteca de tipos.  
  
 `pTypeLibLCID`  
 fora A ID da localização da biblioteca de tipos.  
  
 `pTypeLibPlatform`  
 fora Um sinalizador [SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) que identifica o sistema operacional de destino para a biblioteca de tipos. Os valores comuns são SYS_WIN32 e SYS_WIN64.  
  
 `pTypeLibMajorVer`  
 fora O número de versão principal da biblioteca de tipos. Por exemplo, para a versão *x. y*, o número de versão principal é *x*.  
  
 `pTypeLibMinorVer`  
 fora O número de versão secundária da biblioteca de tipos. Por exemplo, para a versão *x. y*, o número de versão secundária é *y*.  
  
## <a name="remarks"></a>Comentários  
 A `GetTypeLibInfo` função é chamada pelo [Tlbexp. exe (tipo de exportador da biblioteca de tipos)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md). Essa ferramenta gera uma biblioteca de tipos que descreve os tipos em um assembly Common Language Runtime (CLR).  
  
 Se qualquer parâmetro for nulo, a função retornará um `HRESULT` de `E_POINTER`. Caso contrário, retornará `S_OK`.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** TlbRef.h  
  
 **Biblioteca** TlbRef.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Funções auxiliares do Tlbexp](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [Função LoadTypeLibEx](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
