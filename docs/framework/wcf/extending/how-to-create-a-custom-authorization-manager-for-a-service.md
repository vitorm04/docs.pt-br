---
title: "Como criar gerenciador de autorização personalizado para um serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1977a26f3185ad1ef85584b0da7d63826b7f93ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a>Como criar gerenciador de autorização personalizado para um serviço
A infraestrutura do modelo de identidade no [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] oferece suporte a um modelo de autorização extensível baseada em declarações. Declarações são extraídas de tokens e, opcionalmente, processadas por diretivas de autorização personalizada e, em seguida, são colocadas em um <xref:System.IdentityModel.Policy.AuthorizationContext>. Um Gerenciador de autorização examina as declarações de <xref:System.IdentityModel.Policy.AuthorizationContext> para tomar decisões de autorização.  
  
 Por padrão, as decisões de autorização são feitas a <xref:System.ServiceModel.ServiceAuthorizationManager> classe; no entanto essas decisões podem ser substituídos por criar uma autorização personalizada manager. Para criar uma autorização personalizada manager, crie uma classe que deriva de <xref:System.ServiceModel.ServiceAuthorizationManager> e implementar <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> método. Decisões de autorização são feitas no <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> método, que retorna `true` quando o acesso é concedido e `false` quando o acesso é negado.  
  
 Se a decisão de autorização depende do conteúdo do corpo da mensagem, use o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> método.  
  
 Devido a problemas de desempenho, se possível você deve recriar seu aplicativo para que a decisão de autorização não requer acesso ao corpo da mensagem.  
  
 Registro do Gerenciador de autorização personalizada para um serviço pode ser feito no código ou configuração.  
  
### <a name="to-create-a-custom-authorization-manager"></a>Para criar uma autorização personalizada manager  
  
1.  Derivar uma classe a partir de <xref:System.ServiceModel.ServiceAuthorizationManager> classe.  
  
     [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
     [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]  
  
2.  Substituir o método <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29>.  
  
     Use o <xref:System.ServiceModel.OperationContext> que é passado para o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> método para tomar decisões de autorização.  
  
     O seguinte exemplo de código usa o <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> método para encontrar a declaração personalizada `http://www.contoso.com/claims/allowedoperation` para tomar uma decisão de autorização.  
  
     [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
     [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]  
  
### <a name="to-register-a-custom-authorization-manager-using-code"></a>Para registrar um Gerenciador de autorização personalizada usando código  
  
1.  Criar uma instância da autorização personalizada Gerenciador e atribuí-la para o <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> propriedade.  
  
     O <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> podem ser acessados usando <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> propriedade.  
  
     O código a seguir exemplo registra o `MyServiceAuthorizationManager` Gerenciador de autorização personalizadas.  
  
     [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
     [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]  
  
### <a name="to-register-a-custom-authorization-manager-using-configuration"></a>Para registrar um Gerenciador de autorização personalizada usando a configuração  
  
1.  Abra o arquivo de configuração para o serviço.  
  
2.  Adicionar um [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) para o [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).  
  
     Para o [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), adicione um `serviceAuthorizationManagerType` de atributos e defina seu valor para o tipo que representa o Gerenciador de autorização personalizada.  
  
3.  Adicione uma associação que protege a comunicação entre o cliente e o serviço.  
  
     A associação que é escolhida para essa comunicação determina as declarações que são adicionadas para o <xref:System.IdentityModel.Policy.AuthorizationContext>, que usa o Gerenciador de autorização personalizada para tomar decisões de autorização. Para obter mais detalhes sobre as associações fornecidas pelo sistema, consulte [System-Provided associações](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
4.  Associar o comportamento de um ponto de extremidade de serviço, adicionando um [ \<service >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) elemento e defina o valor da `behaviorConfiguration` de atributo para o valor do atributo name para o [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elemento.  
  
     Para obter mais informações sobre como configurar um ponto de extremidade de serviço, consulte [como: criar um ponto de extremidade de serviço na configuração](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
     O exemplo de código a seguir registra o Gerenciador de autorização personalizada `Samples.MyServiceAuthorizationManager`.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service   
              name="Microsoft.ServiceModel.Samples.CalculatorService"  
              behaviorConfiguration="CalculatorServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
            <endpoint address=""  
                      binding="wsHttpBinding_Calculator"  
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <WSHttpBinding>  
           <binding name = "wsHttpBinding_Calculator">  
             <security mode="Message">  
               <message clientCredentialType="Windows"/>  
             </security>  
            </binding>  
          </WSHttpBinding>  
    </bindings>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="CalculatorServiceBehavior">  
              <serviceAuthorization serviceAuthorizationManagerType="Samples.MyServiceAuthorizationManager,MyAssembly" />  
             </behavior>  
         </serviceBehaviors>  
       </behaviors>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
    > [!WARNING]
    >  Observe que, quando você especificar serviceAuthorizationManagerType, a cadeia de caracteres deve conter o nome de tipo totalmente qualificado. uma vírgula e o nome do assembly no qual o tipo é definido. Se você omitir o nome do assembly, o WCF tentará carregar o tipo do System.ServiceModel.dll.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra uma implementação básica de um <xref:System.ServiceModel.ServiceAuthorizationManager> classe que inclui substituindo o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> método. O código de exemplo examina o <xref:System.IdentityModel.Policy.AuthorizationContext> para um personalizado de declaração e retorna `true` quando o recurso para essa declaração personalizada corresponde ao valor de ação do <xref:System.ServiceModel.OperationContext>. Para uma implementação mais completa de um <xref:System.ServiceModel.ServiceAuthorizationManager> de classe, consulte [política de autorização](../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
 [!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
 [!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [Política de autorização](../../../../docs/framework/wcf/samples/authorization-policy.md)  
 [Política de autorização](../../../../docs/framework/wcf/samples/authorization-policy.md)
