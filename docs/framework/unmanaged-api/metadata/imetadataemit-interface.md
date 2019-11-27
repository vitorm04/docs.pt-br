---
title: Interface IMetaDataEmit
ms.date: 03/30/2017
api_name:
- IMetaDataEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit
helpviewer_keywords:
- IMetaDataEmit interface [.NET Framework metadata]
ms.assetid: 3b48fd47-7397-4e2c-8bec-8157aa08978c
topic_type:
- apiref
ms.openlocfilehash: b4ae599a0e5cdb604fd9a610728671b39c67af31
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440892"
---
# <a name="imetadataemit-interface"></a>Interface IMetaDataEmit
Fornece métodos para criar, modificar e salvar metadados sobre o assembly no escopo definido no momento. Os metadados podem ser armazenados na memória ou salvos em disco.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)|Atualiza o escopo do assembly atual com as alterações feitas no `pImport`especificado.|  
|[Método DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)|Cria uma definição para um atributo personalizado com a assinatura de metadados especificada, a ser anexada ao objeto especificado e Obtém um token para essa definição de atributo personalizado.|  
|[Método DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)|Cria uma definição para um evento com a assinatura de metadados especificada e Obtém um token para essa definição de evento.|  
|[Método DefineField](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definefield-method.md)|Cria uma definição para um campo com a assinatura de metadados especificada e Obtém um token para essa definição de campo.|  
|[Método DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)|Cria uma definição para um membro de um tipo que é definido em um módulo fora do escopo atual e Obtém um token para essa definição de referência.|  
|[Método DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)|Cria uma definição para uma referência a um tipo que é definido em um módulo fora do escopo atual e Obtém um token para essa definição de referência.|  
|[Método DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)|Cria uma definição para uma referência a um membro de um módulo fora do escopo atual e Obtém um token para essa definição de referência.|  
|[Método DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)|Cria uma definição para um método com a assinatura especificada e retorna um token para essa definição de método.|  
|[Método DefineMethodImpl](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethodimpl-method.md)|Cria uma definição para implementação de um método herdado de uma interface e retorna um token para essa definição de implementação de método.|  
|[Método DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)|Cria a assinatura de metadados para um módulo com o nome especificado.|  
|[Método DefineNestedType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definenestedtype-method.md)|Cria a assinatura de metadados de uma definição de tipo e retorna um token `mdTypeDef` para esse tipo, especificando também que o tipo definido é um membro do tipo referenciado por `tdEncloser`.|  
|[Método DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md)|Cria uma definição de parâmetro com a assinatura especificada para o método referenciado pelo token especificado e Obtém um token para essa definição de parâmetro.|  
|[Método DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md)|Cria uma definição para um conjunto de permissões com a assinatura de metadados especificada e Obtém um token para essa definição de conjunto de permissões.|  
|[Método DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)|Define os recursos da assinatura PInvoke do método referenciado pelo token especificado.|  
|[Método DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md)|Cria uma definição de propriedade para o tipo especificado, com o `get` especificado e `set` acessadores de método, e Obtém um token para essa definição de propriedade.|  
|[Método DefineSecurityAttributeSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definesecurityattributeset-method.md)|Cria um conjunto de permissões de segurança para anexar ao objeto referenciado pelo token especificado.|  
|[Método DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)|Cria uma definição de tipo para um tipo de Common Language Runtime e Obtém um token de metadados para essa definição de tipo.|  
|[Método DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)|Obtém um token de metadados para um tipo que é definido em outro módulo fora do escopo atual.|  
|[Método DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)|Obtém um token de metadados para a cadeia de caracteres literal especificada.|  
|[Método DeleteClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deleteclasslayout-method.md)|Destrói a assinatura de metadados de layout de classe para o tipo referenciado pelo token especificado.|  
|[Método DeleteFieldMarshal](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletefieldmarshal-method.md)|Destrói a assinatura de metadados de marshaling do PInvoke para o objeto referenciado pelo token especificado.|  
|[Método DeletePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletepinvokemap-method.md)|Destrói os metadados de mapeamento do PInvoke para o objeto referenciado pelo token especificado.|  
|[Método DeleteToken](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-deletetoken-method.md)|Exclui o token especificado do escopo de metadados atual.|  
|[Método GetSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-getsavesize-method.md)|Obtém o tamanho binário estimado do assembly no escopo atual.|  
|[Método GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md)|Obtém um token para a assinatura de metadados especificada.|  
|[Método GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)|Obtém um token de metadados para o tipo com a assinatura de metadados especificada.|  
|[Método Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)|Adiciona o escopo importado especificado à lista de escopos a serem mesclados.|  
|[Método MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)|Mescla no escopo atual todos os escopos de metadados especificados por uma ou mais chamadas anteriores para `IMetaDataEmit::Merge`.|  
|[Método Save](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-save-method.md)|Salva todos os metadados no escopo atual para o arquivo no endereço especificado.|  
|[Método SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)|Salva todos os metadados no escopo atual para a área especificada da memória.|  
|[Método SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)|Salva todos os metadados no escopo atual para o `IStream`especificado.|  
|[Método SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md)|Define ou atualiza a assinatura de layout de classe de um tipo definido por uma chamada anterior para `IMetaDataEmit::DefineTypeDef`.|  
|[Método SetCustomAttributeValue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setcustomattributevalue-method.md)|Define ou atualiza o valor de um atributo personalizado definido por uma chamada anterior para `IMetaDataEmit::DefineCustomAttribute`.|  
|[Método SetEventProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-seteventprops-method.md)|Define ou atualiza o recurso especificado de um evento definido por uma chamada anterior para `IMetaDataEmit::DefineEvent`.|  
|[Método SetFieldMarshal](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldmarshal-method.md)|Define as informações de marshaling do PInvoke para o campo, o retorno do método ou o parâmetro do método referenciado pelo token especificado.|  
|[Método SetFieldProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldprops-method.md)|Define ou atualiza o valor padrão para o campo referenciado pelo token do campo especificado.|  
|[Método SetFieldRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setfieldrva-method.md)|Define um valor de variável global para o endereço virtual relativo do campo referenciado pelo token especificado.|  
|[Método SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)|Define o método referenciado pelo ponteiro de `IUnknown` especificado como um retorno de chamada de notificação para remapeamentos de token.|  
|[Método SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)|Define ou atualiza a assinatura de metadados da implementação do método herdado referenciado pelo token especificado.|  
|[Método SetMethodProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodprops-method.md)|Define ou atualiza o recurso, armazenado no endereço virtual relativo especificado, de um método definido por uma chamada anterior para `IMetaDataEmit::DefineMethod`.|  
|[Método SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)|Atualiza referências a um módulo definido por uma chamada anterior para `IMetaDataEmit::DefineModuleRef`.|  
|[Método SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)|Define ou altera recursos de um parâmetro de método que foi definido por uma chamada anterior para `IMetaDataEmit::DefineParam`.|  
|[Método SetParent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparent-method.md)|Estabelece que o membro especificado, conforme definido por uma chamada anterior para `IMetaDataEmit::DefineMemberRef`, é um membro do tipo especificado, conforme definido por uma chamada anterior para `IMetaDataEmit::DefineTypeDef`.|  
|[Método SetPermissionSetProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpermissionsetprops-method.md)|Define ou atualiza recursos da assinatura de metadados de um conjunto de permissões definido por uma chamada anterior para `IMetaDataEmit::DefinePermissionSet`.|  
|[Método SetPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpinvokemap-method.md)|Define ou altera recursos da assinatura do PInvoke de um método, conforme definido por uma chamada anterior para `IMetaDataEmit::DefinePinvokeMap`.|  
|[Método SetPropertyProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setpropertyprops-method.md)|Define os recursos armazenados em metadados para uma propriedade definida por uma chamada anterior para `IMetaDataEmit::DefineProperty`.|  
|[Método SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)|Define o endereço virtual relativo do método especificado.|  
|[Método SetTypeDefProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-settypedefprops-method.md)|Define recursos de um tipo definido por uma chamada anterior para `IMetaDataEmit::DefineTypeDef`.|  
|[Método TranslateSigWithScope](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-translatesigwithscope-method.md)|Importa um assembly para o escopo atual e obtém uma nova assinatura de metadados para o escopo mesclado.|  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
