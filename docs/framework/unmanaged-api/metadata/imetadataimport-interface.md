---
title: Interface IMetaDataImport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport
helpviewer_keywords: IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0adbbd35-5e8d-4fec-8268-dc70a07c5975
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1067582b506d60092bef9639dc4a96ba41306437
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport-interface"></a>Interface IMetaDataImport
Fornece métodos para importação e manipulação de metadados existentes de um arquivo PE (executável portátil) ou outra fonte, como uma biblioteca de tipos ou um binário de metadados independente, o tempo de execução.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CloseEnum](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-closeenum-method.md)|Fecha o enumerador com o identificador especificado.|  
|[Método CountEnum](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-countenum-method.md)|Obtém o número de elementos no enumerador com o identificador especificado.|  
|[Método EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md)|Enumera uma lista de tokens de definição de atributo personalizado associado ao tipo especificado ou membro.|  
|[Método EnumEvents](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumevents-method.md)|Enumera os tokens de definição de eventos para o token de TypeDef especificado.|  
|[Método EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)|Enumera FieldDef tokens para o tipo referenciado pelo token de TypeDef especificado.|  
|[Método EnumFieldsWithName](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfieldswithname-method.md)|Enumera os tokens de FieldDef do tipo especificado com o nome especificado.|  
|[Método EnumInterfaceImpls](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enuminterfaceimpls-method.md)|Enumera MethodDef tokens que representam as implementações de interface.|  
|[Método EnumMemberRefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberrefs-method.md)|Enumera os tokens de MemberRef que representa os membros do tipo especificado.|  
|[Método EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md)|Enumera os tokens de MemberDef que representa os membros do tipo especificado.|  
|[Método EnumMembersWithName](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummemberswithname-method.md)|Enumera os tokens de MemberDef que representa os membros do tipo especificado com o nome especificado.|  
|[Método EnumMethodImpls](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodimpls-method.md)|Enumera os tokens de MethodBody e MethodDeclaration que representa os métodos do tipo especificado.|  
|[Método EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)|Enumera MethodDef tokens que representa os métodos do tipo especificado.|  
|[Método EnumMethodSemantics](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodsemantics-method.md)|Enumera as propriedades e os eventos de alteração de propriedade ao qual o método especificado está relacionado.|  
|[Método EnumMethodsWithName](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethodswithname-method.md)|Enumera os métodos que têm o nome especificado e que são definidos pelo tipo referenciado pelo token de TypeDef especificado.|  
|[Método EnumModuleRefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummodulerefs-method.md)|Enumera ModuleRef tokens que representam os módulos importados.|  
|[Método EnumParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumparams-method.md)|Enumera ParamDef tokens que representam os parâmetros do método referenciada pelo token MethodDef especificado.|  
|[Método EnumPermissionSets](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumpermissionsets-method.md)|Enumera as permissões para os objetos em um escopo de metadados especificado.|  
|[Método EnumProperties](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumproperties-method.md)|Enumera os tokens de PropertyDef que representa as propriedades do tipo referenciado pelo token de TypeDef especificado.|  
|[Método EnumSignatures](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumsignatures-method.md)|Enumera os tokens de assinatura que representa as assinaturas autônomas no escopo atual.|  
|[Método EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)|Enumera os tokens de TypeDef que representa todos os tipos de dentro do escopo atual.|  
|[Método EnumTypeRefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtyperefs-method.md)|Enumera os tokens de TypeRef definidos no escopo atual de metadados.|  
|[Método EnumTypeSpecs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypespecs-method.md)|Enumera os tokens de TypeSpec definidos no escopo atual de metadados.|  
|[Método EnumUnresolvedMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumunresolvedmethods-method.md)|Enumera os tokens de MemberDef que representa os métodos não resolvidos no escopo atual de metadados.|  
|[Método EnumUserStrings](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumuserstrings-method.md)|Enumera os tokens de cadeia de caracteres que representa a cadeias de caracteres codificadas no escopo atual de metadados.|  
|[Método FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)|Obtém o FieldDef token para o campo que é um membro do tipo especificado e tem o nome especificado e a assinatura de metadados.|  
|[Método FindMember](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmember-method.md)|Obtém um ponteiro para o MemberDef token para o membro definido pelo tipo especificado com o nome especificado e a assinatura de metadados.|  
|[Método FindMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmemberref-method.md)|Obtém um ponteiro para o MemberRef token para o membro definido pelo tipo especificado com o nome especificado e a assinatura de metadados.|  
|[Método FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md)|Obtém um ponteiro para o MethodDef token para o método definido pelo tipo especificado com o nome especificado e a assinatura de metadados.|  
|[Método FindTypeDefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtypedefbyname-method.md)|Obtém um ponteiro para os metadados de TypeDef token para o tipo com o nome especificado.|  
|[Método FindTypeRef](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findtyperef-method.md)|Obtém um ponteiro para o token de metadados de TypeRef que faz referência ao tipo no escopo da pesquisa especificada com o nome especificado.|  
|[Método GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)|Obtém informações de layout para a classe referenciada por TypeDef especificado token.|  
|[Método GetCustomAttributeByName](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributebyname-method.md)|Obtém o valor do atributo personalizado, dado seu nome.|  
|[Método GetCustomAttributeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getcustomattributeprops-method.md)|Obtém o valor do atributo personalizado, dado seu token de metadados.|  
|[Método GetEventProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-geteventprops-method.md)|Obtém informações de metadados (incluindo o tipo de declaração, adicionar e remover métodos para delegados e os sinalizadores e outros dados associados) para o evento representado pelo token de evento especificado.|  
|[Método GetFieldMarshal](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldmarshal-method.md)|Obtém um ponteiro para o tipo nativo, não gerenciado do campo representado pelo token de metadados de campo especificado.|  
|[Método GetFieldProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getfieldprops-method.md)|Obtém os metadados associados ao campo referenciado pelo FieldDef especificado token.|  
|[Método GetInterfaceImplProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getinterfaceimplprops-method.md)|Obtém um ponteiro para os tokens de metadados para o tipo que implementa o método especificado e para a interface que declara esse método.|  
|[Método GetMemberProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberprops-method.md)|Obtém informações de metadados (incluindo o nome, a assinatura binária e o endereço virtual relativo) do membro do tipo referenciado pelo token de metadados especificado.|  
|[Método GetMemberRefProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmemberrefprops-method.md)|Obtém os metadados associados ao membro referenciado pelo token especificado.|  
|[Método GetMethodProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodprops-method.md)|Obtém os metadados associados com o método referenciado pelo MethodDef especificado token.|  
|[Método GetMethodSemantics](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmethodsemantics-method.md)|Obtém um ponteiro para a relação entre o método referenciado por token MethodDef especificado e a propriedade emparelhada e o evento referenciado pelo EventProp especificado token.|  
|[Método GetModuleFromScope](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulefromscope-method.md)|Obtém um ponteiro para os metadados de token para o módulo referenciado no escopo atual de metadados.|  
|[Método GetModuleRefProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getmodulerefprops-method.md)|Obtém o nome do módulo referenciado pelo token de metadados especificado.|  
|[Método GetNameFromToken](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnamefromtoken-method.md)|Obtém o nome de UTF-8 do objeto referenciado pelo token de metadados especificado.|  
|[Método GetNativeCallConvFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnativecallconvfromsig-method.md)|Obtém o nativo convenção de chamada para o método que é representado pelo ponteiro de assinatura especificada.|  
|[Método GetNestedClassProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getnestedclassprops-method.md)|Obtém o TypeDef token para o tipo de delimitador pai do tipo aninhado especificado.|  
|[Método GetParamForMethodIndex](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamformethodindex-method.md)|Obtém um ponteiro para o token que representa o parâmetro na posição ordinal especificada na sequência de parâmetros de método para o método representado pelo token MethodDef especificado.|  
|[Método GetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getparamprops-method.md)|Obtém os valores de metadados para o parâmetro referenciado pelo ParamDef especificado token.|  
|[Método GetPermissionSetProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpermissionsetprops-method.md)|Obtém os metadados associados a System.Security.PermissionSet representada pelo token de permissão especificado.|  
|[GetPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpinvokemap-method.md)|Obtém um ModuleRef token para representar o assembly de destino de uma chamada de PInvoke.|  
|[Método GetPropertyProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getpropertyprops-method.md)|Obtém os metadados associados com a propriedade representada pelo token especificado.|  
|[Método GetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getrva-method.md)|Obtém o deslocamento do endereço virtual relativo do objeto de código representado pelo token especificado.|  
|[Método GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md)|Obtém o nome e, opcionalmente, o identificador da versão do assembly ou módulo no escopo atual de metadados.|  
|[Método GetSigFromToken](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getsigfromtoken-method.md)|Obtém a assinatura de binários de metadados associada ao token especificado.|  
|[Método GetTypeDefProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypedefprops-method.md)|Retorna informações de metadados para o tipo representado pelo token de TypeDef especificado.|  
|[Método GetTypeRefProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettyperefprops-method.md)|Obtém os metadados associados com o tipo referenciado pelo TypeRef especificado token.|  
|[Método GetTypeSpecFromToken](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-gettypespecfromtoken-method.md)|Obtém a assinatura de metadados binário da especificação de tipo representada pelo token especificado.|  
|[Método GetUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getuserstring-method.md)|Obtém a cadeia de caracteres literal, representada pelo token de metadados especificado.|  
|[Método IsGlobal](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isglobal-method.md)|Obtém um valor que indica se o campo, método ou tipo representado pelo token de metadados especificado tem escopo global.|  
|[Método IsValidToken](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-isvalidtoken-method.md)|Obtém um valor que indica se o token especificado contém uma referência válida para um objeto de código.|  
|[Método ResetEnum](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resetenum-method.md)|Redefine o enumerador especificado para a posição especificada.|  
|[Método ResolveTypeRef](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-resolvetyperef-method.md)|Obtém informações de tipo para o tipo referenciado pelo token TypeRef especificado.|  
  
## <a name="remarks"></a>Comentários  
 O design do `IMetaDataImport` interface destina-se principalmente a ser usada por ferramentas e serviços que serão importando informações de tipo (por exemplo, ferramentas de desenvolvimento) ou gerenciando implantado os componentes (por exemplo, serviços de resolução/ativação). Os métodos em `IMetaDataImport` se enquadram nas categorias de tarefas a seguir:  
  
-   Enumerando coleções de itens no escopo de metadados.  
  
-   Localizar um item que tem um conjunto específico de características.  
  
-   Obtendo as propriedades de um item especificado.  
  
-   Os métodos Get projetados especificamente para retornar propriedades de valor único de um item de metadados. Quando a propriedade é uma referência a outro item, é retornado um token para aquele item. Qualquer tipo de ponteiro de entrada pode ser nulo para indicar que o valor específico não está sendo solicitado. Para obter as propriedades que são basicamente objetos de coleção (por exemplo, a coleção de interfaces que implementa uma classe), use os métodos de enumeração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
