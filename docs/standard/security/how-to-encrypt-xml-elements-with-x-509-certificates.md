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
ms.openlocfilehash: b3d61fcbab4c905ba675e08346ea7cb28b0e710c
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845496"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a>Como criptografar elementos XML com certificados X.509
Você pode usar as classes de <xref:System.Security.Cryptography.Xml> namespace para criptografar um elemento em um documento XML.  Criptografia de XML é uma maneira padrão para trocar ou armazenar dados XML criptografados, sem se preocupar com os dados que está sendo lidos com facilidade.  Para obter mais informações sobre o padrão de criptografia de XML, consulte a especificação do World Wide Web Consortium (W3C) para criptografia XML localizado em <https://www.w3.org/TR/xmldsig-core/>.  
  
 Você pode usar a criptografia XML para substituir qualquer elemento XML ou documento com um <`EncryptedData`> elemento que contém os dados XML criptografados. O <`EncryptedData`> elemento pode conter elementos sub que incluem informações sobre as chaves e os processos usados durante a criptografia.  Criptografia XML permite que um documento conter vários elementos criptografados e permite que um elemento a ser criptografado várias vezes.  O exemplo de código neste procedimento mostra como criar um <`EncryptedData`> elemento juntamente com vários outros subelementos que você pode usar mais tarde durante a descriptografia.  
  
 Este exemplo criptografa um elemento XML usando duas chaves.  Ele gera um certificado X.509 de teste usando o [ferramenta de criação de certificado (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) e salva o certificado em um repositório de certificados.  O exemplo, em seguida, por meio de programação recupera o certificado e usa-o para criptografar um elemento XML usando o <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> método.  Internamente, o <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> método cria uma chave de sessão separada e o utiliza para criptografar o documento XML. Esse método criptografa a chave de sessão e salva-o junto com o XML criptografado dentro de um novo <`EncryptedData`> elemento.  
  
 Para descriptografar o elemento XML, basta chamar o <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> método, que recupera o certificado X.509 do repositório automaticamente e executa a descriptografia necessária.  Para obter mais informações sobre como descriptografar um elemento XML que foi criptografado usando esse procedimento, consulte [como: descriptografar a elementos XML com certificados x. 509](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md).  
  
 Este exemplo é apropriado para situações em que vários aplicativos precisam compartilhar os dados criptografados ou qual o aplicativo precisa para salvar os dados criptografados entre os horários em que ele é executado.  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a>Para criptografar um elemento XML com um certificado X.509  
  
1.  Use o [ferramenta de criação de certificado (Makecert.exe)](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx) para gerar um certificado X.509 de teste e colocá-lo no repositório de usuário local.  Você deve gerar uma chave de troca e você deve fazer com que a chave exportável. Execute o seguinte comando:  
  
    ```  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2.  Criar um <xref:System.Security.Cryptography.X509Certificates.X509Store> do objeto e inicializá-lo para abrir o repositório do usuário atual.  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3.  Abra o repositório no modo somente leitura.  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4.  Inicializar um <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> com todos os certificados no repositório.  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5.  Enumerar os certificados no repositório e encontre o certificado com o nome apropriado.  Neste exemplo, o certificado é chamado `"CN=XML_ENC_TEST_CERT"`.  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6.  Feche o armazenamento depois que o certificado está localizado.  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7.  Criar um <xref:System.Xml.XmlDocument> objeto carregando um arquivo XML do disco.  O <xref:System.Xml.XmlDocument> objeto contém o elemento XML para criptografar.  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8.  Localize o elemento especificado na <xref:System.Xml.XmlDocument> do objeto e crie um novo <xref:System.Xml.XmlElement> objeto para representar o elemento que você deseja criptografar.  Neste exemplo, o `"creditcard"` elemento é criptografado.  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. Criar uma nova instância do <xref:System.Security.Cryptography.Xml.EncryptedXml> de classe e usá-lo para criptografar o elemento especificado usando o certificado X.509.  O <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> método retorna o elemento criptografado como um <xref:System.Security.Cryptography.Xml.EncryptedData> objeto.  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. Substitua o elemento do original <xref:System.Xml.XmlDocument> do objeto com o <xref:System.Security.Cryptography.Xml.EncryptedData> elemento.  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. Salve o <xref:System.Xml.XmlDocument> objeto.  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
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
  
 [!code-csharp[HowToEncryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Para compilar este exemplo, você precisa incluir uma referência ao `System.Security.dll`.  
  
-   Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, e <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 O certificado x. 509 usado neste exemplo é apenas a fins de teste.  Aplicativos devem usar um certificado X.509 gerado por uma autoridade de certificação confiável ou usar um certificado gerado pelo servidor de certificado do Microsoft Windows.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Security.Cryptography.Xml>  
- [Como descriptografar elementos XML com certificados X.509](../../../docs/standard/security/how-to-decrypt-xml-elements-with-x-509-certificates.md)
