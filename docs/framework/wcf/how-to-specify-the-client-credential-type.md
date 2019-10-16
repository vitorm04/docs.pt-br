---
title: Como especificar o tipo de credencial de cliente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: d62011728b6b03023ef4039480cea8dfa0ec8f02
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321293"
---
# <a name="how-to-specify-the-client-credential-type"></a>Como especificar o tipo de credencial de cliente
Depois de definir um modo de segurança (transporte ou mensagem), você tem a opção de definir o tipo de credencial do cliente. Essa propriedade especifica o tipo de credencial que o cliente deve fornecer ao serviço para autenticação. Para obter mais informações sobre como definir o modo de segurança (uma etapa necessária antes de definir o tipo de credencial do cliente), consulte [como: definir o modo de segurança](how-to-set-the-security-mode.md).  
  
### <a name="to-set-the-client-credential-type-in-code"></a>Para definir o tipo de credencial do cliente no código  
  
1. Crie uma instância da associação que será usada pelo serviço. Este exemplo usa a associação <xref:System.ServiceModel.WSHttpBinding>.  
  
2. Defina a propriedade <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> com um valor apropriado. Este exemplo usa o modo de mensagem.  
  
3. Defina a propriedade <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> com um valor apropriado. Este exemplo o define para usar a autenticação do Windows (<xref:System.ServiceModel.MessageCredentialType.Windows>).  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a>Para definir o tipo de credencial do cliente na configuração  
  
1. Adicione um elemento de [> @no__t. ServiceModel](../configure-apps/file-schema/wcf/system-servicemodel.md) ao arquivo de configuração.  
  
2. Como um elemento filho, adicione um elemento de [> \<bindings](../configure-apps/file-schema/wcf/bindings.md) .  
  
3. Adicione uma associação apropriada. Este exemplo usa o elemento [\<wsHttpBinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) .  
  
4. Adicione um elemento de [> \<binding](../misc/binding.md) e defina o atributo `name` com um valor apropriado. Este exemplo usa o nome "Securebinding".  
  
5. Adicione uma associação `<security>`. Defina o atributo `mode` como um valor apropriado. Este exemplo o define como `"Message"`.  
  
6. Adicione um elemento `<message>` ou `<transport>`, conforme determinado pelo modo de segurança. Defina o atributo `clientCredentialType` como um valor apropriado. Este exemplo usa `"Windows"`.  
  
    ```xml  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Protegendo serviços](securing-services.md)
- [Como definir o modo de segurança](how-to-set-the-security-mode.md)
