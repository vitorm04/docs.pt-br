---
title: Método IMetaDataImport::GetInterfaceImplProps
ms.date: 02/25/2019
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76e2ebbd47a5e36a722fce33ba67d7efb4db8675
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115928"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>Método IMetaDataImport::GetInterfaceImplProps
Obtém um ponteiro para os tokens de metadados para o <xref:System.Type> que implementa o método especificado, e para a interface que declara esse método.
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `iiImpl`  
 [in] O token de metadados que representa o método para retornar os tokens de classe e interface para.  
  
 `pClass`  
 [out] O token de metadados que representa a classe que implementa o método.  
  
 `ptkIface`  
 [out] O token de metadados que representa a interface que define o método implementado.  

## <a name="remarks"></a>Comentários

 Obter o valor de `iImpl` chamando o [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) método.
 
 Por exemplo, suponha que uma classe tem um `mdTypeDef` valor 0x02000007 e que ele implementa três interfaces cujos tipos têm tokens de token: 

- 0x02000003 (TypeDef)
- 0x0100000A (TypeRef)
- 0x0200001C (TypeDef)

Conceitualmente, essas informações são armazenadas em uma tabela de implementação de interface como:

| Número de linha | Token de classe | Token de interface |
|------------|-------------|-----------------|
| 4          |             |                 |
| 5          | 02000007    | 02000003        |
| 6          | 02000007    | 0100000A        |
| 7          |             |                 |
| 8          | 02000007    | 0200001C        |

Lembre-se de que o token é um valor de 4 bytes:

- Inferiores a 3 bytes contêm o número de linha ou de RID.
- O byte superior contém o tipo de token – 0x09 para `mdtInterfaceImpl`.

`GetInterfaceImplProps` Retorna as informações mantidas na linha cujo token que você fornecer no `iImpl` argumento. 
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
