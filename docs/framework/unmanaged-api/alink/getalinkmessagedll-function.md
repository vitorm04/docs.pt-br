---
title: Função GetALinkMessageDll
ms.date: 03/30/2017
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
ms.openlocfilehash: 63719d0c6e13768e9dc7ed80e52e2a293e32a8a1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449346"
---
# <a name="getalinkmessagedll-function"></a>Função GetALinkMessageDll
Localiza e carrega a DLL de mensagem. Retornará 0 se a DLL de mensagem não puder ser localizada ou carregada. A DLL de mensagem deve estar em um subdiretório cujo nome é uma ID de idioma ou no diretório atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Cabeçalho:** ALink. h  
  
 **Biblioteca**: Alink. dll  
  
## <a name="see-also"></a>Consulte também

- [Al.exe (Assembly Linker)](../../tools/al-exe-assembly-linker.md)
