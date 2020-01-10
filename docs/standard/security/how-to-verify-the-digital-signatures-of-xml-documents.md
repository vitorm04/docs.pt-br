---
title: Como verificar as assinaturas digitais de documentos XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.SignedXml class
- signatures, cryptographic
- System.Security.Cryptography.RSACryptoServiceProvider class
- verifying signatures
- checking signatures
- XML digital signatures
- digital signatures, verifying
ms.assetid: a4d5ceb1-b9f5-47e8-9e4a-a2b39110002f
ms.openlocfilehash: 5d562c23d3b0fd7eda5dc273932ada77709641a1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706000"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a>Como verificar as assinaturas digitais de documentos XML
Você pode usar as classes no namespace <xref:System.Security.Cryptography.Xml> para verificar os dados XML assinados com uma assinatura digital. As assinaturas digitais XML (XMLDSIG) permitem que você verifique se os dados não foram alterados após sua assinatura. Para obter mais informações sobre o padrão XMLDSIG, consulte a especificação do World Wide Web Consortium (W3C) em <https://www.w3.org/TR/xmldsig-core/>.
  
 O exemplo de código neste procedimento demonstra como verificar uma assinatura digital XML contida em um elemento <`Signature`>.  O exemplo recupera uma chave pública RSA de um contêiner de chave e, em seguida, usa a chave para verificar a assinatura.  
  
 Para obter informações sobre como criar uma assinatura digital que pode ser verificada usando essa técnica, consulte [como assinar documentos XML com assinaturas digitais](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a>Para verificar a assinatura digital de um documento XML  
  
1. Para verificar o documento, você deve usar a mesma chave assimétrica que foi usada para assinatura.  Crie um objeto <xref:System.Security.Cryptography.CspParameters> e especifique o nome do contêiner de chave que foi usado para assinatura.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2. Recupere a chave pública usando a classe <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  A chave é carregada automaticamente do contêiner de chave por nome quando você passa o objeto <xref:System.Security.Cryptography.CspParameters> para o construtor da classe <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3. Crie um objeto de <xref:System.Xml.XmlDocument> carregando um arquivo XML do disco.  O objeto <xref:System.Xml.XmlDocument> contém o documento XML assinado para verificar.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4. Crie um novo objeto <xref:System.Security.Cryptography.Xml.SignedXml> e passe o objeto <xref:System.Xml.XmlDocument> para ele.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5. Localize o elemento <`signature`> e crie um novo objeto <xref:System.Xml.XmlNodeList>.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6. Carregue o XML do primeiro <`signature`elemento > no objeto <xref:System.Security.Cryptography.Xml.SignedXml>.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7. Verifique a assinatura usando o método <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> e a chave pública RSA.  Esse método retorna um valor booliano que indica êxito ou falha.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo pressupõe que um arquivo chamado `"test.xml"` exista no mesmo diretório que o programa compilado.  O arquivo de `"test.xml"` deve ser assinado usando as técnicas descritas em [como assinar documentos XML com assinaturas digitais](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
  
- Para compilar este exemplo, você precisa incluir uma referência a `System.Security.dll`.  
  
- Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>e <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Nunca armazene ou transfira a chave privada de um par de chaves assimétricas em texto não criptografado.  Para obter mais informações sobre chaves de criptografia simétrica e assimétrica, consulte [gerando chaves para criptografia e descriptografia](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nunca incorpore uma chave privada diretamente em seu código-fonte.  Chaves inseridas podem ser facilmente lidas de um assembly usando o [ILDASM. exe (desmontador Il)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ou abrindo o assembly em um editor de texto como o bloco de notas.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Security.Cryptography.Xml>
- [Como assinar documento XML com assinaturas digitais](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)
