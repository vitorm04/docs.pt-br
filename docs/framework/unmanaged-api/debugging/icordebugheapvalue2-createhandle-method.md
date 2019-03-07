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
ms.openlocfilehash: 078dfd7162c250f0279b8bc372aeb39662aa0119
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498530"
---
# <a name="icordebugheapvalue2createhandle-method"></a>Método ICorDebugHeapValue2::CreateHandle
Cria um identificador do tipo especificado para o valor de heap representado por esse objeto ICorDebugHeapValue2.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `type`  
 [in] Um valor de enumeração CorDebugHandleType que especifica o tipo de identificador a ser criado.  
  
 `ppHandle`  
 [out] Um ponteiro para o endereço de um objeto ICorDebugHandleValue que representa o novo identificador para esse valor de heap.  
  
## <a name="remarks"></a>Comentários  
 O identificador será criado no domínio do aplicativo que está associado com o valor de heap e se tornará inválido caso se o domínio do aplicativo seja descarregado.  
  
 Várias chamadas para essa função para o mesmo valor de heap criará vários identificadores. Como identificadores de afetam o desempenho do coletor de lixo, o depurador deve se limitar a um número relativamente pequeno de identificadores (cerca de 256) que estão ativos por vez.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
