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
ms.openlocfilehash: f8e85a670d04e5825653864484b7ccd9ce747949
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175896"
---
# <a name="imetadatadispenserexsetoption-method"></a>Método IMetaDataDispenserEx::SetOption
Define a opção especificada para um determinado valor para o escopo de metadados atual. A opção controla como as chamadas para o escopo de metadados atuais são tratadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetOption (  
    [in] REFGUID optionId,
    [in] const VARIANT *pValue  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `optionId`  
 [em] Um ponteiro para um GUID que especifica a opção a ser definida.  
  
 `pValue`  
 [em] O valor a ser usado para definir a opção. O tipo deste valor deve ser uma variante do tipo da opção especificada.  
  
## <a name="remarks"></a>Comentários  
 A tabela a seguir lista as `optionId` GUIDs disponíveis que o parâmetro `pValue` pode apontar e os valores válidos correspondentes para o parâmetro.  
  
|GUID|Descrição|`pValue`Parâmetro|  
|----------|-----------------|------------------------|  
|MetaDadosVerificandoduplicadosPara|Controla quais itens são verificados para duplicatas. Cada vez que você chamar um método [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) que cria um novo item, você pode pedir ao método para verificar se o item já existe no escopo atual. Por exemplo, você pode verificar `mdMethodDef` a existência de itens; neste caso, quando você chamar [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md), ele verificará se o método ainda não existe no escopo atual. Esta verificação usa a chave que identifica exclusivamente um determinado método: tipo pai, nome e assinatura.|Deve ser uma variante do tipo UI4, e deve conter uma combinação dos valores do [CorCheckDuplicatesPara](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md) enumeração.|  
|MetaDataRefToDefCheck|Os controles que referenciavam itens são convertidos em definições. Por padrão, o mecanismo de metadados otimizará o código convertendo um item referenciado à sua definição se o item referenciado for realmente definido no escopo atual.|Deve ser uma variante do tipo UI4, e deve conter uma combinação dos valores da enumeração [CorRefToDefCheck.](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md)|  
|MetaDataNotificationToKenMovement|Controles que remapeiam remapeadores durante uma mesclagem de metadados geram retornos de chamada. Use o método [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) para estabelecer sua interface [IMapToken.](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)|Deve ser uma variante do tipo UI4, e deve conter uma combinação dos valores da enumeração [CorNotificationForTokenMovement.](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md)|  
|MetaDataSetENC|Controla o comportamento de editar e continuar (ENC). Apenas um modo de comportamento pode ser definido de cada vez.|Deve ser uma variante do tipo UI4, e deve conter um valor da enumeração [CorSetENC.](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md) O valor não é uma máscara de bit.|  
|MetaDataErrorItItOutOutOfOrder|Controles que emitem erros fora de ordem geram retornos de chamada. Emitir metadados fora de ordem não é fatal; no entanto, se você emite metadados em uma ordem que é favorecida pelo mecanismo de metadados, os metadados são mais compactos e, portanto, podem ser pesquisados de forma mais eficiente. Use `IMetaDataEmit::SetHandler` o método para estabelecer sua interface [IMetaDataError.](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)|Deve ser uma variante do tipo UI4, e deve conter uma combinação dos valores da enumeração [CorErrorIfEmitOutOfOrder.](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md)|  
|MetaDataImportOption|Controles que tipos de itens que foram excluídos durante um ENC são recuperados por um enumerador.|Deve ser uma variante do tipo UI4, e deve conter uma combinação dos valores da [enumeração CorImportOptions Enumeration.](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md)|  
|Opções de segurança do MetaDataThread|Controla se o mecanismo de metadados obtém bloqueios de leitor/escritor, garantindo assim a segurança do segmento. Por padrão, o mecanismo assume que o acesso é de um único rosca pelo chamador, de modo que nenhum bloqueio é obtido. Os clientes são responsáveis por manter a sincronização adequada do segmento ao usar a API de metadados.|Deve ser uma variante do tipo UI4, e deve conter um valor da enumeração [CorThreadSafetyOptions.](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md) O valor não é uma máscara de bit.|  
|MetaDataGeraradaptados DESEGURANÇA|Controla se o importador da biblioteca do tipo deve gerar os adaptadores de evento de evento acoplado (TCE) para recipientes de ponto de conexão COM.|Deve ser uma variante do tipo BOOL. Se `pValue` for `true`definido como , o importador de biblioteca tipo gera os adaptadores TCE.|  
|MetaDataTypeLib'SNomespace|Especifica um namespace não padrão para a biblioteca de tipos que está sendo importada.|Deve ser um valor nulo ou uma variante do tipo BSTR. Se `pValue` for um valor nulo, o namespace atual será definido como nulo; caso contrário, o namespace atual é definido para a string que é mantida no tipo BSTR da variante.|  
|Opções de MetaDataLinker|Controla se o linker deve gerar um conjunto ou um arquivo de módulo .NET Framework.|Deve ser uma variante do tipo UI4, e deve conter uma combinação dos valores da enumeração [CorLinkerOptions.](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md)|  
|MetaDataExecução de tempo|Especifica a versão do tempo de execução do idioma comum contra o qual essa imagem foi construída. A versão é armazenada como uma string, como "v1.0.3705".|Deve ser um valor nulo, um valor VT_EMPTY ou uma variante do tipo BSTR. Se `pValue` for nula, a versão em tempo de execução será definida como nula. Se `pValue` for VT_EMPTY, a versão será definida como um valor padrão, que é extraído da versão do Mscorwks.dll dentro do qual o código de metadados está sendo executado. Caso contrário, a versão em tempo de execução é definida como a string que é mantida no tipo BSTR da variante.|  
|Opções de fusão de metadados|Especifica opções para mesclar metadados.|Deve ser uma variante do tipo UI4, e `MergeFlags` deve conter uma combinação dos valores da enumeração, que está descrito no arquivo CorHdr.h.|  
|MetaDataPreserveLocalRefs|Desabilita a otimização de referências locais em definições.|Deve conter uma combinação dos valores da enumeração [CorLocalRefPreservation.](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md)|  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** Consulte [os requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [Interface IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
