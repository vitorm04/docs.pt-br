---
title: "Vis&#227;o geral de LINQ to XML no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "LINQ [Visual Basic], LINQ to XML"
  - "LINQ to XML [Visual Basic], sobre o LINQ to XML"
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vis&#227;o geral de LINQ to XML no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece suporte para [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] através de literais XML e propriedades de eixo XML.  Isso permite que você use uma sintaxe conveniente e familiar para trabalhar com XML no seu [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] código.  *Literais XML* permitem que você incluir o XML diretamente em seu código.  *Propriedades de eixo XML* permitem acesso a nós filhos, nós descendentes e atributos de uma literal XML.  Para obter mais informações, consulte [Visão geral dos literais XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) e [Acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] é uma API de programação XML de memória projetada especificamente para aproveitar [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)].  Embora você possa chamar as APIs [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] diretamente, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] somente permite que você declare literais XML e acesse propriedades do eixo XML diretamente.  
  
> [!NOTE]
>  Não há suporte para literais XML e propriedades de eixo XML no código declarativo em um página ASP.NET.  Para usar recursos Visual Basic XML, coloque o código em uma página code\-behind no seu aplicativo ASP.NET.  
  
 ![link para vídeo](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.png "PlayVideo") Para demonstrações de vídeo relacionadas, consulte [como fazer começar com os LINQ to XML?](http://go.microsoft.com/fwlink/?LinkId=143034) e [Como faço para criar planilhas do Excel usando o LINQ to XML?](http://go.microsoft.com/fwlink/?LinkId=143536).  
  
## Criando XML  
 Há duas maneiras para criar árvores XML em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  Você pode declarar um literal XML diretamente no código, ou você pode usar as APIs [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] para criar a árvore.  Os dois processos permitem ao código refletir a estrutura final da árvore do XML.  Por exemplo, o exemplo de código a seguir cria um elemento XML:  
  
 [!CODE [VbXmlSamples#5](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#5)]  
  
 Para obter mais informações, consulte [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).  
  
## Acesso e Navegação XML  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece propriedades de eixo XML para acessar e navegar por estruturas XML.  Essas propriedades permitem que você acesse elementos e atributos XML, especificando os nomes dos elementos XML filhos.  Como alternativa, você pode chamar os métodos [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] explicitamente para navegar e localizar elementos e atributos.  Por exemplo, o seguinte exemplo de código usa propriedades do eixo XML para se referir aos atributos e elementos filhos de um elemento XML.  O exemplo de código usa uma consulta [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] para recuperar elementos filhos e de retorná\-los como elementos XML, de forma eficaz, executando uma transformação.  
  
 [!CODE [VbXmlSamples#8](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#8)]  
  
 Para obter mais informações, consulte [Acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
## Namespaces XML  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] permite que você especifique um alias para um namespace para XML global usando a instrução `Imports`.  O exemplo a seguir mostra como usar a instrução `Imports` para importar um namespace para XML:  
  
 [!CODE [VbXMLSamples#1](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#1)]  
  
 Você pode usar um alias de namespace para XML quando você acessar propriedades do eixo XML e declarar literais XML para documentos e elementos XML.  
  
 Você pode recuperar um objeto <xref:System.Xml.Linq.XNamespace> para um determinado prefixo de namespace usando o [Operador GetXmlNamespace](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).  
  
 Para obter mais informações, consulte [Instrução Imports \(namespace XML\)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
### Usando Namespaces XML em literais XML  
 O exemplo a seguir mostra como criar um objeto <xref:System.Xml.Linq.XElement> que usa o namespace global `ns`:  
  
 [!CODE [VbXMLSamples#2](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#2)]  
  
 O compilador [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] converte literais XML que contêm alias de namespace para XML em código equivalente que usa a notação XML para namespaces XML, com o atributo `xmlns`.  Quando compilado, o código no exemplo da seção anterior produz basicamente o mesmo código executável que o exemplo a seguir:  
  
 [!CODE [VbXMLSamples#3](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#3)]  
  
### Usando Namespaces XML em propriedades do eixo XML  
 Namespaces para XML declarados em literais XML não estão disponíveis para uso em eixo de propriedades XML.  No entanto, namespaces globais podem ser usados com as propriedades do eixo XML.  Use dois\-pontos para separar o prefixo do namespace para XML do nome de elemento local.  A seguir, há um exemplo:  
  
 [!CODE [VbXMLSamples#4](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#4)]  
  
## Consulte também  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)   
 [Manipulando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)