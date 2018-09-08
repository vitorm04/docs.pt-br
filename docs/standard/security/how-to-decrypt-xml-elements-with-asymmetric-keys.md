---
title: Como descriptografar elementos XML com chaves assimétricas
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96bee90c7cb3847f9c7059e1a0b1d737209b924f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185988"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a>Como descriptografar elementos XML com chaves assimétricas
Você pode usar as classes de <xref:System.Security.Cryptography.Xml> namespace para criptografar e descriptografar um elemento dentro de um documento XML.  Criptografia de XML é uma maneira padrão para trocar ou armazenar dados XML criptografados, sem se preocupar com os dados que está sendo lidos com facilidade.  Para obter mais informações sobre o padrão de criptografia de XML, consulte a recomendação do World Wide Web Consortium (W3C) [sintaxe de assinatura XML e o processamento](https://www.w3.org/TR/xmldsig-core/).  
  
 O exemplo neste procedimento descriptografa um elemento XML que foi criptografado usando os métodos descritos em [como: criptografar a elementos XML com chaves assimétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  Ele encontra um <`EncryptedData`> elemento, descriptografa o elemento e, em seguida, substitui o elemento por elemento XML de texto sem formatação original.  
  
 Este exemplo descriptografa um elemento XML usando duas chaves.  Ele recupera uma chave privada do RSA gerada anteriormente de um contêiner de chave e, em seguida, usa a chave RSA para descriptografar uma chave de sessão armazenados no <`EncryptedKey`> elemento da <`EncryptedData`> elemento.  O exemplo, em seguida, usa a chave de sessão para descriptografar o elemento XML.  
  
 Este exemplo é apropriado para situações em que vários aplicativos precisam compartilhar os dados criptografados ou onde um aplicativo tem que salvar os dados criptografados entre os horários em que ele é executado.  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a>Para descriptografar um elemento XML com uma chave assimétrica  
  
1.  Criar um <xref:System.Security.Cryptography.CspParameters> de objeto e especifique o nome do contêiner de chave.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  Recuperar uma chave assimétrica gerada anteriormente do contêiner usando o <xref:System.Security.Cryptography.RSACryptoServiceProvider> objeto.  A chave é recuperada automaticamente do contêiner de chave quando você passa o <xref:System.Security.Cryptography.CspParameters> do objeto para o <xref:System.Security.Cryptography.RSACryptoServiceProvider> construtor.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  Criar um novo <xref:System.Security.Cryptography.Xml.EncryptedXml> objeto para descriptografar o documento.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4.  Adicione um mapeamento de chave/nome para associar a chave RSA com o elemento no documento que deve ser descriptografado.  Você deve usar o mesmo nome para a chave que você usou quando você criptografou o documento.  Observe que esse nome é diferente do nome usado para identificar a chave no contêiner de chave especificada na etapa 1.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5.  Chame o <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> método para descriptografar o <`EncryptedData`> elemento.  Esse método usa a chave RSA para descriptografar a chave de sessão e usa automaticamente a chave de sessão para descriptografar o elemento XML.  Ele também automaticamente substitui o <`EncryptedData`> elemento com o texto sem formatação original.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6.  Salve o documento XML.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo supõe que um arquivo chamado `test.xml` existe no mesmo diretório que o programa compilado.  Ele também pressupõe que `test.xml` contém um elemento XML que foi criptografado usando as técnicas descritas [como: criptografar a elementos XML com chaves assimétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Para compilar este exemplo, você precisa incluir uma referência ao `System.Security.dll`.  
  
-   Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, e <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Nunca armazenar uma chave de criptografia simétrica em texto não criptografado ou transferir uma chave simétrica entre as máquinas em texto não criptografado.  Além disso, nunca armazenar ou transferir a chave privada de um par de chaves assimétricas em texto não criptografado.  Para obter mais informações sobre chaves de criptografia simétricas e assimétricas, consulte [gerando chaves para criptografia e descriptografia](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nunca incorpore uma chave diretamente no seu código-fonte.  Chaves inseridas podem ser facilmente lido de um assembly usando [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ou abrindo o assembly em um editor de texto como bloco de notas.  
  
 Quando você terminar usando uma chave de criptografia, desmarcá-la da memória, definindo cada byte como zero ou chamando o <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> método da classe de criptografia gerenciada.  Chaves de criptografia, às vezes, podem ser lido da memória por um depurador ou ler de um disco rígido se o local da memória é paginado para o disco.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Security.Cryptography.Xml>  
- [Como criptografar elementos XML com chaves assimétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)
