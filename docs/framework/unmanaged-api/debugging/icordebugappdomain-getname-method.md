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
ms.openlocfilehash: 84f895e749fc8f2520dbce3caf9e6c11fda78a7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugappdomaingetname-method"></a>Método ICorDebugAppDomain::GetName
Obtém o nome do domínio do aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cchName`  
 [in] O tamanho do `szName` matriz. Defina esse valor como zero para colocar esse método no modo de consulta.  
  
 `pcchName`  
 [out] Um ponteiro para o tamanho do nome ou o número de caracteres de fato retornadas em `szName`. No modo de consulta, esse valor permite que o chamador saiba grande como um buffer para alocar para o nome.  
  
 `szName`  
 [out] Uma matriz que armazena o nome do domínio do aplicativo.  
  
## <a name="remarks"></a>Comentários  
 Um depurador chama o `GetName` método uma vez para obter o tamanho de um buffer necessário para o nome. O depurador aloca o buffer e, em seguida, chama o método uma segunda vez para preencher o buffer. A primeira chamada para obter o tamanho do nome é conhecida como *o modo de consulta*.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
