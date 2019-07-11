---
title: Função CreateALink
ms.date: 03/30/2017
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 993848711f41c9e03b969a3c611982a5c8bc860d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742212"
---
# <a name="createalink-function"></a>Função CreateALink
Cria uma instância do vinculador de Assembly e define um ponteiro para a interface especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`riid`|O nome físico de uma das interfaces de vinculador de Assembly.|  
|`ppInterface`|O local que contém um ponteiro para a conclusão bem-sucedida de `riid` interface.|  
  
## <a name="requirements"></a>Requisitos  
 **Biblioteca**: ALink  
  
## <a name="see-also"></a>Consulte também

- [Al.exe (Assembly Linker)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
