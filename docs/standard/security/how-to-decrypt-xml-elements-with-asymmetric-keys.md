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
ms.openlocfilehash: 5ed1e2eb2518366da0a57655d7a8691e23f725d5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706130"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a>Como descriptografar elementos XML com chaves assimétricas
Você pode usar as classes no namespace <xref:System.Security.Cryptography.Xml> para criptografar e descriptografar um elemento em um documento XML.  A criptografia XML é uma maneira padrão de trocar ou armazenar dados XML criptografados, sem se preocupar com os dados que estão sendo facilmente lidos.  Para obter mais informações sobre o padrão de criptografia XML, consulte a [sintaxe e o processamento da assinatura XML](https://www.w3.org/TR/xmldsig-core/)de recomendação do World Wide Web CONSORTIUM (W3C).  
  
 O exemplo neste procedimento descriptografa um elemento XML que foi criptografado usando os métodos descritos em [como: Criptografar elementos XML com chaves assimétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  Ele encontra um elemento <`EncryptedData`>, descriptografa o elemento e, em seguida, substitui o elemento pelo elemento XML original de texto não criptografado.  
  
 Este exemplo descriptografa um elemento XML usando duas chaves.  Ele recupera uma chave privada RSA gerada anteriormente de um contêiner de chave e, em seguida, usa a chave RSA para descriptografar uma chave de sessão armazenada no elemento <`EncryptedKey`> do elemento <`EncryptedData`>.  Em seguida, o exemplo usa a chave de sessão para descriptografar o elemento XML.  
  
 Este exemplo é apropriado para situações em que vários aplicativos precisam compartilhar dados criptografados ou onde um aplicativo precisa salvar dados criptografados entre os horários em que são executados.  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a>Para descriptografar um elemento XML com uma chave assimétrica  
  
1. Crie um objeto <xref:System.Security.Cryptography.CspParameters> e especifique o nome do contêiner de chave.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. Recupere uma chave assimétrica gerada anteriormente do contêiner usando o objeto <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  A chave é recuperada automaticamente do contêiner de chave quando você passa o objeto <xref:System.Security.Cryptography.CspParameters> para o Construtor <xref:System.Security.Cryptography.RSACryptoServiceProvider>.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. Crie um novo objeto <xref:System.Security.Cryptography.Xml.EncryptedXml> para descriptografar o documento.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4. Adicione um mapeamento de chave/nome para associar a chave RSA ao elemento dentro do documento que deve ser descriptografado.  Você deve usar o mesmo nome para a chave que usou ao criptografar o documento.  Observe que esse nome é separado do nome usado para identificar a chave no contêiner de chave especificado na etapa 1.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5. Chame o método <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> para descriptografar a <`EncryptedData`elemento >.  Esse método usa a chave RSA para descriptografar a chave de sessão e usa automaticamente a chave de sessão para descriptografar o elemento XML.  Ele também substitui automaticamente o elemento <`EncryptedData`> pelo texto não criptografado original.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6. Salve o documento XML.  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo pressupõe que um arquivo chamado `test.xml` exista no mesmo diretório que o programa compilado.  Ele também pressupõe que `test.xml` contém um elemento XML que foi criptografado usando as técnicas descritas em [como: Criptografar elementos XML com chaves assimétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md).  
  
 [!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
  
- Para compilar este exemplo, você precisa incluir uma referência a `System.Security.dll`.  
  
- Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>e <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Nunca armazene uma chave de criptografia simétrica em texto não criptografado ou transfira uma chave simétrica entre máquinas em texto não criptografado.  Além disso, nunca armazene ou transfira a chave privada de um par de chaves assimétricas em texto não criptografado.  Para obter mais informações sobre chaves de criptografia simétrica e assimétrica, consulte [gerando chaves para criptografia e descriptografia](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nunca incorpore uma chave diretamente no seu código-fonte.  Chaves inseridas podem ser facilmente lidas de um assembly usando [ILDASM. exe (desmontador Il)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ou abrindo o assembly em um editor de texto como o bloco de notas.  
  
 Quando você terminar de usar uma chave criptográfica, limpe-a da memória definindo cada byte como zero ou chamando o método <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> da classe de criptografia gerenciada.  Às vezes, as chaves criptográficas podem ser lidas da memória por um depurador ou lidas de um disco rígido se o local da memória for paginado no disco.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Security.Cryptography.Xml>
- [Como criptografar elementos XML com chaves assimétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-asymmetric-keys.md)
