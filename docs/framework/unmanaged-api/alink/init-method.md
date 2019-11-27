---
title: Método Init
ms.date: 03/30/2017
api_name:
- IALink.Init
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- Init
helpviewer_keywords:
- Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type:
- apiref
ms.openlocfilehash: 986ae69e7ebb8f607be5d37fab426bcc787abb26
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445647"
---
# <a name="init-method"></a>Método Init
Prepara objetos que implementam a [interface IALink](ialink-interface.md) para uso.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pDispenser`  
 Ponteiro de [interface IMetaDataDispenserEx](../metadata/imetadatadispenserex-interface.md) para o dispensador de metadados.  
  
 `pErrorHandler`  
 Ponteiro de [interface IMetaDataError](../metadata/imetadataerror-interface.md) para uma interface de tratamento de erro opcional.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna S_OK se o método tiver sucesso.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 Requer ALink. h  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink](ialink-interface.md)
- [Interface IALink2](ialink2-interface.md)
- [API do ALink](index.md)
