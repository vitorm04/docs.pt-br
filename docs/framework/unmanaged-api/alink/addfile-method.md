---
title: Método AddFile
ms.date: 03/30/2017
api_name:
- IALink.AddFile
- AddFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile
helpviewer_keywords:
- AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type:
- apiref
ms.openlocfilehash: 4dd104805d547613315335bc9c95b5c60a9cab14
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446675"
---
# <a name="addfile-method"></a>Método AddFile
Adiciona arquivos ao assembly. Também pode ser usado para criar módulos desvinculados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>Parâmetros  
 `AssemblyID`  
 ID exclusiva do assembly a ser aumentada.  
  
 `pszFilename`  
 Nome totalmente qualificado do arquivo a ser adicionado.  
  
 `dwFlags`  
 Sinalizadores de FileDef COM+, como `ffContainsNoMetaData` e `ffWriteable`. `dwFlags` é passado para o [método definofile](../metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pEmitter`  
 Interface de [interface IMetaDataEmit](../metadata/imetadataemit-interface.md) a ser usada para emitir metadados, se necessário.  
  
 `pFileToken`  
 Ponteiro para onde a ID exclusiva do arquivo adicionado será armazenada.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna S_OK se o método tiver sucesso.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 Requer ALink. h.  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink](ialink-interface.md)
- [Interface IALink2](ialink2-interface.md)
- [API do ALink](index.md)
