---
title: Como assinar documento XML com assinaturas digitais
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signatures, XML signing
- System.Security.Cryptography.SignedXml class
- digital signatures, XML signing
- System.Security.Cryptography.RSACryptoServiceProvider class
- XML digital signatures
- XML signing
- signing XML
ms.assetid: 99692ac1-d8c9-42d7-b1bf-2737b01037e4
ms.openlocfilehash: 0df036b3336527f3cc0e48d9a7ec835ab9f1cf4a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706039"
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a>Como assinar documento XML com assinaturas digitais
Você pode usar as classes no namespace <xref:System.Security.Cryptography.Xml> para assinar um documento XML ou parte de um documento XML com uma assinatura digital.  As assinaturas digitais XML (XMLDSIG) permitem que você verifique se os dados não foram alterados após sua assinatura.  Para obter mais informações sobre o padrão XMLDSIG, consulte a [sintaxe e o processamento da assinatura XML](https://www.w3.org/TR/xmldsig-core/)de recomendação do World Wide Web CONSORTIUM (W3C).  
  
 O exemplo de código neste procedimento demonstra como assinar digitalmente um documento XML inteiro e anexar a assinatura ao documento em um elemento <`Signature`>.  O exemplo cria uma chave de assinatura RSA, adiciona a chave a um contêiner de chave segura e, em seguida, usa a chave para assinar digitalmente um documento XML.  A chave pode ser recuperada para verificar a assinatura digital XML ou pode ser usada para assinar outro documento XML.  
  
 Para obter informações sobre como verificar uma assinatura digital XML que foi criada usando esse procedimento, consulte [como verificar as assinaturas digitais de documentos XML](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md).  
  
### <a name="to-digitally-sign-an-xml-document"></a>Para assinar digitalmente um documento XML  
  
1. Crie um objeto <xref:System.Security.Cryptography.CspParameters> e especifique o nome do contêiner de chave.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2. Gere uma chave assimétrica usando a classe <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  A chave é salva automaticamente no contêiner de chave quando você passa o objeto <xref:System.Security.Cryptography.CspParameters> para o construtor da classe <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  Essa chave será usada para assinar o documento XML.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3. Crie um objeto de <xref:System.Xml.XmlDocument> carregando um arquivo XML do disco.  O objeto <xref:System.Xml.XmlDocument> contém o elemento XML a ser criptografado.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4. Crie um novo objeto <xref:System.Security.Cryptography.Xml.SignedXml> e passe o objeto <xref:System.Xml.XmlDocument> para ele.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5. Adicione a chave RSA de assinatura ao objeto <xref:System.Security.Cryptography.Xml.SignedXml>.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6. Crie um objeto <xref:System.Security.Cryptography.Xml.Reference> que descreva o que assinar.  Para assinar todo o documento, defina a propriedade <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> como `""`.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7. Adicione um objeto <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> ao objeto <xref:System.Security.Cryptography.Xml.Reference>.  Uma transformação permite que o verificador represente os dados XML da maneira idêntica usada pelo signatário.  Os dados XML podem ser representados de maneiras diferentes, portanto, essa etapa é vital para a verificação.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8. Adicione o objeto <xref:System.Security.Cryptography.Xml.Reference> ao objeto <xref:System.Security.Cryptography.Xml.SignedXml>.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. Computar a assinatura chamando o método <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A>.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. Recupere a representação XML da assinatura (um <`Signature`elemento >) e salve-a em um novo objeto <xref:System.Xml.XmlElement>.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. Acrescente o elemento ao objeto <xref:System.Xml.XmlDocument>.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. Salve o documento.  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo pressupõe que um arquivo chamado `test.xml` exista no mesmo diretório que o programa compilado.  Você pode inserir o XML a seguir em um arquivo chamado `test.xml` e usá-lo com este exemplo.  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToSignXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToSignXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
  
- Para compilar este exemplo, você precisa incluir uma referência a `System.Security.dll`.  
  
- Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>e <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Nunca armazene ou transfira a chave privada de um par de chaves assimétricas em texto não criptografado.  Para obter mais informações sobre chaves de criptografia simétrica e assimétrica, consulte [gerando chaves para criptografia e descriptografia](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nunca incorpore uma chave privada diretamente em seu código-fonte.  Chaves inseridas podem ser facilmente lidas de um assembly usando o [ILDASM. exe (desmontador Il)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ou abrindo o assembly em um editor de texto como o bloco de notas.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Security.Cryptography.Xml>
- [Como verificar as assinaturas digitais de documentos XML](../../../docs/standard/security/how-to-verify-the-digital-signatures-of-xml-documents.md)
