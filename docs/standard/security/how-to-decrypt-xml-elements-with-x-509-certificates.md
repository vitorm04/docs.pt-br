---
title: Como descriptografar elementos XML com certificados X.509
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- decryption
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: bd015722-d88d-408d-8ca8-e4e475c441ed
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 25a2fb441269508402263e103a6c6e1be2635406
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44140730"
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a>Como descriptografar elementos XML com certificados X.509
Você pode usar as classes de <xref:System.Security.Cryptography.Xml> namespace para criptografar e descriptografar um elemento dentro de um documento XML.  Criptografia de XML é uma maneira padrão para trocar ou armazenar dados XML criptografados, sem se preocupar com os dados que está sendo lidos com facilidade.  Para obter mais informações sobre o padrão de criptografia de XML, consulte a especificação do World Wide Web Consortium (W3C) para criptografia XML localizado em http://www.w3.org/TR/xmldsig-core/.  
  
 Este exemplo descriptografa um elemento XML que foi criptografado usando os métodos descritos em: [como: criptografar a elementos XML com certificados x. 509](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md).  Ele encontra um <`EncryptedData`> elemento, descriptografa o elemento e, em seguida, substitui o elemento por elemento XML de texto sem formatação original.  
  
 O exemplo de código neste procedimento descriptografa um elemento XML usando um certificado X.509 do repositório de certificados local da conta de usuário atual.  O exemplo usa o <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> método para recuperar o certificado x. 509 automaticamente e descriptografar a chave armazenada em uma sessão das <`EncryptedKey`> elemento da <`EncryptedData`> elemento.  O <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> método, em seguida, usa automaticamente a chave de sessão para descriptografar o elemento XML.  
  
 Este exemplo é apropriado para situações em que vários aplicativos precisam compartilhar os dados criptografados ou qual o aplicativo precisa para salvar os dados criptografados entre os horários em que ele é executado.  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a>Para descriptografar um elemento XML com um certificado X.509  
  
1.  Criar um <xref:System.Xml.XmlDocument> objeto carregando um arquivo XML do disco.  O <xref:System.Xml.XmlDocument> objeto contém o elemento XML ao descriptografar.  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2.  Criar um novo <xref:System.Security.Cryptography.Xml.EncryptedXml> objeto, passando o <xref:System.Xml.XmlDocument> objeto para o construtor.  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3.  Descriptografar o documento XML usando o <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> método.  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4.  Salve o <xref:System.Xml.XmlDocument> objeto.  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo supõe que um arquivo chamado `"test.xml"` existe no mesmo diretório que o programa compilado.  Ele também pressupõe que `"test.xml"` contém um `"creditcard"` elemento.  Você pode colocar o XML a seguir em um arquivo chamado `test.xml` e usá-lo com este exemplo.  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToDecryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Para compilar este exemplo, você precisa incluir uma referência ao `System.Security.dll`.  
  
-   Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, e <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 O certificado x. 509 usado neste exemplo é apenas a fins de teste.  Aplicativos devem usar um certificado X.509 gerado por uma autoridade de certificação confiável ou usar um certificado gerado pelo servidor de certificado do Microsoft Windows.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Security.Cryptography.Xml>  
- [Como criptografar elementos XML com certificados X.509](../../../docs/standard/security/how-to-encrypt-xml-elements-with-x-509-certificates.md)
