---
title: Função CoEEShutDownCOM
ms.date: 03/30/2017
api_name:
- CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoEEShutDownCOM
helpviewer_keywords:
- CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ddef35b1b707cc5c962402e880923dca7d4d9d6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59208144"
---
# <a name="coeeshutdowncom-function"></a>Função CoEEShutDownCOM
Força o common language runtime (CLR) para liberar todos os ponteiros de interface, que ele mantém dentro do runtime callable wrappers (RCW). Isso tem o efeito de liberar todos os caches RCW. Essa função global foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Em vez disso, use o ponto de entrada para um tempo de execução específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>Comentários  
 O `CoEEShutDownCOM` função primeiro libera todos os RCWs em todos os contextos e em todos os caches e, em seguida, remove qualquer notificação de desmontagem existente na instalação. Nenhuma DLL descarregando ocorre.  
  
> [!CAUTION]
>  Esta função afeta todos os tempos de execução que são carregados no processo.  
  
 Começando com o [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], chamar o ponto de entrada para esta função em que o tempo de execução específico que você deseja afetar. Para obter o ponto de entrada, chame o [iclrruntimeinfo:: GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) método e especificar "CoEEShutDownCOM".  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Funções estáticas globais de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
