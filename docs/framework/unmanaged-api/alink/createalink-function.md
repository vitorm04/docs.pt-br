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
ms.openlocfilehash: 1e29c9c246649229900beba2fcc9ab482071ae46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400660"
---
# <a name="createalink-function"></a>Função CreateALink
Cria uma instância de Assembly Linker e define um ponteiro para a interface especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`riid`|O nome físico de um Assembly Linker interfaces.|  
|`ppInterface`|O local que contém um ponteiro para após a conclusão bem-sucedida de `riid` interface.|  
  
## <a name="requirements"></a>Requisitos  
 **Biblioteca**: arquivo  
  
## <a name="see-also"></a>Consulte também  
 [Al.exe (Assembly Linker)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
