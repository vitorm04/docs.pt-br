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
ms.openlocfilehash: 11117db08d58684cc854400424d1836ec35b8c12
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497997"
---
# <a name="createalink-function"></a>Função CreateALink
Cria uma instância do vinculador de Assembly e define um ponteiro para a interface especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
