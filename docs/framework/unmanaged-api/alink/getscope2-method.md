---
title: Método GetScope2
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a3c6b9e1239dc1baed9428d4fe967eb8274a9304
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206025"
---
# <a name="getscope2-method"></a>Método GetScope2
Obtém um escopo de importação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
## <a name="parameters"></a>Parâmetros  
 `AssemblyID`  
 ID do assembly de destino.  
  
 `FileToken`  
 ID do arquivo do qual importar.  
  
 `dwScope`  
 Escopo baseado em zero para importar.  
  
 `ppImportScope`  
 Recebe um ponteiro para [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface para escopo indicada.  
  
## <a name="return-value"></a>Valor de retorno  
 Se o método for bem-sucedido, retornará S_OK.  
  
## <a name="requirements"></a>Requisitos  
 Requer alink.h.  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink2](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [Interface IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [API do ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
