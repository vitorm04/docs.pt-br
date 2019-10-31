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
ms.openlocfilehash: 4e85a9a98bf0550fa906f8b905c73890948f4ac1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124934"
---
# <a name="coeeshutdowncom-function"></a>Função CoEEShutDownCOM
Força o Common Language Runtime (CLR) a liberar todos os ponteiros de interface que ele mantém dentro de RCW (Runtime Callable Wrappers). Isso tem o efeito de liberar todos os caches de RCW. Essa função global foi preterida no .NET Framework 4. Em vez disso, use o ponto de entrada para um tempo de execução específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>Comentários  
 A função `CoEEShutDownCOM` primeiro libera todos os RCWs em todos os contextos e em todos os caches e, em seguida, remove qualquer notificação de subdivisão existente na instalação. Nenhum descarregamento de DLL ocorre.  
  
> [!CAUTION]
> Essa função afeta todos os tempos de execução que são carregados no processo.  
  
 Começando com o .NET Framework 4, chame o ponto de entrada para essa função no tempo de execução específico que você deseja afetar. Para obter o ponto de entrada, chame o método [ICLRRuntimeInfo:: GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) e especifique "CoEEShutDownCOM".  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Funções estáticas globais de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
