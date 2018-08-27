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
ms.openlocfilehash: 0ec28c581b8e6e0aff3a2765720b6e9795be931b
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931698"
---
# <a name="gettypelibinfo-function"></a>Função GetTypeLibInfo
Retorna informações sobre a biblioteca de tipos especificada, examinando sua [TLIBATTR](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagtlibattr) estrutura.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `szFile`  
 [in] O nome do arquivo da biblioteca de tipos.  
  
 `pTypeLibID`  
 [out] O GUID da biblioteca de tipos.  
  
 `pTypeLibLCID`  
 [out] A ID de localização da biblioteca de tipos.  
  
 `pTypeLibPlatform`  
 [out] Um [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) sinalizador que identifica o sistema operacional de destino para a biblioteca de tipos. Os valores comuns são SYS_WIN32 e SYS_WIN64.  
  
 `pTypeLibMajorVer`  
 [out] O número de versão principal da biblioteca de tipos. Por exemplo, para versão *x. y*, o número de versão principal é *x*.  
  
 `pTypeLibMinorVer`  
 [out] O número de versão secundária da biblioteca de tipos. Por exemplo, para versão *x. y*, é o número de versão secundária *y*.  
  
## <a name="remarks"></a>Comentários  
 O `GetTypeLibInfo` função é chamada pela [Tlbexp.exe (exportador da biblioteca)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md). Essa ferramenta gera uma biblioteca de tipos que descreve os tipos em um assembly do common language runtime (CLR).  
  
 Se nenhum parâmetro for nulo, a função retorna um `HRESULT` de `E_POINTER`. Caso contrário, retornará `S_OK`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** TlbRef.h  
  
 **Biblioteca:** TlbRef.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Funções auxiliares do Tlbexp](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [Função LoadTypeLibEx](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
