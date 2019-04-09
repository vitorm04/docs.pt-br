---
title: 'Como: especificar o tipo de credencial de cliente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: 1138f0fe955782c71076d5c15c236d1d4ebbec01
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59185049"
---
# <a name="how-to-specify-the-client-credential-type"></a>Como: especificar o tipo de credencial de cliente
Depois de definir um modo de segurança (transporte ou mensagem), você tem a opção de configuração de tipo de credencial de cliente. Esta propriedade especifica o tipo de credencial que o cliente deve fornecer para o serviço para autenticação. Para obter mais informações sobre como definir o modo de segurança (uma etapa necessária antes de definir tipo de credencial de cliente), consulte [como: Definir o modo de segurança](../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
### <a name="to-set-the-client-credential-type-in-code"></a>Definir tipo de credencial de cliente no código  
  
1.  Crie uma instância de associação que serão usadas pelo serviço. Este exemplo usa o <xref:System.ServiceModel.WSHttpBinding> associação.  
  
2.  Defina a propriedade <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> com um valor apropriado. Este exemplo usa o modo de mensagem.  
  
3.  Defina a propriedade <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> com um valor apropriado. Este exemplo define-o para usar a autenticação do Windows (<xref:System.ServiceModel.MessageCredentialType.Windows>).  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a>Para definir o tipo de credencial de cliente na configuração  
  
1.  Adicionar um [ \<System. ServiceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento ao arquivo de configuração.  
  
2.  Como um elemento filho, adicione uma [ \<associações >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elemento.  
  
3.  Adicione uma associação apropriada. Este exemplo usa o [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elemento.  
  
4.  Adicionar um [ \<associação >](../../../docs/framework/misc/binding.md) elemento e defina o `name` de atributo para um valor apropriado. Este exemplo usa o nome "SecureBinding".  
  
5.  Adicionar um `<security>` associação. Defina o `mode` de atributo para um valor apropriado. Este exemplo define como `"Message"`.  
  
6.  Adicione uma `<message>` ou `<transport>` elemento, conforme determinado pelo modo de segurança. Defina o `clientCredentialType` de atributo para um valor apropriado. Este exemplo usa `"Windows"`.  
  
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

- [Serviços de segurança](../../../docs/framework/wcf/securing-services.md)
- [Como: definir o modo de segurança](../../../docs/framework/wcf/how-to-set-the-security-mode.md)
