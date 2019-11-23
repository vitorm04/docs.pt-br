---
title: Como criptografar elementos XML com certificados X.509
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET Framework], X.509 certificates
- cryptography [.NET Framework], X.509 certificates
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: 761f1c66-631c-47af-aa86-ad9c50cfa453
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d569d3c020e7329d987e957f181b34c8cfbf941a
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353855"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a>Como criptografar elementos XML com certificados X.509
Você pode usar as classes no namespace <xref:System.Security.Cryptography.Xml> para criptografar um elemento em um documento XML.  A criptografia XML é uma maneira padrão de trocar ou armazenar dados XML criptografados, sem se preocupar com os dados que estão sendo facilmente lidos.  Para obter mais informações sobre o padrão de criptografia XML, consulte a especificação do World Wide Web Consortium (W3C) para criptografia XML localizada em <https://www.w3.org/TR/xmldsig-core/>.  
  
 Você pode usar a criptografia XML para substituir qualquer elemento XML ou documento por um <`EncryptedData`elemento > que contenha os dados XML criptografados. O elemento <`EncryptedData`> pode conter subelementos que incluem informações sobre as chaves e os processos usados durante a criptografia.  A criptografia XML permite que um documento contenha vários elementos criptografados e permite que um elemento seja criptografado várias vezes.  O exemplo de código neste procedimento mostra como criar um elemento <`EncryptedData`> juntamente com vários outros subelementos que você pode usar posteriormente durante a descriptografia.  
  
 Este exemplo criptografa um elemento XML usando duas chaves. Ele gera um certificado X. 509 de teste usando a [ferramenta de criação de certificado (MakeCert. exe)](/windows/desktop/SecCrypto/makecert) e salva o certificado em um repositório de certificados. Em seguida, o exemplo recupera programaticamente o certificado e o usa para criptografar um elemento XML usando o método <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A>. Internamente, o método <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> cria uma chave de sessão separada e a usa para criptografar o documento XML. Esse método criptografa a chave de sessão e a salva junto com o XML criptografado em um novo <`EncryptedData`elemento >.  
  
 Para descriptografar o elemento XML, basta chamar o método <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A>, que recupera automaticamente o certificado X. 509 da loja e executa a descriptografia necessária.  Para obter mais informações sobre como descriptografar um elemento XML que foi criptografado usando esse procedimento, consulte [como: descriptografar elementos XML com certificados X. 509](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).  
  
 Este exemplo é apropriado para situações em que vários aplicativos precisam compartilhar dados criptografados ou onde um aplicativo precisa salvar dados criptografados entre os horários em que é executado.  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a>Para criptografar um elemento XML com um certificado X.509  
  
1. Use a [ferramenta de criação de certificado (MakeCert. exe)](/windows/desktop/SecCrypto/makecert) para gerar um certificado X. 509 de teste e colocá-lo no repositório de usuários local. Você deve gerar uma chave do Exchange e deve tornar a chave exportável. Execute o seguinte comando:  
  
    ```console  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2. Crie um objeto <xref:System.Security.Cryptography.X509Certificates.X509Store> e inicialize-o para abrir o armazenamento do usuário atual.  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3. Abra o repositório no modo somente leitura.  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4. Inicializar um <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> com todos os certificados no repositório.  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5. Enumere os certificados no repositório e localize o certificado com o nome apropriado.  Neste exemplo, o certificado é nomeado `"CN=XML_ENC_TEST_CERT"`.  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6. Feche o repositório após a localização do certificado.  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7. Crie um objeto de <xref:System.Xml.XmlDocument> carregando um arquivo XML do disco.  O objeto <xref:System.Xml.XmlDocument> contém o elemento XML a ser criptografado.  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8. Localize o elemento especificado no objeto <xref:System.Xml.XmlDocument> e crie um novo objeto <xref:System.Xml.XmlElement> para representar o elemento que você deseja criptografar.  Neste exemplo, o elemento `"creditcard"` é criptografado.  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. Crie uma nova instância da classe <xref:System.Security.Cryptography.Xml.EncryptedXml> e use-a para criptografar o elemento especificado usando o certificado X. 509.  O método <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> retorna o elemento Encrypted como um objeto <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. Substitua o elemento do objeto <xref:System.Xml.XmlDocument> original pelo elemento <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. Salve o objeto <xref:System.Xml.XmlDocument>.  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 Este exemplo pressupõe que um arquivo chamado `"test.xml"` exista no mesmo diretório que o programa compilado.  Ele também pressupõe que `"test.xml"` contém um elemento `"creditcard"`.  Você pode inserir o XML a seguir em um arquivo chamado `test.xml` e usá-lo com este exemplo.  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
  
- Para compilar este exemplo, você precisa incluir uma referência a `System.Security.dll`.  
  
- Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>e <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 O certificado X. 509 usado neste exemplo é apenas para fins de teste.  Os aplicativos devem usar um certificado X. 509 gerado por uma autoridade de certificação confiável ou usar um certificado gerado pelo servidor de certificado do Microsoft Windows.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Security.Cryptography.Xml>
- [Como descriptografar elementos XML com certificados X.509](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)
