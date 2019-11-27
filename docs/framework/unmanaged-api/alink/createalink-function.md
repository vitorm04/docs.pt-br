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
ms.openlocfilehash: 9165a4db7e65fb0f409a902b06d32e9c2988aa69
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446545"
---
# <a name="createalink-function"></a>Função CreateALink
Cria uma instância do vinculador de assembly e define um ponteiro para a interface especificada.  
  
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
|`riid`|O nome físico de uma das interfaces do vinculador de assembly.|  
|`ppInterface`|O local em que a conclusão bem-sucedida contém um ponteiro para a interface `riid`.|  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Biblioteca**: Alink. dll  
  
## <a name="see-also"></a>Consulte também

- [Al.exe (Assembly Linker)](../../tools/al-exe-assembly-linker.md)
