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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b2cb61f2cc7129153a71398c6fb219c4e3990a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a>Como verificar as assinaturas digitais de documentos XML
Você pode usar as classes de <xref:System.Security.Cryptography.Xml> namespace para verificar os dados XML assinado com uma assinatura digital.  Assinaturas digitais XML (XMLDSIG) permitem que você verificar que os dados não foi alterados depois de ser assinado.  Para obter mais informações sobre o padrão XMLDSIG, consulte a especificação de World Wide Web Consortium (W3C) em http://www.w3.org/TR/xmldsig-core/.  
  
 O exemplo de código neste procedimento demonstra como verificar uma assinatura digital XML contida em um <`Signature`> elemento.  O exemplo recupera uma chave pública RSA de um contêiner de chave e, em seguida, usa a chave para verificar a assinatura.  
  
 Para obter informações sobre como criar uma assinatura digital pode ser verificada usando essa técnica, consulte [como: documentos XML de entrada com assinaturas digitais](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a>Para verificar a assinatura digital de um documento XML  
  
1.  Para verificar se o documento, você deve usar a mesma chave assimétrica que foi usada para assinatura.  Criar um <xref:System.Security.Cryptography.CspParameters> do objeto e especifique o nome do recipiente de chave que foi usado para assinar.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2.  Recuperar a chave pública usando o <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe.  A chave é carregada automaticamente do contêiner de chave por nome quando você passar o <xref:System.Security.Cryptography.CspParameters> objeto para o construtor do <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3.  Criar um <xref:System.Xml.XmlDocument> objeto carregando um arquivo XML do disco.  O <xref:System.Xml.XmlDocument> objeto contém o documento XML assinado para verificar.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4.  Criar um novo <xref:System.Security.Cryptography.Xml.SignedXml> de objeto e passar o <xref:System.Xml.XmlDocument> objeto a ela.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5.  Localize o <`signature`> elemento e criar um novo <xref:System.Xml.XmlNodeList> objeto.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6.  Carregar o XML do primeiro <`signature`> elemento para o <xref:System.Security.Cryptography.Xml.SignedXml> objeto.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7.  Verificar a assinatura usando o <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> método e a chave pública RSA.  Esse método retorna um valor booliano que indica êxito ou falha.  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo assume que um arquivo chamado `"test.xml"` existe no mesmo diretório que o programa compilado.  O `"test.xml"` arquivo deve ser assinado usando as técnicas descritas em [como: documentos XML de entrada com assinaturas digitais](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Para compilar este exemplo, você precisa incluir uma referência a `System.Security.dll`.  
  
-   Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, e <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Nunca armazenar ou transferir a chave privada de um par de chaves assimétricas em texto não criptografado.  Para obter mais informações sobre chaves de criptografia simétricas e assimétricas, consulte [gerando chaves de criptografia e descriptografia](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nunca incorpore uma chave privada diretamente no seu código-fonte.  Chaves inseridas podem ser facilmente lidas de um assembly usando o [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ou abrindo o assembly em um editor de texto como o bloco de notas.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Security.Cryptography.Xml>  
 [Como assinar documento XML com assinaturas digitais](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)
