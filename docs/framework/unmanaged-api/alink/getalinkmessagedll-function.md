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
ms.openlocfilehash: edd83e62b08aa7892c01577cd8c46f9d965c0894
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163014"
---
# <a name="getalinkmessagedll-function"></a>Função GetALinkMessageDll
Localiza e carrega a DLL da mensagem. Retorna 0 se a DLL da mensagem não pode ser localizado ou carregado. A DLL de mensagem deve ser em um subdiretório, cujo nome é uma ID de idioma ou no diretório atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** alink.h  
  
 **Biblioteca**: ALink  
  
## <a name="see-also"></a>Consulte também

- [Al.exe (Assembly Linker)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
