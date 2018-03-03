---
title: "Como descriptografar elementos XML com chaves assimétricas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- decryption
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 698a542765cf8599a2f07e747669893502b75045
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2018
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a>Como descriptografar elementos XML com chaves assimétricas
Você pode usar as classes de <xref:System.Security.Cryptography.Xml> namespace para criptografar e descriptografar um elemento em um documento XML.  Criptografia XML é uma maneira padrão para trocar ou armazenar dados criptografados do XML, sem se preocupar com os dados que estão sendo lidos facilmente.  Para obter mais informações sobre o padrão de criptografia XML, consulte a recomendação do World Wide Web Consortium (W3C) [sintaxe de assinatura XML e processamento](https://www.w3.org/TR/xmldsig-core/).  
  
 O exemplo neste procedimento descriptografa um elemento XML que foi criptografado usando os métodos descritos no [como: criptografar elementos XML com chaves assimétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  Encontrar um <`EncryptedData`> elemento, descriptografa o elemento e, em seguida, substitui o elemento com o elemento XML de texto sem formatação original.  
  
 Este exemplo descriptografa um elemento XML usando duas chaves.  Recupera uma chave privada do RSA gerada anteriormente de um contêiner de chave e, em seguida, usa a chave RSA para descriptografar uma chave de sessão armazenada no <`EncryptedKey`> elemento de <`EncryptedData`> elemento.  O exemplo usa a chave de sessão para descriptografar o elemento XML.  
  
 Este exemplo é apropriado para situações em que vários aplicativos precisam compartilhar dados criptografados ou onde um aplicativo tem que salvar os dados criptografados entre os horários em que ele é executado.  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a>Para descriptografar um elemento XML com uma chave assimétrica  
  
1.  Criar um <xref:System.Security.Cryptography.CspParameters> do objeto e especifique o nome do contêiner de chave.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  Recuperar uma chave assimétrica gerada antes do contêiner usando o <xref:System.Security.Cryptography.RSACryptoServiceProvider> objeto.  A chave é recuperada automaticamente do contêiner de chave quando você passa o <xref:System.Security.Cryptography.CspParameters> o objeto para o <xref:System.Security.Cryptography.RSACryptoServiceProvider> construtor.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  Criar um novo <xref:System.Security.Cryptography.Xml.EncryptedXml> objeto para descriptografar o documento.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4.  Adicione um mapeamento de chave/nome para associar a chave RSA com o elemento no documento que deve ser descriptografado.  Você deve usar o mesmo nome para a chave que você usou quando você criptografou o documento.  Observe que esse nome é separado do nome usado para identificar a chave no contêiner de chave especificado na etapa 1.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5.  Chamar o <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> método para descriptografar o <`EncryptedData`> elemento.  Esse método usa a chave RSA para descriptografar a chave de sessão e usa automaticamente a chave de sessão para descriptografar o elemento XML.  Ele também automaticamente substitui o <`EncryptedData`> elemento com o texto não criptografado original.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6.  Salve o documento XML.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo assume que um arquivo chamado `test.xml` existe no mesmo diretório que o programa compilado.  Ele também pressupõe que `test.xml` contém um elemento XML que foi criptografado usando as técnicas descritas em [como: criptografar elementos XML com chaves assimétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Para compilar este exemplo, você precisa incluir uma referência a `System.Security.dll`.  
  
-   Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, e <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Nunca armazenar uma chave de criptografia simétrica em texto não criptografado ou transferir uma chave simétrica entre máquinas em texto não criptografado.  Além disso, nunca armazenar ou transferir a chave privada de um par de chaves assimétricas em texto não criptografado.  Para obter mais informações sobre chaves de criptografia simétricas e assimétricas, consulte [gerando chaves de criptografia e descriptografia](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nunca incorpore uma chave diretamente no seu código-fonte.  Chaves inseridas podem ser facilmente lidos de um assembly usando [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ou abrindo o assembly em um editor de texto como o bloco de notas.  
  
 Quando você terminar usando uma chave de criptografia, limpá-la da memória, definindo cada byte para zero ou chamando o <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> método da classe gerenciada de criptografia.  As chaves de criptografia, às vezes, podem ser lido da memória por um depurador ou ler de um disco rígido se o local de memória é paginado para o disco.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Security.Cryptography.Xml>  
 [Como criptografar elementos XML com chaves assimétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)
