---
title: Método ICorDebugAppDomain::GetName
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type:
- apiref
ms.openlocfilehash: 2c9aa6792885c685195049948a540453b1f5235e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110303"
---
# <a name="icordebugappdomaingetname-method"></a>Método ICorDebugAppDomain::GetName
Obtém o nome do domínio do aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cchName`  
 no O tamanho da matriz de `szName`. Defina esse valor como zero para colocar esse método no modo de consulta.  
  
 `pcchName`  
 fora Um ponteiro para o tamanho do nome ou o número de caracteres realmente retornados em `szName`. No modo de consulta, esse valor permite que o chamador saiba quanto tamanho um buffer deve ser alocado para o nome.  
  
 `szName`  
 fora Uma matriz que armazena o nome do domínio do aplicativo.  
  
## <a name="remarks"></a>Comentários  
 Um depurador chama o método `GetName` uma vez para obter o tamanho de um buffer necessário para o nome. O depurador aloca o buffer e, em seguida, chama o método uma segunda vez para preencher o buffer. A primeira chamada, para obter o tamanho do nome, é referida como modo de *consulta*.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
