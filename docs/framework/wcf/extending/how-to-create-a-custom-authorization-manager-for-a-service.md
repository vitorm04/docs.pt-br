---
title: 'Como: criar gerenciador de autorização personalizado para um serviço'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
ms.openlocfilehash: ffdfe41db05eb5f2dd55a233f8ed646401777d0f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040295"
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a>Como: criar gerenciador de autorização personalizado para um serviço

A infraestrutura do modelo de identidade no Windows Communication Foundation (WCF) dá suporte a um modelo de autorização baseado em declarações extensível. As declarações são extraídas de tokens e, opcionalmente, processadas por políticas de <xref:System.IdentityModel.Policy.AuthorizationContext>autorização personalizadas e, em seguida, colocadas em um. Um Gerenciador de autorização examina as declarações no <xref:System.IdentityModel.Policy.AuthorizationContext> para tomar decisões de autorização.

Por padrão, as decisões de autorização são feitas <xref:System.ServiceModel.ServiceAuthorizationManager> pela classe; no entanto, essas decisões podem ser substituídas por meio da criação de um Gerenciador de autorização personalizado. Para criar um Gerenciador de autorização personalizado, crie uma classe que derive <xref:System.ServiceModel.ServiceAuthorizationManager> de e <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> implemente o método. As <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> decisões de autorização são feitas no método, que `true` retorna quando o acesso é `false` concedido e quando o acesso é negado.

Se a decisão de autorização depender do conteúdo do corpo da mensagem, use o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> método.

Devido a problemas de desempenho, se possível, você deve reprojetar seu aplicativo para que a decisão de autorização não exija acesso ao corpo da mensagem.

O registro do Gerenciador de autorização personalizado para um serviço pode ser feito no código ou na configuração.

### <a name="to-create-a-custom-authorization-manager"></a>Para criar um Gerenciador de autorização personalizado

1. Derive uma classe da <xref:System.ServiceModel.ServiceAuthorizationManager> classe.

    [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
    [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]

2. Substituir o método <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29>.

    Use o <xref:System.ServiceModel.OperationContext> que é passado para o <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> método para tomar decisões de autorização.

    O exemplo de código a seguir <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> usa o método para localizar a `http://www.contoso.com/claims/allowedoperation` declaração personalizada para tomar uma decisão de autorização.

    [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
    [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]

### <a name="to-register-a-custom-authorization-manager-using-code"></a>Para registrar um Gerenciador de autorização personalizado usando código

1. Crie uma instância do Gerenciador de autorização personalizado e atribua-a à <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> propriedade.

    O <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> pode ser acessado usando <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> a propriedade.

    O exemplo de código a seguir `MyServiceAuthorizationManager` registra o Gerenciador de autorização personalizado.

    [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
    [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]

### <a name="to-register-a-custom-authorization-manager-using-configuration"></a>Para registrar um Gerenciador de autorização personalizado usando a configuração

1. Abra o arquivo de configuração para o serviço.

2. Adicione um [ \<> de autorização](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) para os [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).

    Para a [ \<> de autorização](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), adicione um `serviceAuthorizationManagerType` atributo e defina seu valor para o tipo que representa o Gerenciador de autorização personalizado.

3. Adicione uma associação que proteja a comunicação entre o cliente e o serviço.

    A associação escolhida para essa comunicação determina as declarações que são adicionadas ao <xref:System.IdentityModel.Policy.AuthorizationContext>, que o Gerenciador de autorização personalizado usa para tomar decisões de autorização. Para obter mais detalhes sobre as associações fornecidas pelo sistema, consulte [associações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md).

4. Associe o comportamento a um ponto de extremidade de serviço, adicionando um elemento de [ \<> de serviço](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) e defina `behaviorConfiguration` o valor do atributo como o valor do atributo Name para o [ \<elemento de comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) .

    Para obter mais informações sobre como configurar um ponto de [extremidade de serviço, consulte Como: Criar um ponto de extremidade de](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)serviço na configuração.

    O exemplo de código a seguir registra o Gerenciador `Samples.MyServiceAuthorizationManager`de autorização personalizado.

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
    > Observe que, quando você especifica o serviceAuthorizationManagerType, a cadeia de caracteres deve conter o nome do tipo totalmente qualificado. uma vírgula e o nome do assembly no qual o tipo é definido. Se você sair do nome do assembly, o WCF tentará carregar o tipo de System. ServiceModel. dll.

## <a name="example"></a>Exemplo

O exemplo de código a seguir demonstra uma implementação básica <xref:System.ServiceModel.ServiceAuthorizationManager> de uma classe que inclui <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> a substituição do método. O código de exemplo examina o <xref:System.IdentityModel.Policy.AuthorizationContext> para uma declaração personalizada e retorna `true` quando o recurso dessa declaração personalizada corresponde ao valor da ação do <xref:System.ServiceModel.OperationContext>. Para obter uma implementação mais completa de <xref:System.ServiceModel.ServiceAuthorizationManager> uma classe, consulte [política de autorização](../../../../docs/framework/wcf/samples/authorization-policy.md).

[!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
[!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Política de autorização](../../../../docs/framework/wcf/samples/authorization-policy.md)
