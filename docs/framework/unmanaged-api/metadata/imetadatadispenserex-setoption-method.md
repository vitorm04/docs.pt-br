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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cfe600b54eb03a07ea01375355c5ff94190e5d9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatadispenserexsetoption-method"></a>Método IMetaDataDispenserEx::SetOption
Define a opção especificada para um determinado valor para o escopo de metadados atual. A opção controla como as chamadas para o escopo de metadados atual são tratadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetOption (  
    [in] REFGUID optionId,   
    [in] const VARIANT *pValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `optionId`  
 [in] Um ponteiro para um GUID que especifica a opção a ser definido.  
  
 `pValue`  
 [in] O valor a ser usado para definir a opção. O tipo do valor deve ser uma variante do tipo da opção especificada.  
  
## <a name="remarks"></a>Comentários  
 A tabela a seguir lista os GUIDs disponíveis que o `optionId` parâmetro pode apontar para e os valores válidos correspondentes para o `pValue` parâmetro.  
  
|GUID|Descrição|`pValue` Parâmetro|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|Controla quais itens são marcados para duplicatas. Cada vez que você chamar um [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) método que cria um novo item, você pode pedir o método para verificar se o item já existe no escopo atual. Por exemplo, você pode verificar a existência de `mdMethodDef` itens; nesse caso, quando você chama [Definemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md), ele verificará se o método ainda não existir no escopo atual. Essa verificação usa a chave que identifica exclusivamente um determinado método: pai tipo, nome e assinatura.|Deve ser uma variante do tipo UI4 e deve conter uma combinação dos valores da [CorCheckDuplicatesFor](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md) enumeração.|  
|MetaDataRefToDefCheck|Controla quais itens de referência é convertidas em definições. Por padrão, o mecanismo de metadados otimizará o código, convertendo um item referenciado em sua definição se o item referenciado é definido no escopo atual.|Deve ser uma variante do tipo UI4 e deve conter uma combinação dos valores da [CorRefToDefCheck](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md) enumeração.|  
|MetaDataNotificationForTokenMovement|Qual o token remapeia que ocorrem durante uma mesclagem de metadados de controles gerarem retornos de chamada. Use o [: Sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) método para estabelecer sua [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface.|Deve ser uma variante do tipo UI4 e deve conter uma combinação dos valores da [CorNotificationForTokenMovement](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md) enumeração.|  
|MetaDataSetENC|Controla o comportamento de editar e continuar (c). Apenas um modo de comportamento pode ser definido por vez.|Deve ser uma variante do tipo UI4 e deve conter um valor de [CorSetENC](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md) enumeração. O valor não é uma máscara de bits.|  
|MetaDataErrorIfEmitOutOfOrder|Controla quais erros emitido-fora de ordem geram retornos de chamada. Não é fatal; emissoras de metadados fora de ordem No entanto, se você emitir metadados em uma ordem que é protegido pelo mecanismo de metadados, os metadados mais compacta e, portanto, podem ser pesquisados com mais eficiência. Use o `IMetaDataEmit::SetHandler` método para estabelecer sua [IMetaDataError](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) interface.|Deve ser uma variante do tipo UI4 e deve conter uma combinação dos valores da [CorErrorIfEmitOutOfOrder](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md) enumeração.|  
|MetaDataImportOption|Controla quais tipos de itens que foram excluídos durante um ENC são recuperados por um enumerador.|Deve ser uma variante do tipo UI4 e deve conter uma combinação dos valores da [enumeração CorImportOptions](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md) enumeração.|  
|MetaDataThreadSafetyOptions|Controla se o mecanismo de metadados obtém leitor/gravador bloqueios, garantindo a segurança do thread. Por padrão, o mecanismo pressupõe que acesso é single-threaded pelo chamador, portanto não há bloqueios são obtidos. Os clientes são responsáveis por manter sincronização adequada da thread ao usar o API de metadados.|Deve ser uma variante do tipo UI4 e deve conter um valor de [CorThreadSafetyOptions](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md) enumeração. O valor não é uma máscara de bits.|  
|MetaDataGenerateTCEAdapters|Controla se o importador da biblioteca deve gerar os adaptadores de evento firmemente acopladas (TCE) para contêineres de ponto de conexão de COM.|Deve ser uma variante do tipo BOOL. Se `pValue` é definido como `true`, o importador da biblioteca gera os adaptadores TCE.|  
|MetaDataTypeLibImportNamespace|Especifica um namespace não padrão para a biblioteca de tipo que está sendo importado.|Deve ser um valor nulo ou uma variante do tipo BSTR. Se `pValue` é um valor nulo, o namespace atual está definido como nulo; caso contrário, o namespace atual está definido como a cadeia de caracteres que é mantida no tipo BSTR da variante.|  
|MetaDataLinkerOptions|Controla se o vinculador deve gerar um assembly ou um arquivo de módulo do .NET Framework.|Deve ser uma variante do tipo UI4 e deve conter uma combinação dos valores da [CorLinkerOptions](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md) enumeração.|  
|MetaDataRuntimeVersion|Especifica a versão do common language runtime em relação ao qual esta imagem foi criada. A versão é armazenada como uma cadeia de caracteres, como "v 1.0.3705".|Deve ser um valor nulo, um valor VT_EMPTY ou uma variante do tipo BSTR. Se `pValue` for null, a versão de tempo de execução é definida como null. Se `pValue` é VT_EMPTY, a versão é definida como um valor padrão, que é desenhado da versão do arquivo Mscorwks.dll dentro do qual o código de metadados está em execução. Caso contrário, a versão de tempo de execução é definida como a cadeia de caracteres que é mantida no tipo BSTR da variante.|  
|MetaDataMergerOptions|Especifica opções para metadados de mesclagem.|Deve ser uma variante do tipo UI4 e deve conter uma combinação dos valores da `MergeFlags` enumeração, que é descrita no arquivo Corhdr.|  
|MetaDataPreserveLocalRefs|Desabilita locais referências às definições de otimização.|Deve conter uma combinação dos valores da [CorLocalRefPreservation](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md) enumeração.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [Interface IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
