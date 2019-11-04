---
title: Como criptografar elementos XML com chaves simétricas
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AES algorithm
- cryptography [.NET Framework], symmetric keys
- encryption [.NET Framework], symmetric keys
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Advanced Encryption Standard algorithm
- Rijndael
ms.assetid: d8461a44-aa2c-4ef4-b3e4-ab7cbaaee1b5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b792fd6eea0a33b0143fafa03641a78947d7e127
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458063"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a>Como criptografar elementos XML com chaves simétricas
Você pode usar as classes no namespace <xref:System.Security.Cryptography.Xml> para criptografar um elemento em um documento XML.  A criptografia XML permite que você armazene ou transporte XML confidencial, sem se preocupar com os dados que estão sendo facilmente lidos.  Este procedimento criptografa um elemento XML usando o algoritmo criptografia AES (AES), também conhecido como Rijndael.  
  
 Para obter informações sobre como descriptografar um elemento XML que foi criptografado usando esse procedimento, consulte [como: descriptografar elementos XML com chaves simétricas](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md).  
  
 Ao usar um algoritmo simétrico como o AES para criptografar dados XML, você deve usar a mesma chave para criptografar e descriptografar os dados XML.  O exemplo neste procedimento pressupõe que o XML criptografado será descriptografado usando a mesma chave e que as partes de criptografia e descriptografia concordam com o algoritmo e a chave a serem usados.  Este exemplo não armazena ou criptografa a chave AES no XML criptografado.  
  
 Este exemplo é apropriado para situações em que um único aplicativo precisa criptografar dados com base em uma chave de sessão armazenada na memória ou com base em uma chave criptograficamente forte derivada de uma senha.  Para situações em que dois ou mais aplicativos precisam compartilhar dados XML criptografados, considere usar um esquema de criptografia baseado em um algoritmo assimétrico ou um certificado X. 509.  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a>Para criptografar um elemento XML com uma chave simétrica  
  
1. Gere uma chave simétrica usando a classe <xref:System.Security.Cryptography.RijndaelManaged>.  Essa chave será usada para criptografar o elemento XML.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2. Crie um objeto de <xref:System.Xml.XmlDocument> carregando um arquivo XML do disco.  O objeto <xref:System.Xml.XmlDocument> contém o elemento XML a ser criptografado.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3. Localize o elemento especificado no objeto <xref:System.Xml.XmlDocument> e crie um novo objeto <xref:System.Xml.XmlElement> para representar o elemento que você deseja criptografar.  Neste exemplo, o elemento `"creditcard"` é criptografado.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4. Crie uma nova instância da classe <xref:System.Security.Cryptography.Xml.EncryptedXml> e use-a para criptografar o <xref:System.Xml.XmlElement> com a chave simétrica.  O método <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> retorna o elemento Encrypted como uma matriz de bytes criptografados.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5. Construa um objeto de <xref:System.Security.Cryptography.Xml.EncryptedData> e popule-o com o identificador de URL do elemento de criptografia XML.  Esse identificador de URL permite que uma parte descriptografada saiba que o XML contém um elemento criptografado.  Você pode usar o campo <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> para especificar o identificador da URL.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6. Crie um objeto <xref:System.Security.Cryptography.Xml.EncryptionMethod> que é inicializado para o identificador de URL do algoritmo criptográfico usado para gerar a chave.  Passe o objeto <xref:System.Security.Cryptography.Xml.EncryptionMethod> para a propriedade <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A>.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7. Adicione os dados do elemento criptografado ao objeto <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8. Substitua o elemento do objeto <xref:System.Xml.XmlDocument> original pelo elemento <xref:System.Security.Cryptography.Xml.EncryptedData>.  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a>Exemplo  
  
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
  
## <a name="compiling-the-code"></a>Compilando o código  
  
- Para compilar este exemplo, você precisa incluir uma referência a `System.Security.dll`.  
  
- Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>e <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Nunca armazene uma chave criptográfica em texto sem formatação ou transfira uma chave entre máquinas em texto não criptografado.  Em vez disso, use um contêiner de chave segura para armazenar chaves criptográficas.  
  
 Quando você terminar de usar uma chave criptográfica, limpe-a da memória definindo cada byte como zero ou chamando o método <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> da classe de criptografia gerenciada.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Security.Cryptography.Xml>
- [Como descriptografar elementos XML com chaves simétricas](../../../docs/standard/security/how-to-decrypt-xml-elements-with-symmetric-keys.md)
