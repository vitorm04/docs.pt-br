---
title: Elemento <serviceAuthorization>
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: 7099c5eca9cf28624153a705e4e16136628214a2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157333"
---
# <a name="serviceauthorization-element"></a>\<serviceAuthorization > elemento
Especifica as configurações que autorizam o acesso a operações de serviço  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors>  
\<behavior>  
\<serviceAuthorization>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<serviceAuthorization impersonateCallerForAllOperations="Boolean"
                      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"
                      roleProviderName="String"
                      serviceAuthorizationManagerType="String">
  <authorizationPolicies>
    <add policyType="String" />
  </authorizationPolicies>
</serviceAuthorization>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|impersonateCallerForAllOperations|Um valor booliano que especifica se todas as operações no serviço representam o chamador. O padrão é `false`.<br /><br /> Quando uma operação de serviço específica representará o chamador, o contexto do thread é alternado para o contexto do chamador antes de executar o serviço especificado.|  
|principalPermissionMode|Define a entidade de segurança usada para executar operações no servidor. Os valores incluem o seguinte:<br /><br /> – None<br />-UseWindowsGroups<br />-   UseAspNetRoles<br />-Custom<br /><br /> O valor padrão é UseWindowsGroups. O valor é do tipo <xref:System.ServiceModel.Description.PrincipalPermissionMode>. Para obter mais informações sobre como usar esse atributo, consulte [como: Restringir o acesso com a classe PrincipalPermissionAttribute](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).|  
|roleProviderName|Uma cadeia de caracteres que especifica o nome do provedor de função, que fornece informações de função para um aplicativo do Windows Communication Foundation (WCF). O padrão é uma cadeia de caracteres vazia.|  
|ServiceAuthorizationManagerType|Uma cadeia de caracteres que contém o tipo do Gerenciador de autorização de serviço. Para obter mais informações, consulte <xref:System.ServiceModel.ServiceAuthorizationManager>.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|authorizationPolicies|Contém uma coleção de tipos de política de autorização, que podem ser adicionados usando o `add` palavra-chave. Cada política de autorização contém um único necessário `policyType` atributo que é uma cadeia de caracteres. O atributo especifica uma política de autorização, que possibilita a transformação de um conjunto de declarações de entrada em outro conjunto de declarações. Controle de acesso pode ser concedido ou negado com base nisso. Para obter mais informações, consulte <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Contém uma coleção de configurações para o comportamento de um serviço.|  
  
## <a name="remarks"></a>Comentários  
 Esta seção contém os elementos que afetam a representação de autorização e provedores de função personalizada.  
  
 O `principalPermissionMode` atributo especifica os grupos de usuários para usar ao autorizar o uso de um método protegido. O valor padrão é `UseWindowsGroups` e especifica que os grupos do Windows, como "Administradores" ou "Usuários", são pesquisados para uma tentativa de acessar um recurso de identidade. Você também pode especificar `UseAspNetRoles` para usar um provedor de função personalizada que é configurado no \<System. Web > elemento, conforme mostrado no código a seguir.  
  
```xml  
<system.web>
  <membership defaultProvider="SqlProvider"
              userIsOnlineTimeWindow="15">
    <providers>
      <clear />
      <add name="SqlProvider"
           type="System.Web.Security.SqlMembershipProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipProvider"
           enablePasswordRetrieval="false"
           enablePasswordReset="false"
           requiresQuestionAndAnswer="false"
           requiresUniqueEmail="true"
           passwordFormat="Hashed" />
    </providers>
  </membership>
  <!-- Other configuration code not shown. -->
</system.web>
```  
  
 O código a seguir mostra a `roleProviderName` usado com o `principalPermissionMode` atributo.  
  
```xml  
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```  
  
 Para obter um exemplo detalhado de como usar este elemento de configuração, consulte [autorizando o acesso a operações de serviço](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md) e [política de autorização](../../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [Comportamentos de segurança](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Autorizando o acesso a operações de serviço](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [Como: Criar um Gerenciador de autorização personalizado para um serviço](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [Como: Restringir o acesso com a PrincipalPermissionAttribute Class](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Política de autorização](../../../../../docs/framework/wcf/samples/authorization-policy.md)
