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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 323e53c45a26d5703548ebe9863978f6d3929f0b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787461"
---
# <a name="getalinkmessagedll-function"></a>Função GetALinkMessageDll
Localiza e carrega a DLL de mensagem. Retornará 0 se a DLL de mensagem não puder ser localizada ou carregada. A DLL de mensagem deve estar em um subdiretório cujo nome é uma ID de idioma ou no diretório atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** ALink. h  
  
 **Biblioteca**: Alink. dll  
  
## <a name="see-also"></a>Consulte também

- [Al.exe (Assembly Linker)](../../tools/al-exe-assembly-linker.md)
