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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 535d94688d02a7315529d17fae555fba457bbb86
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737876"
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
 [in] O tamanho do `szName` matriz. Defina esse valor como zero para colocar esse método no modo de consulta.  
  
 `pcchName`  
 [out] Um ponteiro para o tamanho do nome ou o número de caracteres retornado de fato no `szName`. No modo de consulta, esse valor permite que o chamador saiba quão grande um buffer para alocar para o nome.  
  
 `szName`  
 [out] Uma matriz que armazena o nome do domínio do aplicativo.  
  
## <a name="remarks"></a>Comentários  
 Um depurador chama o `GetName` método uma vez para obter o tamanho de um buffer necessário para o nome. O depurador aloca o buffer e, em seguida, chama o método uma segunda vez para preencher o buffer. A primeira chamada para obter o tamanho do nome, é conhecida como *modo de consulta*.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
