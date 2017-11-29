---
title: Estrutura FUSION_INSTALL_REFERENCE
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FUSION_INSTALL_REFERENCE
api_location: fusion.dll
api_type: COM
f1_keywords: FUSION_INSTALL_REFERENCE
helpviewer_keywords: FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 244ea215b6668685920a454c1bd9da065076f38b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="fusioninstallreference-structure"></a>Estrutura FUSION_INSTALL_REFERENCE
Representa uma referência que faz com que um aplicativo a um assembly que o aplicativo instalado no cache de assembly global.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`cbSize`|O tamanho da estrutura em bytes.|  
|`dwFlags`|Reservado para extensibilidade futura. Esse valor deve ser 0 (zero).|  
|`guidScheme`|A entidade que adiciona a referência. Este campo pode ter um dos seguintes valores:<br /><br /> -FUSION_REFCOUNT_MSI_GUID: O assembly é referenciado por um aplicativo que foi instalado com o Microsoft Windows Installer. O `szIdentifier` campo é definido como `MSI`e o `szNonCanonicalData` campo é definido como `Windows Installer`. Esse esquema é usado para assemblies lado a lado do Windows.<br />-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: O assembly é referenciado por um aplicativo que aparece no **adicionar ou remover programas** interface. O `szIdentifier` campo fornece o token que registra o aplicativo com o **adicionar ou remover programas** interface.<br />-FUSION_REFCOUNT_FILEPATH_GUID: O assembly é referenciado por um aplicativo que é representado por um arquivo no sistema de arquivos. O `szIdentifier` campo fornece o caminho para este arquivo.<br />-FUSION_REFCOUNT_OPAQUE_STRING_GUID: O assembly é referenciado por um aplicativo que é representado apenas por uma cadeia de caracteres opaca. O `szIdentifier` campo fornece essa cadeia de caracteres opaca. O cache de assembly global não verifica a existência de referências opacas quando você remover este valor.<br />-FUSION_REFCOUNT_OSINSTALL_GUID: Este valor é reservado.|  
|`szIdentifier`|Uma cadeia de caracteres exclusiva que identifica o aplicativo que instalou o assembly no cache de assembly global. Seu valor depende do valor da `guidScheme` campo.|  
|`szNonCanonicalData`|Uma cadeia de caracteres que é entendida somente pelo que adiciona a referência de entidade. O cache de assembly global armazena essa cadeia de caracteres, mas não usá-lo.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [Cache de assembly global](../../../../docs/framework/app-domains/gac.md)
