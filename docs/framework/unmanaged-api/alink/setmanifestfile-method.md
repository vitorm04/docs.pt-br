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
ms.openlocfilehash: 8307960166cfc668a577431d688c439f0f794be2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072422"
---
# <a name="setmanifestfile-method"></a>Método SetManifestFile
Permite que você especificar ou redefinir o arquivo de manifesto que o vinculador usa quando cria o assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pszFile`  
  
 O nome do arquivo de manifesto cujos conteúdos são colocados no blob de recursos do Win32.  
  
## <a name="return-value"></a>Valor de retorno  
 Se o método for bem-sucedido, retornará S_OK.  
  
## <a name="remarks"></a>Comentários  
 Chame isso antes de solicitar o Win32ResBlob. O valor da `pszFile` parâmetro é o nome do arquivo de manifesto cujos conteúdos são lidos e put nos recursos do Win32 com ID de RT_MANIFEST. Quando chamado usando um parâmetro de NULL, nenhum manifesto lida anteriormente está desmarcado. Isso permite que um para redefinir o estado do vinculador para que o tempo de inicialização.  
  
## <a name="requirements"></a>Requisitos  
 Requer aLink.h  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink3](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)
- [API do ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
- [Interface IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [Al.exe (Assembly Linker)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
