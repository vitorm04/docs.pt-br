---
title: Método ResolveTypeLib
ms.date: 03/30/2017
api_name:
- ResolveTypeLib
api_location:
- tlbref.dll
f1_keywords:
- ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d734f35b5878ec39e4f2159c326283d168e3be2b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040840"
---
# <a name="resolvetypelib-method"></a>Método ResolveTypeLib
Resolve o nome simples de uma biblioteca de tipos, retornando seu caminho totalmente qualificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `bstrSimpleName`  
 [in] Um [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) que contém o nome simple da biblioteca de tipos.  
  
 `tlbid`  
 [in] O GUID atribuído à biblioteca de tipos no registro.  
  
 `lcid`  
 [in] A ID de localização da biblioteca de tipos.  
  
 `wMajorVersion`  
 [in] O número de versão principal da biblioteca de tipos. Por exemplo, para versão *x. y*, o número de versão principal é *x*.  
  
 `wMinorVersion`  
 [in] O número de versão secundária da biblioteca de tipos. Por exemplo, para versão *x. y*, é o número de versão secundária *y*.  
  
 `syskind`  
 [in] Um [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) sinalizador que identifica o ambiente operacional. Os valores comuns são SYS_WIN32 e SYS_WIN64.  
  
 `pbstrResolvedTlbName`  
 [out] Um ponteiro para um [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) que contém o caminho completo da biblioteca de tipos nomeado no `bstrSimpleName` parâmetro.  
  
## <a name="remarks"></a>Comentários  
 O `ResolveTypeLib` método é chamado pelo [função LoadTypeLibWithResolver](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) durante [Tlbexp.exe (exportador da biblioteca)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) de processamento.  
  
 As implementações personalizadas dessa interface devem retornar um [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) que contém o caminho completo da biblioteca de tipos nomeado no `bstrSimpleName` parâmetro.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** TlbRef.idl, TlbRef.h  
  
 **Biblioteca:** TlbRef.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Funções auxiliares do Tlbexp](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [LoadTypeLibEx](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
