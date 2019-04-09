---
title: 'Como: definir uma confirmação de assinatura'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
ms.openlocfilehash: 78ad6a88d5c123272e1796f1a75e2bd226bfc8f5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176157"
---
# <a name="how-to-set-up-a-signature-confirmation"></a>Como: definir uma confirmação de assinatura
*Confirmação de assinatura* é um mecanismo para um iniciador de mensagem garantir que uma resposta recebida foi gerada em resposta à mensagem original do remetente. Confirmação de assinatura é definida na especificação WS-Security 1.1. Se um ponto de extremidade dá suporte a WS-Security 1.0, você não pode usar a confirmação de assinatura.  
  
 Os procedimentos a seguir especificam como habilitar a confirmação de assinatura usando um <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Você pode usar o mesmo procedimento com um <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>. O procedimento tem como base as etapas básicas encontradas em [como: Criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-enable-signature-confirmation-in-code"></a>Para habilitar a confirmação de assinatura no código  
  
1.  Crie uma instância da classe <xref:System.ServiceModel.Channels.BindingElementCollection>.  
  
2.  Criar uma instância da <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> classe.  
  
3.  Defina o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> como `true`.  
  
4.  Adicione o elemento de segurança para a coleção de associação.  
  
5.  Criar uma ligação personalizada, conforme especificado na [como: Criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-enable-signature-confirmation-in-configuration"></a>Para habilitar a confirmação de assinatura na configuração  
  
1.  Adicionar um `<customBinding>` elemento para o `<bindings>` seção do arquivo de configuração.  
  
2.  Adicionar um `<binding>` elemento e defina o nome de atributo para um valor apropriado.  
  
3.  Adicione um elemento de codificação apropriado. O exemplo a seguir adiciona um `<TextMessageEncoding>` elemento.  
  
4.  Adicionar um `<security>` elemento filho e defina o `requireSignatureConfirmation` atributo `true`.  
  
5.  Opcional. Para habilitar a confirmação de assinatura durante a inicialização, adicione uma [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) elemento filho e defina o `equireSignatureConfirmation` atributo `true`.  
  
6.  Adicione um elemento de transporte apropriado. O exemplo a seguir adiciona uma [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="SignatureConfirmationBinding">  
          <security requireSignatureConfirmation="true">  
            <secureConversationBootstrap requireSignatureConfirmation="true" />  
              </security>  
           <textMessageEncoding />  
             <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="example"></a>Exemplo  
 O código a seguir cria uma instância das <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> e define o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> propriedade `true`. Observe que este exemplo usa o `<secureConversationBootstrap>` elemento mostrado no exemplo anterior. Este exemplo demonstra a confirmação de assinatura ao usar um token do Windows (Kerberos protocol). Nesse caso, a assinatura do cliente é retornada em todas as respostas do serviço e é confirmada pelo cliente.  
  
 [!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
 [!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>
- [Como: criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Como: criar um SecurityBindingElement para um modo de autenticação especificado](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
