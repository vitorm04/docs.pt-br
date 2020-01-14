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
ms.openlocfilehash: f0f6fe321f4d38129b6d70ce94a7ea8de8fff6c8
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935665"
---
# <a name="resolvetypelib-method"></a>Método ResolveTypeLib
Resolve o nome simples de uma biblioteca de tipos retornando seu caminho totalmente qualificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
 no Um [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) que contém o nome simples da biblioteca de tipos.  
  
 `tlbid`  
 no O GUID atribuído à biblioteca de tipos no registro.  
  
 `lcid`  
 no A ID da localização da biblioteca de tipos.  
  
 `wMajorVersion`  
 no O número de versão principal da biblioteca de tipos. Por exemplo, para a versão *x. y*, o número de versão principal é *x*.  
  
 `wMinorVersion`  
 no O número de versão secundária da biblioteca de tipos. Por exemplo, para a versão *x. y*, o número de versão secundária é *y*.  
  
 `syskind`  
 no Um sinalizador [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) que identifica o ambiente operacional. Os valores comuns são SYS_WIN32 e SYS_WIN64.  
  
 `pbstrResolvedTlbName`  
 fora Um ponteiro para um [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) que contém o caminho completo da biblioteca de tipos denominada no parâmetro `bstrSimpleName`.  
  
## <a name="remarks"></a>Comentários  
 O método `ResolveTypeLib` é chamado pela [função LoadTypeLibWithResolver](loadtypelibwithresolver-function.md) durante o processamento de [Tlbexp. exe (tipo de exportador de biblioteca de tipos)](../../tools/tlbexp-exe-type-library-exporter.md) .  
  
 Implementações personalizadas dessa interface devem retornar um [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) que contém o caminho completo da biblioteca de tipos denominada no parâmetro `bstrSimpleName`.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** TlbRef. idl, TlbRef. h  
  
 **Biblioteca:** TlbRef. lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Funções auxiliares do Tlbexp](index.md)
- [LoadTypeLibEx](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
