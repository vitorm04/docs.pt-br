---
title: Como criptografar elementos XML com chaves assimétricas
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- AES algorithm
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys [.NET Framework]
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- key containers
- Advanced Encryption Standard algorithm
- Rijndael
- encryption [.NET Framework], asymmetric keys
ms.assetid: a164ba4f-e596-4bbe-a9ca-f214fe89ed48
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6840a9005aaca4805252298e1ceaf7e51f38971
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591454"
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a>Como criptografar elementos XML com chaves assimétricas
Você pode usar as classes de <xref:System.Security.Cryptography.Xml> namespace para criptografar um elemento em um documento XML.  Criptografia XML é uma maneira padrão para trocar ou armazenar dados criptografados do XML, sem se preocupar com os dados que estão sendo lidos facilmente.  Para obter mais informações sobre o padrão de criptografia XML, consulte a especificação de World Wide Web Consortium (W3C) para criptografia XML localizado em http://www.w3.org/TR/xmldsig-core/.  
  
 Você pode usar criptografia XML para substituir qualquer elemento XML ou um documento com um <`EncryptedData`> elemento que contém os dados criptografados do XML.  O <`EncryptedData`> elemento também pode conter elementos sub que incluem informações sobre as chaves e os processos usados durante a criptografia.  Criptografia XML permite que um documento conter vários elementos criptografados e permite que um elemento a ser criptografado várias vezes.  O exemplo de código neste procedimento mostra como criar um <`EncryptedData`> elemento juntamente com vários outros elementos sub que você pode usar durante a descriptografia.  
  
 Este exemplo criptografa um elemento XML usando duas chaves.  Ele gera um par de chaves pública/privada RSA e salva o par de chaves em um contêiner de chave seguro.  O exemplo cria uma chave de sessão separada usando o algoritmo de criptografia AES (Advanced Standard), também chamado do algoritmo Rijndael.  O exemplo usa a chave de sessão AES para criptografar o documento XML e, em seguida, usa a chave pública RSA para criptografar a chave de sessão AES.  Por fim, o exemplo salva a chave de sessão criptografada AES e os dados criptografados do XML para o documento XML dentro de um novo <`EncryptedData`> elemento.  
  
 Para descriptografar o elemento XML, recuperar a chave privada do RSA do contêiner de chave, usá-lo para descriptografar a chave de sessão e, em seguida, usar a chave de sessão para descriptografar o documento.  Para obter mais informações sobre como descriptografar um elemento XML que foi criptografado usando esse procedimento, consulte [como: descriptografar elementos XML com chaves assimétricas](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md).  
  
 Este exemplo é apropriado para situações em que vários aplicativos precisam compartilhar dados criptografados ou onde um aplicativo precisa salvar os dados criptografados entre os horários em que ele é executado.  
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a>Para criptografar um elemento XML com uma chave assimétrica  
  
