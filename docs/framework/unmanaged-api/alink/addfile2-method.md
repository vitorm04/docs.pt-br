---
title: Método AddFile2
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
ms.openlocfilehash: 8dadf9ec8f896b03e4918b21f5153c1b747010fd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446669"
---
# <a name="addfile2-method"></a>Método AddFile2
Adiciona arquivos ao assembly. Também pode ser usado para criar módulos desvinculados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>Parâmetros  
 `AssemblyID`  
 ID do assembly ao qual o arquivo é adicionado.  
  
 `pszFilename`  
 Nome do arquivo a ser adicionado.  
  
 `dwFlags`  
 Sinalizadores de `FileDef` COM+, como `ffContainsNoMetaData` e `ffWriteable`. `dwFlags` é passado para o [método definofile](../metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pEmitter`  
 Interface para interface de [interface IMetaDataEmit2](../metadata/imetadataemit2-interface.md) .  
  
 `pFileToken`  
 Recebe a ID do arquivo que está sendo adicionado.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna S_OK se o método tiver sucesso.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 Requer ALink. h.  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink2](ialink2-interface.md)
- [Interface IALink](ialink-interface.md)
- [API do ALink](index.md)
