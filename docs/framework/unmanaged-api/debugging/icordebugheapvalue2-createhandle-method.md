---
title: Método ICorDebugHeapValue2::CreateHandle
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c69d1f83a4591df4d2dcb7fb9724fa582ea28387
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413573"
---
# <a name="icordebugheapvalue2createhandle-method"></a>Método ICorDebugHeapValue2::CreateHandle
Cria um identificador do tipo especificado para o valor de heap representado por esse objeto em ICorDebugHeapValue2.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `type`  
 [in] Um valor da enumeração CorDebugHandleType que especifica o tipo de identificador a ser criado.  
  
 `ppHandle`  
 [out] Um ponteiro para o endereço de um objeto ICorDebugHandleValue que representa o novo identificador para esse valor de heap.  
  
## <a name="remarks"></a>Comentários  
 O identificador será criado no domínio do aplicativo que está associado com o valor de heap e se tornarão inválido se o domínio de aplicativo seja descarregado.  
  
 Várias chamadas a essa função para o mesmo valor de heap criará vários identificadores. Identificadores de afetam o desempenho do coletor de lixo, o depurador deve limitar automaticamente para um número relativamente pequeno de identificadores (aproximadamente 256) que estão ativos por vez.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
