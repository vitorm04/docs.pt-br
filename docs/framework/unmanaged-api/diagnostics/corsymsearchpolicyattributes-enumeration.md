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
ms.openlocfilehash: 8a9b0f085820bac12638c0310ab23b2eafacb23b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186167"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a>Enumeração CorSymSearchPolicyAttributes
Especifica a política a ser usado ao fazer uma pesquisa por um leitor de símbolo. Essas constantes são usadas pelo [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) e [ISymUnmanagedBinder3::GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) métodos.  
  
> [!IMPORTANT]
>  É um risco de segurança para abrir um arquivo de programa (PDB) do banco de dados de uma fonte não confiável.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
|`AllowRegistryAccess`|Consulta o registro para caminhos de pesquisa do símbolo.|  
|`AllowSymbolServerAccess`|Acessa um servidor de símbolos.|  
|`AllowOriginalPathAccess`|Pesquisa o caminho especificado no diretório de depuração.|  
|`AllowReferencePathAccess`|Pesquisa o PDB no local onde está o arquivo .exe.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também

- [Enumerações do repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
