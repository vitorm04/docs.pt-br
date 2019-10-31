---
title: Função CreateInstallReferenceEnum
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
ms.openlocfilehash: f089769f854bad5d3e572e0307734e06e72ca89c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108560"
---
# <a name="createinstallreferenceenum-function"></a>Função CreateInstallReferenceEnum
Obtém um ponteiro para uma instância de [IInstallReferenceEnum](iinstallreferenceenum-interface.md) que representa uma lista de referências de um aplicativo para o assembly especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppRefEnum`  
 fora O ponteiro de `IInstallReferenceEnum` retornado.  
  
 `pName`  
 no O [IAssemblyName](iassemblyname-interface.md) que identifica o assembly para o qual enumerar referências.  
  
 `dwFlags`  
 no Sinalizadores que influenciam o comportamento do enumerador.  
  
 `pvReserved`  
 no Reservado para extensibilidade futura. `pvReserved` deve ser uma referência nula.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion. h  
  
 **Biblioteca:** Fusion. dll e mscorwks. dll. Use Fusion. dll em vez de mscorwks. dll para garantir que você direcione a versão correta do .NET Framework.  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IInstallReferenceEnum](iinstallreferenceenum-interface.md)
- [Interface IAssemblyName](iassemblyname-interface.md)
- [Funções estáticas globais de fusão](fusion-global-static-functions.md)
