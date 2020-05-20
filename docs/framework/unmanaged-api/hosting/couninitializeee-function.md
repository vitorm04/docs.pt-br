---
title: Função CoUninitializeEE
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
ms.openlocfilehash: fa6297e926d53c02bb0d1af7b59b45b8ee152399
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616457"
---
# <a name="couninitializeee-function"></a>Função CoUninitializeEE
`CoUninitializeEE`é obsoleto e não fornece nenhuma funcionalidade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a>Comentários  
 O mecanismo de execução de Common Language Runtime não pode ser descarregado de um processo. Para desligar a chamada do mecanismo de execução [CorExitProcess](corexitprocess-function.md).  
  
## <a name="see-also"></a>Veja também

- [Função CoInitializeEE](coinitializeee-function.md)
- [Funções estáticas globais de metadados](../metadata/metadata-global-static-functions.md)
