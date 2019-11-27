---
title: Método SetAssemblyFile
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
ms.openlocfilehash: 1db4c4ab7e47e223a492e08297ac3cedcb3a27eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445597"
---
# <a name="setassemblyfile-method"></a>Método SetAssemblyFile
Atribui o nome do assembly a ser compilado. Não para uso na produção de módulos não associados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pszFilename`  
 Nome totalmente qualificado do arquivo de manifesto.  
  
 `pEmitter`  
 Ponteiro para interface de [interface IMetaDataEmit](../metadata/imetadataemit-interface.md) .  
  
 `afFlags`  
 Sinalizadores, conforme definido na [Enumeração AssemblyFlags](../metadata/assemblyflags-enumeration.md).  
  
 `pAssemblyID`  
 Ponteiro para a ID do assembly resultante.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna S_OK se o método tiver sucesso.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 Requer ALink. h.  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink](ialink-interface.md)
- [Interface IALink2](ialink2-interface.md)
- [API do ALink](index.md)
