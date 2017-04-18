---
title: "Visão geral de LINQ to XML no Visual Basic | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 508d4a97b0636f10607326eb35c4c5d8c7860873
ms.lasthandoff: 03/13/2017

---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Visão geral de LINQ to XML no Visual Basic
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]fornece suporte para [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] através de literais XML e propriedades de eixo XML. Isso permite que você use uma sintaxe familiar e conveniente para trabalhar com XML em seu [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] código. *Literais XML* permitem que você inclua XML diretamente no seu código. *Propriedades do eixo XML* permitem acessar os nós filho, nós descendentes e atributos de um literal XML. Para obter mais informações, consulte [visão geral de literais XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) e [acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]é projetada especificamente para aproveitar de API de programação XML na memória [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]. Embora você possa chamar o [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] APIs diretamente, apenas [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] permite que você declare literais XML e acessar propriedades do eixo XML diretamente.  
  
> [!NOTE]
>  Não há suporte para literais XML e propriedades de eixo XML no código declarativo em um página ASP.NET. Para usar recursos XML do Visual Basic, coloque o código em uma página code-behind no seu aplicativo ASP.NET.  
  
 ![link para vídeo](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") para demonstrações em vídeo relacionadas, consulte [fazer como começar com o LINQ to XML?](http://go.microsoft.com/fwlink/?LinkId=143034) e [como faço para criar planilhas do Excel usando o LINQ to XML?](http://go.microsoft.com/fwlink/?LinkId=143536).  
  
## <a name="creating-xml"></a>Criando XML  
 Há duas maneiras para criar árvores XML em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]. Você pode declarar um literal XML diretamente no código, ou você pode usar o [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] APIs para criar a árvore. Os dois processos permitem ao código refletir a estrutura final da árvore XML. Por exemplo, o exemplo de código a seguir cria um elemento XML:  
  
 [!code-vb[VbXmlSamples n º&5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_1.vb)]  
  
 Para obter mais informações, consulte [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).  
  
## <a name="accessing-and-navigating-xml"></a>Acesso e navegação XML  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]fornece propriedades de eixo XML para acessar e navegar por estruturas XML. Essas propriedades permitem que você acesse elementos e atributos XML, especificando os nomes dos elementos filho XML. Como alternativa, você pode chamar explicitamente o [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] métodos para navegar e localizar elementos e atributos. Por exemplo, o exemplo de código a seguir usa propriedades do eixo XML para se referir aos atributos e elementos filho de um elemento XML. O exemplo de código usa um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta para recuperar elementos filho e retorná-los como elementos XML, efetivamente executando uma transformação.  
  
 [!code-vb[VbXmlSamples n º&8;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_2.vb)]  
  
 Para obter mais informações, consulte [acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
## <a name="xml-namespaces"></a>Namespaces XML  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]permite que você especifique um alias para um namespace XML global usando o `Imports` instrução. O exemplo a seguir mostra como usar o `Imports` instrução de importação de um namespace XML:  
  
 [!code-vb[VbXMLSamples n º&1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_3.vb)]  
  
 Você pode usar um alias de namespace XML quando você acessar propriedades do eixo XML e declara literais XML para documentos e elementos XML.  
  
 Você pode recuperar um <xref:System.Xml.Linq.XNamespace>objeto para um determinado prefixo de namespace usando o [operador GetXmlNamespace](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).</xref:System.Xml.Linq.XNamespace>  
  
 Para obter mais informações, consulte [instrução Imports (Namespace XML)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>Usando Namespaces XML em literais XML  
 O exemplo a seguir mostra como criar um <xref:System.Xml.Linq.XElement>objeto que usa o namespace global `ns`:</xref:System.Xml.Linq.XElement>  
  
 [!code-vb[VbXMLSamples n º&2;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_4.vb)]  
  
 O [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte literais XML que contêm alias de namespace XML em código equivalente que usa a notação XML para namespaces XML, com o `xmlns` atributo. Quando compilado, o código no exemplo da seção anterior produz basicamente o mesmo código executável que o exemplo a seguir:  
  
 [!code-vb[VbXMLSamples n º&3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_5.vb)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>Usando Namespaces XML em Propriedades do eixo XML  
 Namespaces XML declarados em literais XML não estão disponíveis para uso em Propriedades do eixo XML. No entanto, namespaces globais podem ser usados com as propriedades do eixo XML. Use um vírgula para separar o prefixo de namespace XML do nome do elemento local. Veja um exemplo a seguir:  
  
 [!code-vb[VbXMLSamples n º&4;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_6.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)   
 [Manipulando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
