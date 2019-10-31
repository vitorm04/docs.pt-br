---
title: Método ICorPublish::EnumProcesses
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
ms.openlocfilehash: 5f0dd814ad5adfa1b0dd7199530a3f993634a548
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121791"
---
# <a name="icorpublishenumprocesses-method"></a>Método ICorPublish::EnumProcesses
Obtém um enumerador para os processos gerenciados em execução neste computador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `Type`  
 Um valor da enumeração [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) que especifica o tipo de processo a ser recuperado. Na versão atual, somente COR_PUB_MANAGEDONLY é válido.  
  
 `ppIEnum`  
 Um ponteiro para o endereço de uma instância de [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) que é o enumerador dos processos.  
  
## <a name="remarks"></a>Comentários  
 A coleção de processos do enumerador é baseada em um instantâneo dos processos que estão em execução quando o método de `EnumProcesses` é chamado. O enumerador não incluirá nenhum processo que seja encerrado antes ou iniciado depois que `EnumProcesses` for chamado.  
  
 O método `EnumProcesses` pode ser chamado mais de uma vez nesta instância de [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) para criar uma nova coleção atualizada de processos. As coleções existentes não serão afetadas pelas chamadas subsequentes do método `EnumProcesses`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub. idl, CorPub. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
