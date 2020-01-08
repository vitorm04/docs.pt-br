---
title: Como ler dados de objeto de um arquivo XML (C#)
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 2da5919c11ed2d6e43f4f9fc406f43e3ed48060f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346433"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a>Como ler dados de objeto de um arquivo XML (C#)
Este exemplo lê dados de objeto que foram previamente gravados em um arquivo XML usando a classe <xref:System.Xml.Serialization.XmlSerializer>.  
  
## <a name="example"></a>Exemplo  
  
```csharp  
public class Book  
{  
    public String title;  
}         
  
public void ReadXML()  
{  
    // First write something so that there is something to read ...  
    var b = new Book { title = "Serialization Overview" };  
    var writer = new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    var wfile = new System.IO.StreamWriter(@"c:\temp\SerializationOverview.xml");  
    writer.Serialize(wfile, b);  
    wfile.Close();  
  
    // Now we can read the serialized book ...  
    System.Xml.Serialization.XmlSerializer reader =   
        new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    System.IO.StreamReader file = new System.IO.StreamReader(  
        @"c:\temp\SerializationOverview.xml");  
    Book overview =  (Book)reader.Deserialize(file);  
    file.Close();  
  
    Console.WriteLine(overview.title);  
  
}  
```  
  
## <a name="compiling-the-code"></a>Compilando o Código  
Substitua o nome de arquivo "c:\temp\SerializationOverview.xml" pelo nome do arquivo que contém os dados serializados. Para obter mais informações sobre a serialização de dados, consulte [como gravar dados de objeto em umC#arquivo XML ()](./how-to-write-object-data-to-an-xml-file.md).
  
 A classe deve ter um construtor público sem parâmetros.  
  
 Somente propriedades e campos públicos são desserializados.  
  
## <a name="robust-programming"></a>Programação Robusta  
 As seguintes condições podem causar uma exceção:  
  
- A classe que está sendo serializada não tem um construtor público sem parâmetros.  
  
- Os dados no arquivo não representam dados da classe a ser desserializada.  
  
- O arquivo não existe (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Sempre verifique as entradas e nunca desserialize dados de uma fonte não confiável. O objeto recriado é executado em um computador local com as permissões do código que o desserializou. Verifique todas as entradas antes de usar os dados no seu aplicativo.  
  
## <a name="see-also"></a>Veja também

- <xref:System.IO.StreamWriter>
- [Como gravar dados de objeto em um arquivo XML (C#)](./how-to-write-object-data-to-an-xml-file.md)
- [Serialização (C#)](./index.md)
- [Guia de Programação em C#](../../index.md)
