---
title: Interface IMetaDataImport
ms.date: 03/30/2017
api_name:
- IMetaDataImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport
helpviewer_keywords:
- IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0adbbd35-5e8d-4fec-8268-dc70a07c5975
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e4241f2057ce77713f91e969eda7765739613333
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732837"
---
# <a name="imetadataimport-interface"></a>Interface IMetaDataImport
Fornece métodos para importação e manipulação de metadados existentes de um arquivo executável portátil (PE) ou outra fonte, como uma biblioteca de tipos ou um binário de metadados independente, o tempo de execução.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CloseEnum](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-closeenum-method.md)|Fecha o enumerador com o identificador especificado.|  
|[Método CountEnum](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-countenum-method.md)|Obtém o número de elementos no enumerador com o identificador especificado.|  
|[Método EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md)|Enumera uma lista de tokens de definição de atributo personalizado associado com o tipo especificado ou um membro.|  
|[Método EnumEvents](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumevents-method.md)|Enumera os tokens de definição de eventos para o token de TypeDef especificado.|  
|[Método EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)|Enumera FieldDef tokens para o tipo referenciado pelo token de TypeDef especificado.|  
|[Método EnumFieldsWithName](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfieldswithname-method.md)|Enumera FieldDef tokens do tipo especificado com o nome especificado.|  
|[Método EnumInterfaceImpls](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enuminterfaceimpls-method.md)|Enumera os tokens MethodDef representando as implementações de interface.|  
|[Método EnumMemberRefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberrefs-method.md)|Enumera os tokens de MemberRef que representa os membros do tipo especificado.|  
|[Método EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md)|Enumera os tokens de MemberDef que representa os membros do tipo especificado.|  
|[Método EnumMembersWithName](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberswithname-method.md)|Enumera os tokens de MemberDef que representa os membros do tipo especificado com o nome especificado.|  
|[Método EnumMethodImpls](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodimpls-method.md)|Enumera MethodBody e MethodDeclaration tokens que representam os métodos do tipo especificado.|  
|[Método EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)|Enumera os tokens MethodDef que representam os métodos do tipo especificado.|  
|[Método EnumMethodSemantics](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodsemantics-method.md)|Enumera as propriedades e os eventos de alteração de propriedade à qual o método especificado está relacionado.|  
|[Método EnumMethodsWithName](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodswithname-method.md)|Enumera métodos que têm o nome especificado e que são definidos pelo tipo referenciado pelo token de TypeDef especificado.|  
|[Método EnumModuleRefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummodulerefs-method.md)|Enumera ModuleRef tokens que representam os módulos importados.|  
|[Método EnumParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumparams-method.md)|Enumera os tokens de ParamDef que representam os parâmetros do método referenciada pelo token de MethodDef especificado.|  
|[Método EnumPermissionSets](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumpermissionsets-method.md)|Enumera as permissões para os objetos em um escopo de metadados especificado.|  
|[Método EnumProperties](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumproperties-method.md)|Enumera os tokens de PropertyDef que representa as propriedades do tipo referenciado pelo token de TypeDef especificado.|  
|[Método EnumSignatures](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumsignatures-method.md)|Enumera os tokens de assinatura que representa as assinaturas autônomas no escopo atual.|  
|[Método EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)|Enumera os tokens de TypeDef que representa todos os tipos dentro do escopo atual.|  
|[Método EnumTypeRefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtyperefs-method.md)|Enumera os tokens TypeRef definidos no escopo atual de metadados.|  
|[Método EnumTypeSpecs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypespecs-method.md)|Enumera os tokens de TypeSpec definidos no escopo atual de metadados.|  
|[Método EnumUnresolvedMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumunresolvedmethods-method.md)|Enumera os tokens de MemberDef que representam os métodos não resolvidos no escopo atual de metadados.|  
|[Método EnumUserStrings](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumuserstrings-method.md)|Enumera os tokens de cadeia de caracteres que representa cadeias de caracteres codificadas no escopo atual de metadados.|  
|[Método FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)|Obtém o FieldDef token para o campo que é um membro do tipo especificado e tem o nome especificado e a assinatura de metadados.|  
|[Método FindMember](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmember-method.md)|Obtém um ponteiro para o MemberDef token para o membro definido pelo tipo especificado com o nome especificado e a assinatura de metadados.|  
|[Método FindMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmemberref-method.md)|Obtém um ponteiro para o MemberRef token para o membro definido pelo tipo especificado com o nome especificado e a assinatura de metadados.|  
|[Método FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md)|Obtém um ponteiro para o MethodDef token para o método definido pelo tipo especificado com o nome especificado e a assinatura de metadados.|  
|[Método FindTypeDefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtypedefbyname-method.md)|Obtém um ponteiro para os metadados de TypeDef token para o tipo com o nome especificado.|  
|[Método FindTypeRef](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtyperef-method.md)|Obtém um ponteiro para o token de metadados TypeRef que faz referência ao tipo no escopo de pesquisa especificado com o nome especificado.|  
|[Método GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)|Obtém o token de informações de layout para a classe referenciada por TypeDef especificado.|  
|[Método GetCustomAttributeByName](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributebyname-method.md)|Obtém o valor do atributo personalizado, dado seu nome.|  
|[Método GetCustomAttributeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributeprops-method.md)|Obtém o valor do atributo personalizado, dado seu token de metadados.|  
|[Método GetEventProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-geteventprops-method.md)|Obtém informações de metadados (incluindo o tipo de declaração, adicionar e remover métodos para representantes e os sinalizadores e outros dados associados) para o evento representado pelo token de evento especificado.|  
|[Método GetFieldMarshal](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldmarshal-method.md)|Obtém um ponteiro para o tipo não gerenciado, nativo do campo representado pelo token de metadados de campo especificado.|  
|[Método GetFieldProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldprops-method.md)|Obtém o token de metadados associados ao campo referido pelo FieldDef especificado.|  
|[Método GetInterfaceImplProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getinterfaceimplprops-method.md)|Obtém um ponteiro para os tokens de metadados para o tipo que implementa o método especificado e para a interface que declara esse método.|  
|[Método GetMemberProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberprops-method.md)|Obtém informações de metadados (incluindo o nome, a assinatura binária e o endereço virtual relativo) do membro de tipo referenciada pelo token de metadados especificado.|  
|[Método GetMemberRefProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberrefprops-method.md)|Obtém os metadados associados ao membro referenciado pelo token especificado.|  
|[Método GetMethodProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodprops-method.md)|Obtém o token de metadados associados com o método referenciado pelo MethodDef especificado.|  
|[Método GetMethodSemantics](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodsemantics-method.md)|Obtém um ponteiro para a relação entre o método referenciado pelo token MethodDef especificado e a propriedade emparelhada e o evento referenciado pelo EventProp especificado token.|  
|[Método GetModuleFromScope](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulefromscope-method.md)|Obtém um ponteiro para os metadados de token para o módulo referenciado no escopo atual de metadados.|  
|[Método GetModuleRefProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulerefprops-method.md)|Obtém o nome do módulo referenciado pelo token de metadados especificado.|  
|[Método GetNameFromToken](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnamefromtoken-method.md)|Obtém o nome de UTF-8 do objeto referenciado pelo token de metadados especificado.|  
|[Método GetNativeCallConvFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnativecallconvfromsig-method.md)|Obtém o nativo convenção de chamada para o método que é representado pelo ponteiro de assinatura especificada.|  
|[Método GetNestedClassProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnestedclassprops-method.md)|Obtém o TypeDef do token para o tipo delimitador do pai do tipo aninhado especificado.|  
|[Método GetParamForMethodIndex](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamformethodindex-method.md)|Obtém um ponteiro para o token que representa o parâmetro na posição ordinal especificada na sequência de parâmetros de método para o método representado pelo token MethodDef especificado.|  
|[Método GetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamprops-method.md)|Obtém os valores de metadados para o parâmetro referenciado pelo ParamDef especificado token.|  
|[Método GetPermissionSetProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpermissionsetprops-method.md)|Obtém os metadados associados a PermissionSet representado pelo token de permissão especificado.|  
|[GetPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpinvokemap-method.md)|Obtém um ModuleRef token para representar o assembly de destino de uma chamada de PInvoke.|  
|[Método GetPropertyProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpropertyprops-method.md)|Obtém os metadados associados com a propriedade representada pelo token especificado.|  
|[Método GetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getrva-method.md)|Obtém o deslocamento do endereço virtual relativo do código objeto representado pelo token especificado.|  
|[Método GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md)|Obtém o nome e, opcionalmente, o identificador de versão do assembly ou módulo no escopo atual de metadados.|  
|[Método GetSigFromToken](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getsigfromtoken-method.md)|Obtém a assinatura binária metadados associada com o token especificado.|  
|[Método GetTypeDefProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypedefprops-method.md)|Retorna informações de metadados para o tipo representado pelo token de TypeDef especificado.|  
|[Método GetTypeRefProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettyperefprops-method.md)|Obtém o token de metadados associado com o tipo referenciado pelo TypeRef especificado.|  
|[Método GetTypeSpecFromToken](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypespecfromtoken-method.md)|Obtém a assinatura de metadados de binários da especificação do tipo representada pelo token especificado.|  
|[Método GetUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getuserstring-method.md)|Obtém a cadeia de caracteres literal, representada pelo token de metadados especificado.|  
|[Método IsGlobal](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isglobal-method.md)|Obtém um valor que indica se o campo, método ou tipo representado pelo token de metadados especificado tem escopo global.|  
|[Método IsValidToken](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isvalidtoken-method.md)|Obtém um valor que indica se o token especificado mantém uma referência válida para um objeto de código.|  
|[Método ResetEnum](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resetenum-method.md)|Redefine o enumerador especificado na posição especificada.|  
|[Método ResolveTypeRef](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resolvetyperef-method.md)|Obtém informações de tipo para o tipo referenciado pelo token TypeRef especificado.|  
  
## <a name="remarks"></a>Comentários  
 O design do `IMetaDataImport` interface destina-se principalmente a ser usado por ferramentas e serviços que serão importando as informações de tipo (por exemplo, ferramentas de desenvolvimento) ou gerenciando implantado os componentes (por exemplo, serviços de resolução/ativação). Os métodos no `IMetaDataImport` se enquadram nas categorias de tarefas a seguir:  
  
-   Enumerando coleções de itens no escopo de metadados.  
  
-   Localizar um item que tem um conjunto específico de características.  
  
-   Obtendo as propriedades de um item especificado.  
  
-   Os métodos Get projetados especificamente para retornar as propriedades de valor único de um item de metadados. Quando a propriedade é uma referência a outro item, será retornado um token para aquele item. Qualquer tipo de ponteiro de entrada pode ser nulo para indicar que o valor específico não está sendo solicitado. Para obter as propriedades que são basicamente objetos de coleção (por exemplo, a coleção de interfaces que implementa uma classe), use os métodos de enumeração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
