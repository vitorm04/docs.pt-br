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
ms.openlocfilehash: 24f7e2d5a547b78ceb4808feaf581c6f49807cf7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787622"
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
|`ppInterface`|O local em que a conclusão bem-sucedida contém um ponteiro para `riid` a interface.|  
  
## <a name="requirements"></a>Requisitos  
 **Biblioteca**: Alink. dll  
  
## <a name="see-also"></a>Consulte também

- [Al.exe (Assembly Linker)](../../tools/al-exe-assembly-linker.md)
