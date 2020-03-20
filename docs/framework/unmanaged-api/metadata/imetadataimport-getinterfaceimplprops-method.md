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
ms.openlocfilehash: 4b8ddf7fec12d175f030c0ea0ed982c6fb334aee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175376"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>Método IMetaDataImport::GetInterfaceImplProps
Obtém um ponteiro para os tokens de metadados para o <xref:System.Type> que implementa o método especificado e para a interface que declara esse método.
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `iiImpl`  
 [em] O token de metadados representando o método para retornar os tokens de classe e interface para.  
  
 `pClass`  
 [fora] O token de metadados representando a classe que implementa o método.  
  
 `ptkIface`  
 [fora] O token de metadados representando a interface que define o método implementado.  

## <a name="remarks"></a>Comentários

 Você obtém `iImpl` o valor para chamar o método [EnumInterfaceImpls.](imetadataimport-enuminterfaceimpls-method.md)

 Por exemplo, suponha `mdTypeDef` que uma classe tenha um valor de token de 0x02000007 e que implemente três interfaces cujos tipos têm tokens:

- 0x02000003 (TypeDef)
- 0x010000A (TypeRef)
- 0x0200001C (TypeDef)

Conceitualmente, essas informações são armazenadas em uma tabela de implementação de interface como:

| Número da linha | Token de classe | Token de interface |
|------------|-------------|-----------------|
| 4          |             |                 |
| 5          | 02000007    | 02000003        |
| 6          | 02000007    | 010000A        |
| 7          |             |                 |
| 8          | 02000007    | 0200001C        |

Lembre-se, o token é um valor de 4 bytes:

- Os 3 bytes inferiores mantêm o número da linha, ou RID.
- O byte superior contém o tipo de `mdtInterfaceImpl`token – 0x09 para .

`GetInterfaceImplProps`retorna as informações mantidas na linha cujo `iImpl` token você fornece no argumento.
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
