---
title: 'Como: definir a distorção máxima do relógio'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
ms.openlocfilehash: e487da6316ec381c2009ee33575848dd80df8ab2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076622"
---
# <a name="how-to-set-a-max-clock-skew"></a>Como: definir a distorção máxima do relógio
Funções de tempo crítico podem ser derailed se as configurações do relógio em dois computadores são diferentes. Para atenuar essa possibilidade, você pode definir as `MaxClockSkew` propriedade para um <xref:System.TimeSpan>. Essa propriedade está disponível em duas classes:  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
>  Importante para uma conversa segura, altera o `MaxClockSkew` propriedade deve ser feita quando o cliente ou serviço é a ser inicializado. Para fazer isso, você deve definir a propriedade sobre a <xref:System.ServiceModel.Channels.SecurityBindingElement> retornado pelo <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.  
  
 Para alterar a propriedade em uma das associações fornecidas pelo sistema, você deve encontrar o elemento de associação de segurança na coleção de associações e definir o `MaxClockSkew` propriedade para um novo valor. Duas classes derivam a <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> e <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Ao recuperar a associação de segurança da coleção, você deve converter para um desses tipos para definir corretamente o `MaxClockSkew` propriedade. O exemplo a seguir usa uma <xref:System.ServiceModel.WSHttpBinding>, que usa o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>. Para obter uma lista que especifica qual tipo de associação de segurança para usar em cada associação fornecida pelo sistema, consulte [System-Provided associações](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
### <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a>Para criar uma associação personalizada com um novo relógio distorcer o valor em código  
  
1.  > [!WARNING]
    >  Observe a adicionar referências aos namespaces a seguir em seu código: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, e <xref:System.ServiceModel.Security.Tokens>.  
  
     Criar uma instância de um <xref:System.ServiceModel.WSHttpBinding> de classe e definir seu modo de segurança <xref:System.ServiceModel.SecurityMode.Message>.  
  
2.  Criar uma nova instância dos <xref:System.ServiceModel.Channels.BindingElementCollection> classe chamando o <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> método.  
  
3.  Use o <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> método da <xref:System.ServiceModel.Channels.BindingElementCollection> classe para localizar o elemento de associação de segurança.  
  
4.  Ao usar o <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> método, convertido para o tipo real. O exemplo a seguir conversões até a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> tipo.  
  
5.  Defina o <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> propriedade no elemento de associação de segurança.  
  
6.  Criar um <xref:System.ServiceModel.ServiceHost> com um endereço básico e o tipo de serviço apropriado.  
  
7.  Use o <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> método para adicionar um ponto de extremidade e incluem o <xref:System.ServiceModel.Channels.CustomBinding>.  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
### <a name="to-set-the-maxclockskew-in-configuration"></a>Para definir o MaxClockSkew na configuração  
  
1.  Criar uma [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) no [ \<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) seção do elemento.  
  
2.  Criar uma [ \<associação >](../../../../docs/framework/misc/binding.md) elemento e defina o `name` de atributo para um valor apropriado. O exemplo a seguir define como `MaxClockSkewBinding`.  
  
3.  Adicione um elemento de codificação. O exemplo a seguir adiciona uma [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
4.  Adicionar um [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento e defina o `authenticationMode` de atributo para uma configuração apropriada. O exemplo a seguir defina o atributo como `Kerberos` para especificar que o serviço usa a autenticação do Windows.  
  
5.  Adicionar um [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) e defina as `maxClockSkew` de atributo para um valor na forma de `"##:##:##"`. O exemplo a seguir define a 7 minutos. Opcionalmente, adicione uma [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) e defina o `maxClockSkew` de atributo para uma configuração apropriada.  
  
6.  Adicione um elemento de transporte. O exemplo a seguir usa uma [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
7.  Para uma conversa segura, as configurações de segurança devem ocorrer no bootstrap na [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) elemento.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="MaxClockSkewBinding">  
            <textMessageEncoding />  
            <security authenticationMode="Kerberos">  
               <localClientSettings maxClockSkew="00:07:00" />  
               <localServiceSettings maxClockSkew="00:07:00" />  
               <secureConversationBootstrap>  
                  <localClientSettings maxClockSkew="00:30:00" />  
                  <localServiceSettings maxClockSkew="00:30:00" />  
               </secureConversationBootstrap>  
            </security>  
            <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Como: criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
