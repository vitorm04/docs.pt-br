---
title: 'Como: verificar as assinaturas digitais de documentos XML'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19537fa3e3e27c3446d22f1f1a8cf2faf472158e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307763"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a>Como: verificar as assinaturas digitais de documentos XML
Você pode usar as classes de <xref:System.Security.Cryptography.Xml> namespace para verificar os dados XML assinado com uma assinatura digital. As assinaturas digitais XML (XMLDSIG) permitem que você verifique se que os dados não foi alterados depois que ele foi assinado. Para obter mais informações sobre o padrão XMLDSIG, consulte a especificação do World Wide Web Consortium (W3C) em <https://www.w3.org/TR/xmldsig-core/>.
  
 O exemplo de código neste procedimento demonstra como verificar uma assinatura digital de XML contida em um <`Signature`> elemento.  O exemplo recupera uma chave pública RSA de um contêiner de chave e, em seguida, usa a chave para verificar a assinatura.  
  
 Para obter informações sobre como criar uma assinatura digital que pode ser verificada usando essa técnica, consulte [como: Assinar documento XML com assinaturas digitais](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a>Para verificar a assinatura digital de um documento XML  
  
1. Para verificar se o documento, você deve usar a mesma chave assimétrica que foi usada para entrar.  Criar um <xref:System.Security.Cryptography.CspParameters> de objeto e especifique o nome do contêiner de chave que foi usado para entrar.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2. Recuperar a chave pública usando o <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe.  A chave é carregada automaticamente do contêiner de chave pelo nome quando você passa o <xref:System.Security.Cryptography.CspParameters> objeto para o construtor do <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3. Criar um <xref:System.Xml.XmlDocument> objeto carregando um arquivo XML do disco.  O <xref:System.Xml.XmlDocument> objeto contém o documento XML assinado para verificar.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4. Criar um novo <xref:System.Security.Cryptography.Xml.SignedXml> do objeto e passe o <xref:System.Xml.XmlDocument> objeto a ela.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5. Localizar o <`signature`> elemento e crie um novo <xref:System.Xml.XmlNodeList> objeto.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6. Carregar o XML da primeira <`signature`> elemento para o <xref:System.Security.Cryptography.Xml.SignedXml> objeto.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7. Verificar a assinatura usando o <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> método e a chave pública RSA.  Esse método retorna um valor booliano que indica êxito ou falha.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo supõe que um arquivo chamado `"test.xml"` existe no mesmo diretório que o programa compilado.  O `"test.xml"` arquivo deve ser assinado usando as técnicas descritas [como: Assinar documento XML com assinaturas digitais](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Para compilar este exemplo, você precisa incluir uma referência ao `System.Security.dll`.  
  
-   Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, e <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Nunca armazenar ou transferir a chave privada de um par de chaves assimétricas em texto não criptografado.  Para obter mais informações sobre chaves de criptografia simétricas e assimétricas, consulte [gerando chaves para criptografia e descriptografia](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nunca incorpore uma chave privada diretamente no seu código-fonte.  Chaves inseridas podem ser facilmente lido de um assembly usando o [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ou abrindo o assembly em um editor de texto como bloco de notas.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Security.Cryptography.Xml>
- [Como: Assinar documento XML com assinaturas digitais](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)
