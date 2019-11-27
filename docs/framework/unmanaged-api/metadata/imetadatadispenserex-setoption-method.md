---
title: Método IMetaDataDispenserEx::SetOption
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.SetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::SetOption
helpviewer_keywords:
- IMetaDataDispenserEx::SetOption method [.NET Framework metadata]
- SetOption method [.NET Framework metadata]
ms.assetid: 9f1c7ccd-7fb2-41d8-aa00-24b823376527
topic_type:
- apiref
ms.openlocfilehash: bc30f9fb120db92ccfc1e7dd0560b3fe18c54b29
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432736"
---
# <a name="imetadatadispenserexsetoption-method"></a>Método IMetaDataDispenserEx::SetOption
Define a opção especificada para um determinado valor para o escopo de metadados atual. A opção controla como as chamadas para o escopo de metadados atual são tratadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetOption (  
    [in] REFGUID optionId,   
    [in] const VARIANT *pValue  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `optionId`  
 no Um ponteiro para um GUID que especifica a opção a ser definida.  
  
 `pValue`  
 no O valor a ser usado para definir a opção. O tipo desse valor deve ser uma variante do tipo da opção especificada.  
  
## <a name="remarks"></a>Comentários  
 A tabela a seguir lista os GUIDs disponíveis aos quais o parâmetro `optionId` pode apontar e os valores válidos correspondentes para o parâmetro `pValue`.  
  
|GUID|Descrição|`pValue` parâmetro|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|Controla quais itens são verificados em busca de duplicatas. Sempre que você chamar um método [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) que cria um novo item, poderá pedir ao método para verificar se o item já existe no escopo atual. Por exemplo, você pode verificar a existência de itens de `mdMethodDef`; Nesse caso, quando você chama [IMetaDataEmit::D efinemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md), ele verificará se o método ainda não existe no escopo atual. Essa verificação usa a chave que identifica exclusivamente um determinado método: tipo de pai, nome e assinatura.|Deve ser uma variante do tipo UI4 e deve conter uma combinação dos valores da enumeração [CorCheckDuplicatesFor](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md) .|  
|MetaDataRefToDefCheck|Controla quais itens referenciados são convertidos em definições. Por padrão, o mecanismo de metadados otimizará o código convertendo um item referenciado em sua definição se o item referenciado for realmente definido no escopo atual.|Deve ser uma variante do tipo UI4 e deve conter uma combinação dos valores da enumeração [CorRefToDefCheck](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md) .|  
|MetaDataNotificationForTokenMovement|Controla quais remapeamentos de token ocorrem durante uma mesclagem de metadados gerar retornos de chamada. Use o método [IMetaDataEmit:: sethandlers](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) para estabelecer sua interface [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) .|Deve ser uma variante do tipo UI4 e deve conter uma combinação dos valores da enumeração [CorNotificationForTokenMovement](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md) .|  
|MetaDataSetENC|Controla o comportamento de Edit-and-Continue (ENC). Somente um modo de comportamento pode ser definido de cada vez.|Deve ser uma variante do tipo UI4 e deve conter um valor da enumeração [CorSetENC](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md) . O valor não é um bitmask.|  
|MetaDataErrorIfEmitOutOfOrder|Controla quais erros emitidos fora de ordem geram retornos de chamada. A emissão de metadados fora de ordem não é fatal; no entanto, se você emitir metadados em uma ordem que seja favoreceda pelo mecanismo de metadados, os metadados serão mais compactados e, portanto, poderão ser pesquisados com mais eficiência. Use o método `IMetaDataEmit::SetHandler` para estabelecer a interface [IMetaDataError](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) .|Deve ser uma variante do tipo UI4 e deve conter uma combinação dos valores da enumeração [CorErrorIfEmitOutOfOrder](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md) .|  
|MetaDataImportOption|Controla quais tipos de itens que foram excluídos durante um ENC são recuperados por um enumerador.|Deve ser uma variante do tipo UI4 e deve conter uma combinação dos valores da enumeração de [Enumeração CorImportOptions](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md) .|  
|MetaDataThreadSafetyOptions|Controla se o mecanismo de metadados obtém bloqueios de leitor/gravador, garantindo assim a segurança do thread. Por padrão, o mecanismo assume que o acesso é de thread único pelo chamador, portanto, nenhum bloqueio é obtido. Os clientes são responsáveis por manter a sincronização de thread adequada ao usar a API de metadados.|Deve ser uma variante do tipo UI4 e deve conter um valor da enumeração [CorThreadSafetyOptions](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md) . O valor não é um bitmask.|  
|MetaDataGenerateTCEAdapters|Controla se o importador da biblioteca de tipos deve gerar os adaptadores de TCE (eventos rigidamente acoplados) para contêineres de ponto de conexão COM.|Deve ser uma variante do tipo BOOL. Se `pValue` for definido como `true`, o importador da biblioteca de tipos gerará os adaptadores TCE.|  
|MetaDataTypeLibImportNamespace|Especifica um namespace não padrão para a biblioteca de tipos que está sendo importada.|Deve ser um valor nulo ou uma variante do tipo BSTR. Se `pValue` for um valor nulo, o namespace atual será definido como nulo; caso contrário, o namespace atual será definido como a cadeia de caracteres que é mantida no tipo BSTR da variante.|  
|MetaDataLinkerOptions|Controla se o vinculador deve gerar um assembly ou um arquivo de módulo .NET Framework.|Deve ser uma variante do tipo UI4 e deve conter uma combinação dos valores da enumeração [CorLinkerOptions](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md) .|  
|MetaDataRuntimeVersion|Especifica a versão do Common Language Runtime em relação ao qual esta imagem foi criada. A versão é armazenada como uma cadeia de caracteres, como "v 1.0.3705".|Deve ser um valor nulo, um valor VT_EMPTY ou uma variante do tipo BSTR. Se `pValue` for NULL, a versão de tempo de execução será definida como NULL. Se `pValue` for VT_EMPTY, a versão será definida como um valor padrão, que é desenhado a partir da versão de mscorwks. dll dentro da qual o código de metadados está em execução. Caso contrário, a versão de tempo de execução é definida como a cadeia de caracteres que é mantida no tipo BSTR da variante.|  
|MetaDataMergerOptions|Especifica opções para mesclagem de metadados.|Deve ser uma variante do tipo UI4 e deve conter uma combinação dos valores da enumeração `MergeFlags`, que é descrita no arquivo CorHdr. h.|  
|MetaDataPreserveLocalRefs|Desabilita a otimização de referências locais em definições.|Deve conter uma combinação dos valores da enumeração [CorLocalRefPreservation](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md) .|  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataforma:** Consulte [requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [Interface IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
