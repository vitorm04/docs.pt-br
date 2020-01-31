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
ms.openlocfilehash: 5f785b22a3fbda6403c124ec70757b16f5335907
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790763"
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
 Um valor da enumeração de [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) que especifica o tipo de processo a ser recuperado. Na versão atual, somente COR_PUB_MANAGEDONLY é válida.  
  
 `ppIEnum`  
 Um ponteiro para o endereço de uma instância de [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) que é o enumerador dos processos.  
  
## <a name="remarks"></a>Comentários  
 A coleção de processos do enumerador é baseada em um instantâneo dos processos que estão em execução quando o método de `EnumProcesses` é chamado. O enumerador não incluirá nenhum processo que seja encerrado antes ou iniciado depois que `EnumProcesses` for chamado.  
  
 O método `EnumProcesses` pode ser chamado mais de uma vez nesta instância de [ICorPublish](icorpublish-interface.md) para criar uma nova coleção atualizada de processos. As coleções existentes não serão afetadas pelas chamadas subsequentes do método `EnumProcesses`.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorPub. idl, CorPub. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorPublish](icorpublish-interface.md)
