---
title: Como descriptografar elementos XML com chaves simétricas
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Rijndael
- decryption
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
ms.openlocfilehash: fd377cd470d361f5a46c662ab37780713a2d3804
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706117"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a>Como descriptografar elementos XML com chaves simétricas
Você pode usar as classes no namespace <xref:System.Security.Cryptography.Xml> para criptografar um elemento em um documento XML.  A criptografia XML permite que você armazene ou transporte XML confidencial, sem se preocupar com os dados que estão sendo facilmente lidos.  Este exemplo de código descriptografa um elemento XML usando o algoritmo criptografia AES (AES), também conhecido como Rijndael.  
  
 Para obter informações sobre como criptografar um elemento XML usando esse procedimento, consulte [como: Criptografar elementos XML com chaves simétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
 Ao usar um algoritmo simétrico como o AES para criptografar dados XML, você deve usar a mesma chave para criptografar e descriptografar os dados XML.  O exemplo neste procedimento pressupõe que o XML criptografado foi criptografado usando a mesma chave e que as partes de criptografia e descriptografia concordam com o algoritmo e a chave a serem usados.  Este exemplo não armazena ou criptografa a chave AES no XML criptografado.  
  
 Este exemplo é apropriado para situações em que um único aplicativo precisa criptografar dados com base em uma chave de sessão armazenada na memória ou com base em uma chave criptograficamente forte derivada de uma senha.  Para situações em que dois ou mais aplicativos precisam compartilhar dados XML criptografados, considere usar um esquema de criptografia baseado em um algoritmo assimétrico ou um certificado X. 509.  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a>Para descriptografar um elemento XML com uma chave simétrica  
  
1. Criptografe um elemento XML com a chave gerada anteriormente usando as técnicas descritas em [como: Criptografar elementos XML com chaves simétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md).  
  
2. Localize o elemento <`EncryptedData`> (definido pelo padrão de criptografia XML) em um objeto <xref:System.Xml.XmlDocument> que contém o XML criptografado e crie um novo objeto <xref:System.Xml.XmlElement> para representar esse elemento.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3. Crie um objeto de <xref:System.Security.Cryptography.Xml.EncryptedData> carregando os dados XML brutos do objeto <xref:System.Xml.XmlElement> criado anteriormente.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4. Crie um novo objeto <xref:System.Security.Cryptography.Xml.EncryptedXml> e use-o para descriptografar os dados XML usando a mesma chave que foi usada para criptografia.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5. Substitua o elemento Encrypted pelo elemento de texto sem formatação recentemente descriptografado dentro do documento XML.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo pressupõe que um arquivo chamado `"test.xml"` exista no mesmo diretório que o programa compilado.  Ele também pressupõe que `"test.xml"` contém um elemento `"creditcard"`.  Você pode inserir o XML a seguir em um arquivo chamado `test.xml` e usá-lo com este exemplo.  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
  
- Para compilar este exemplo, você precisa incluir uma referência a `System.Security.dll`.  
  
- Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>e <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Nunca armazene uma chave criptográfica em texto sem formatação ou transfira uma chave entre máquinas em texto não criptografado.  
  
 Quando você terminar de usar uma chave de criptografia simétrica, limpe-a da memória definindo cada byte como zero ou chamando o método de <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> da classe de criptografia gerenciada.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Security.Cryptography.Xml>
- [Como criptografar elementos XML com chaves simétricas](../../../docs/standard/security/how-to-encrypt-xml-elements-with-symmetric-keys.md)
