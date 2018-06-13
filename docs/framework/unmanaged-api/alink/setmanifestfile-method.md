---
title: Método SetManifestFile
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f8398c16b27836b772e8ac56ee1f7e8494f4be0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403563"
---
# <a name="setmanifestfile-method"></a>Método SetManifestFile
Permite que você especificar ou redefinir o arquivo de manifesto que o vinculador usa quando ele cria o assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszFile`  
  
 O nome do arquivo de manifesto cujos conteúdos são colocados no blob de recursos do Win32.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna S_OK se o método for bem-sucedido.  
  
## <a name="remarks"></a>Comentários  
 Chamá-lo antes de solicitar o Win32ResBlob. O valor de `pszFile` parâmetro é o nome do arquivo de manifesto cujos conteúdos são lidas e put nos recursos do Win32 com ID de RT_MANIFEST. Quando chamado usando um parâmetro de NULL, nenhum manifesto anteriormente leitura está desmarcado. Isso permite que um redefinir o estado do vinculador do tempo de inicialização.  
  
## <a name="requirements"></a>Requisitos  
 Requer aLink.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IALink3](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)  
 [API do ALink](../../../../docs/framework/unmanaged-api/alink/index.md)  
 [Interface IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Al.exe (Assembly Linker)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
