---
title: Método IMetaDataTables::GetNextUserString
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextUserString
helpviewer_keywords:
- GetNextUserString method [.NET Framework metadata]
- IMetaDataTables::GetNextUserString method [.NET Framework metadata]
ms.assetid: b7cb40ee-67b7-4f4e-8dcc-ee7ac8bc986b
topic_type:
- apiref
ms.openlocfilehash: 6522dbc8e49d612fc4c0d9597a9b5f12edb2cfe1
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937781"
---
# <a name="imetadatatablesgetnextuserstring-method"></a>Método IMetaDataTables::GetNextUserString
Obtém o índice da linha que contém a próxima cadeia de caracteres embutida em código na coluna da tabela atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ixUserString`  
 no Um valor de índice da coluna de cadeia de caracteres atual.  
  
 `pNext`  
 fora Um ponteiro para o índice de linha da próxima cadeia de caracteres na coluna.  
  
## <a name="remarks"></a>Comentários  
 Não recomendamos o uso desse método, pois ele não retorna resultados consistentes. Para obter informações sobre a tabela de GUID, consulte a documentação de Common Language Infrastructure (CLI), especialmente "partição II: definição de metadados e semântica". A documentação está disponível online; consulte [padrões C# ECMA e Common Language Infrastructure](../../../standard/components.md#applicable-standards) e [a CLI (Standard ECMA-335-Common Language Infrastructure)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface IMetaDataTables](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [Interface IMetaDataTables2](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
