---
title: Criar um cabeçalho personalizado que é assinado e- ou criptografado
ms.date: 03/30/2017
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
ms.openlocfilehash: 4770d650cba5c182aa56d9ac7afa39e585512d4b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a>Criar um cabeçalho personalizado que é assinado e- ou criptografado
Ao chamar um serviço WCF não usando um cliente WCF, às vezes, é necessário usar cabeçalhos SOAP personalizados. Há um bug de conversão em formato canônico no WCF que impede a trabalhar com um serviço WCF não cabeçalhos personalizados que são assinados e criptografados. O problema é causado pela concessão incorreta de namespaces XML padrão. Isso só será um problema ao chamar serviços WCF não com cabeçalhos personalizados que são assinados e/ou criptografados.  Quando o serviço recebe a mensagem que contém o cabeçalho personalizado assinado e/ou criptografado não é possível verificar a assinatura. Essa solução alternativa evita o erro de conversão em formato canônico, permite a interoperabilidade com serviços WCF não, mas não impede que a interoperabilidade com serviços WCF.  
  
## <a name="defining-the-custom-header"></a>Definindo o cabeçalho personalizado  
 Cabeçalhos personalizados são definidos com a definição de um contrato de mensagem e marcar os membros que deve ser enviado como cabeçalhos com um <xref:System.ServiceModel.MessageHeaderAttribute> atributo. Para solucionar o erro de conversão em formato canônico, você deve garantir que o serializador XML declara o namespace do cabeçalho personalizado com um prefixo, em vez de uma declaração de namespace padrão. O código a seguir mostra como definir o tipo de dados que será usado como um cabeçalho de mensagem com a declaração de namespace correto.  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("svcutil", "3.0.4506.648")]  
[System.SerializableAttribute()]  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.ComponentModel.DesignerCategoryAttribute("code")]  
[System.Xml.Serialization.XmlTypeAttribute(AnonymousType=true, Namespace="http://www.example.org/getMessage/")]  
public partial class msgHeaderElement  
{  
   // Define the XML namespace and force it to use an ‘h’ prefix  
    [System.Xml.Serialization.XmlNamespaceDeclarations]  
    public System.Xml.Serialization.XmlSerializerNamespaces _xsns = new System.Xml.Serialization.XmlSerializerNamespaces(new System.Xml.XmlQualifiedName[] { new System.Xml.XmlQualifiedName("h", "http://www.example.org/getMessage/") });  
  
    private string msgHeaderInputField;  
  [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified, Order=0)]  
    public string msgHeaderInput  
    {  
        get  
        {  
            return this.msgHeaderInputField;  
        }  
        set  
        {  
            this.msgHeaderInputField = value;  
        }  
    }  
}  
```  
  
 Esse código declara um novo tipo denominado `msgHeaderElement` que será serializado com o serializador XML. Quando uma instância desse tipo é serializada, ela definirá um namespace com um prefixo 'h', portanto contornar o erro de conversão em formato canônico.  O contrato de mensagem, em seguida, define uma instância de `msgHeaderElement` e marcá-la com o <xref:System.ServiceModel.MessageHeaderAttribute> atributo conforme mostrado no exemplo a seguir.  
  
```  
[MessageContract]  
public  class MyMessageContract  
{  
   // other message contents...  
   [MessageHeader(ProductionLevel=ProtectionLevel.EncryptAndSign)]  
   public msgHeaderElement;  
   // other message contents...  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Contrato de mensagem padrão](../../../../docs/framework/wcf/samples/default-message-contract.md)  
 [Contratos de mensagem](../../../../docs/framework/wcf/samples/message-contracts.md)  
 [Usando contratos de mensagem](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)
