---
title: "Como: gravar dados de objeto para um arquivo XML (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como: gravar dados de objeto para um arquivo XML (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Teste de exemplo grava o objeto de uma classe para um arquivo XML usando o <xref:System.Xml.Serialization.XmlSerializer> classe.  
  
## Exemplo  
  
```c#  
public class XMLWrite  
{  
  
   static void Main(string[] args)  
    {  
        WriteXML();  
    }  
  
    public class Book  
    {  
        public String title;   
    }  
  
    public static void WriteXML()  
    {  
        Book overview = new Book();  
        overview.title = "Serialization Overview";  
        System.Xml.Serialization.XmlSerializer writer =   
            new System.Xml.Serialization.XmlSerializer(typeof(Book));  
  
        var path = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments) + "//SerializationOverview.xml";  
        System.IO.FileStream file = System.IO.File.Create(path);  
  
        writer.Serialize(file, overview);  
        file.Close();  
    }  
}  
```  
  
## Compilando o código  
 A classe deve ter um construtor público sem parâmetros.  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   A classe sendo serializada não tem um construtor público, sem parâmetro.  
  
-   O arquivo existe e é somente leitura \(<xref:System.IO.IOException>\).  
  
-   O caminho é muito longo \(<xref:System.IO.PathTooLongException>\).  
  
-   O disco está cheio \(<xref:System.IO.IOException>\).  
  
## Segurança do .NET Framework  
 Este exemplo cria um novo arquivo, se o arquivo ainda não existir. Se um aplicativo precisar criar um arquivo, o aplicativo precisa `Create` acesso para a pasta. Se o arquivo já existir, o aplicativo precisa apenas `Write` acessar, um privilégio menor. Sempre que possível, é mais seguro criar o arquivo durante a implantação e somente conceder `Read` acesso a um único arquivo, em vez de `Create` acesso para uma pasta.  
  
## Consulte também  
 <xref:System.IO.StreamWriter>   
 [Como: ler dados de objeto de um arquivo XML \(c\#\)](../Topic/How%20to:%20Read%20Object%20Data%20from%20an%20XML%20File%20\(C%23\).md)   
 [Serialização \(c\#\)](../../../../csharp/programming-guide/concepts/serialization/index.md)