1.  Criar um <xref:System.Security.Cryptography.CspParameters> do objeto e especifique o nome do contêiner de chave.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2.  Gerar uma chave simétrica usando o <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe.  A chave é salvo automaticamente para o contêiner de chave quando você passa o <xref:System.Security.Cryptography.CspParameters> objeto para o construtor do <xref:System.Security.Cryptography.RSACryptoServiceProvider> classe.  Essa chave será usada para criptografar a chave de sessão AES e pode ser recuperada posteriormente para descriptografá-lo.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3.  Criar um <xref:System.Xml.XmlDocument> objeto carregando um arquivo XML do disco.  O <xref:System.Xml.XmlDocument> objeto contém o elemento XML para criptografar.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4.  Localizar o elemento especificado no <xref:System.Xml.XmlDocument> de objeto e criar um novo <xref:System.Xml.XmlElement> objeto para representar o elemento que você deseja criptografar. Neste exemplo, o `"creditcard"` elemento está criptografado.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5.  Criar uma chave de nova sessão usando o <xref:System.Security.Cryptography.RijndaelManaged> classe.  Essa chave criptografa o elemento XML e, em seguida, ser criptografada em si e colocada no documento XML.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6.  Criar uma nova instância do <xref:System.Security.Cryptography.Xml.EncryptedXml> classe e usá-la para criptografar o elemento especificado usando a chave de sessão.  O <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> método retorna o elemento criptografado como uma matriz de bytes criptografados.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7.  Construir um <xref:System.Security.Cryptography.Xml.EncryptedData> de objeto e preenchê-lo com o identificador de URL do elemento XML criptografado.  Esse identificador de URL permite que um participante descriptografar o XML contém um elemento criptografado.  Você pode usar o <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> campo para especificar o identificador de URL.  O elemento XML de texto sem formatação será substituído por um <`EncryptedData`> elemento encapsulado por este <xref:System.Security.Cryptography.Xml.EncryptedData> objeto.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8.  Criar um <xref:System.Security.Cryptography.Xml.EncryptionMethod> objeto que é inicializado para o identificador de URL do algoritmo de criptografia usado para gerar a chave de sessão.  Passar o <xref:System.Security.Cryptography.Xml.EncryptionMethod> o objeto para o <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> propriedade.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. Criar um <xref:System.Security.Cryptography.Xml.EncryptedKey> objeto para conter a chave de sessão criptografada.  Criptografar a chave de sessão, adicione-o para o <xref:System.Security.Cryptography.Xml.EncryptedKey> objeto e, em seguida, digite um nome de chave de sessão e a URL de identificador de chave.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. Criar um novo <xref:System.Security.Cryptography.Xml.DataReference> objeto que mapeia os dados criptografados para uma chave de sessão específica.  Esta etapa opcional permite que você especifique facilmente que várias partes de um documento XML foram criptografadas por uma única chave.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. Adicionar a chave criptografada para o <xref:System.Security.Cryptography.Xml.EncryptedData> objeto.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. Criar um novo <xref:System.Security.Cryptography.Xml.KeyInfo> objeto para especificar o nome da chave RSA.  Adicioná-lo para o <xref:System.Security.Cryptography.Xml.EncryptedData> objeto. Isso ajuda a parte de descriptografia identificar a chave assimétrica correta a ser usado ao descriptografar a chave de sessão.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. Adicionar os dados criptografados do elemento para o <xref:System.Security.Cryptography.Xml.EncryptedData> objeto.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. Substitua o elemento do original <xref:System.Xml.XmlDocument> do objeto com o <xref:System.Security.Cryptography.Xml.EncryptedData> elemento.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. Salve o <xref:System.Xml.XmlDocument> objeto.  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo assume que um arquivo chamado `"test.xml"` existe no mesmo diretório que o programa compilado.  Ele também pressupõe que `"test.xml"` contém um `"creditcard"` elemento.  Você pode colocar o XML a seguir em um arquivo chamado `test.xml` e usá-lo com este exemplo.  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Para compilar este exemplo, você precisa incluir uma referência a `System.Security.dll`.  
  
-   Inclua os seguintes namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, e <xref:System.Security.Cryptography.Xml>.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Nunca armazenar uma chave de criptografia simétrica em texto não criptografado ou transferir uma chave simétrica entre máquinas em texto não criptografado.  Além disso, nunca armazenar ou transferir a chave privada de um par de chaves assimétricas em texto não criptografado.  Para obter mais informações sobre chaves de criptografia simétricas e assimétricas, consulte [gerando chaves de criptografia e descriptografia](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).  
  
 Nunca incorpore uma chave diretamente no seu código-fonte.  Chaves inseridas podem ser facilmente lidas de um assembly usando o [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ou abrindo o assembly em um editor de texto como o bloco de notas.  
  
 Quando você terminar usando uma chave de criptografia, limpá-la da memória, definindo cada byte para zero ou chamando o <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> método da classe gerenciada de criptografia.  As chaves de criptografia, às vezes, podem ser lido da memória por um depurador ou ler de um disco rígido se o local de memória é paginado para o disco.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Security.Cryptography.Xml>  
 [Como descriptografar elementos XML com chaves assimétricas](../../../docs/standard/security/how-to-decrypt-xml-elements-with-asymmetric-keys.md)
