---
title: Enumeração CorSymSearchPolicyAttributes
ms.date: 03/30/2017
api_name:
- CorSymSearchPolicyAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymSearchPolicyAttributes
helpviewer_keywords:
- CorSymSearchPolicyAttributes enumeration [.NET Framework debugging]
ms.assetid: 03abde84-930a-49d3-bac3-23abb34a0184
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7188c516d3d0a5192251697ec743e9d41f8d9072
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913738"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a>Enumeração CorSymSearchPolicyAttributes
Especifica a política a ser usada ao fazer uma pesquisa por um leitor de símbolo. Essas constantes são usadas pelos métodos [ISymUnmanagedBinder2:: GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) e [ISymUnmanagedBinder3:: GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) .  
  
> [!IMPORTANT]
> É um risco de segurança abrir um arquivo de banco de dados do programa (PDB) de uma fonte não confiável.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,       
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //      
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`AllowRegistryAccess`|Consulta o registro em busca de caminhos de pesquisa de símbolo.|  
|`AllowSymbolServerAccess`|Acessa um servidor de símbolos.|  
|`AllowOriginalPathAccess`|Pesquisa o caminho especificado no diretório de depuração.|  
|`AllowReferencePathAccess`|Procura o PDB no local onde está o arquivo. exe.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também

- [Enumerações do repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
