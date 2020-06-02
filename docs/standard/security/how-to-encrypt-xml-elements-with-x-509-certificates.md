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
ms.openlocfilehash: 9cdd8e52be11eeba86ec406510f40f1a08809ff8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277213"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a>Como criptografar elementos XML com certificados X.509
Você pode usar as classes no <xref:System.Security.Cryptography.Xml> namespace para criptografar um elemento em um documento XML.  A criptografia XML é uma maneira padrão de trocar ou armazenar dados XML criptografados, sem se preocupar com os dados que estão sendo facilmente lidos.  Para obter mais informações sobre o padrão de criptografia XML, consulte a especificação do World Wide Web Consortium (W3C) para criptografia XML localizada em <https://www.w3.org/TR/xmldsig-core/> .  
  
 Você pode usar a criptografia XML para substituir qualquer elemento XML ou documento por um `EncryptedData` elemento <> que contenha os dados XML criptografados. O `EncryptedData` elemento <> pode conter subelementos que incluem informações sobre as chaves e os processos usados durante a criptografia.  A criptografia XML permite que um documento contenha vários elementos criptografados e permite que um elemento seja criptografado várias vezes.  O exemplo de código neste procedimento mostra como criar um elemento de <`EncryptedData`> juntamente com vários outros subelementos que você pode usar posteriormente durante a descriptografia.  
  
 Este exemplo criptografa um elemento XML usando duas chaves. Ele gera um certificado X. 509 de teste usando a [ferramenta de criação de certificado (MakeCert. exe)](/windows/desktop/SecCrypto/makecert) e salva o certificado em um repositório de certificados. Em seguida, o exemplo recupera programaticamente o certificado e o usa para criptografar um elemento XML usando o <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> método. Internamente, o <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> método cria uma chave de sessão separada e a usa para criptografar o documento XML. Esse método criptografa a chave de sessão e salva-a junto com o XML criptografado em um novo `EncryptedData` elemento <>.  
  
 Para descriptografar o elemento XML, basta chamar o <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> método, que recupera automaticamente o certificado X. 509 do repositório e realiza a descriptografia necessária.  Para obter mais informações sobre como descriptografar um elemento XML que foi criptografado usando esse procedimento, consulte [como: descriptografar elementos XML com certificados X. 509](how-to-decrypt-xml-elements-with-x-509-certificates.md).  
  
 Este exemplo é apropriado para situações em que vários aplicativos precisam compartilhar dados criptografados ou onde um aplicativo precisa salvar dados criptografados entre os horários em que é executado.  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a>Para criptografar um elemento XML com um certificado X.509  
  
1. Use a [ferramenta de criação de certificado (MakeCert. exe)](/windows/desktop/SecCrypto/makecert) para gerar um certificado X. 509 de teste e colocá-lo no repositório de usuários local. Você deve gerar uma chave do Exchange e deve tornar a chave exportável. Execute o comando a seguir:  
  
    ```console  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2005 -e 01/01/2010 -sky exchange -ss my  
    ```  
  
2. Crie um <xref:System.Security.Cryptography.X509Certificates.X509Store> objeto e inicialize-o para abrir o repositório de usuários atual.  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3. Abra o repositório no modo somente leitura.  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4. Inicialize um <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection> com todos os certificados no repositório.  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5. Enumere os certificados no repositório e localize o certificado com o nome apropriado.  Neste exemplo, o certificado é nomeado `"CN=XML_ENC_TEST_CERT"` .  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6. Feche o repositório após a localização do certificado.  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7. Crie um <xref:System.Xml.XmlDocument> objeto carregando um arquivo XML do disco.  O <xref:System.Xml.XmlDocument> objeto contém o elemento XML a ser criptografado.  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8. Localize o elemento especificado no <xref:System.Xml.XmlDocument> objeto e crie um novo <xref:System.Xml.XmlElement> objeto para representar o elemento que você deseja criptografar.  Neste exemplo, o `"creditcard"` elemento é criptografado.  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. Crie uma nova instância da <xref:System.Security.Cryptography.Xml.EncryptedXml> classe e use-a para criptografar o elemento especificado usando o certificado X. 509.  O <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> método retorna o elemento Encrypted como um <xref:System.Security.Cryptography.Xml.EncryptedData> objeto.  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. Substitua o elemento do objeto original <xref:System.Xml.XmlDocument> pelo <xref:System.Security.Cryptography.Xml.EncryptedData> elemento.  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. Salve o <xref:System.Xml.XmlDocument> objeto.  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo pressupõe que um arquivo chamado `"test.xml"` existe no mesmo diretório que o programa compilado.  Ele também pressupõe que `"test.xml"` contém um `"creditcard"` elemento.  Você pode inserir o XML a seguir em um arquivo chamado `test.xml` e usá-lo com este exemplo.  
  
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
  
- Para compilar este exemplo, você precisa incluir uma referência para `System.Security.dll` .  
  
- Inclua os seguintes namespaces: <xref:System.Xml> , <xref:System.Security.Cryptography> e <xref:System.Security.Cryptography.Xml> .  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 O certificado X. 509 usado neste exemplo é apenas para fins de teste.  Os aplicativos devem usar um certificado X. 509 gerado por uma autoridade de certificação confiável ou usar um certificado gerado pelo servidor de certificado do Microsoft Windows.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Security.Cryptography.Xml>
- [Como descriptografar elementos XML com certificados X.509](how-to-decrypt-xml-elements-with-x-509-certificates.md)
