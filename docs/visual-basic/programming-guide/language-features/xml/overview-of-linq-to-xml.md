---
title: Visão geral de LINQ to XML no Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be9038fb194c0e4890593b4b80751a477def20a7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Visão geral de LINQ to XML no Visual Basic
Visual Basic oferece suporte para [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] por meio de literais XML e propriedades de eixo XML. Isso permite que você use uma sintaxe familiar e conveniente para trabalhar com XML no código do Visual Basic. *Literais XML* permitem que você inclua XML diretamente no seu código. *Propriedades do eixo XML* permitem acessar os nós filho, nós descendentes e atributos de uma literal XML. Para obter mais informações, consulte [visão geral dos literais de XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) e [acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é projetado especificamente para aproveitar de API de programação XML na memória [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Embora você possa chamar o [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] APIs diretamente, apenas o Visual Basic permite que você declare literais XML e acessar diretamente as propriedades do eixo XML.  
  
> [!NOTE]
>  Não há suporte para literais XML e propriedades de eixo XML no código declarativo em uma página ASP.NET. Para usar os recursos de XML do Visual Basic, coloque o código em uma página code-behind em seu aplicativo ASP.NET.  
  
 ![link para vídeo](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") para demonstrações em vídeo relacionadas, consulte [como fazer começar com LINQ to XML?](http://go.microsoft.com/fwlink/?LinkId=143034) e [como faço para criar planilhas do Excel usando o LINQ to XML?](http://go.microsoft.com/fwlink/?LinkId=143536).  
  
## <a name="creating-xml"></a>Criando XML  
 Há duas maneiras para criar árvores XML no Visual Basic. Você pode declarar um literal XML diretamente no código, ou você pode usar o [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] APIs para criar a árvore. Os dois processos permitem que o código refletir a estrutura final da árvore XML. Por exemplo, o exemplo de código a seguir cria um elemento XML:  
  
 [!code-vb[VbXmlSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_1.vb)]  
  
 Para obter mais informações, consulte [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).  
  
## <a name="accessing-and-navigating-xml"></a>Acesso e navegação XML  
 Visual Basic fornece propriedades de eixo XML para acessar e navegar por estruturas XML. Essas propriedades permitem acessar elementos e atributos XML, especificando os nomes dos elementos filho XML. Como alternativa, você pode chamar explicitamente o [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] métodos para navegar e localizar elementos e atributos. Por exemplo, o exemplo de código a seguir usa propriedades do eixo XML para se referir aos atributos e elementos filho de um elemento XML. O exemplo de código usa um [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] consulta para recuperar elementos filho e retorná-los como elementos XML, efetivamente, executando uma transformação.  
  
 [!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_2.vb)]  
  
 Para obter mais informações, consulte [acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
## <a name="xml-namespaces"></a>Namespaces XML  
 Visual Basic permite que você especifique um alias para um namespace XML global usando o `Imports` instrução. O exemplo a seguir mostra como usar o `Imports` instrução para importar um namespace de XML:  
  
 [!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_3.vb)]  
  
 Você pode usar um alias de namespace XML quando você acessar propriedades do eixo XML e declara literais XML para documentos e elementos XML.  
  
 Você pode recuperar um <xref:System.Xml.Linq.XNamespace> objeto para um determinado prefixo de namespace usando o [operador GetXmlNamespace](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).  
  
 Para obter mais informações, consulte [instrução Imports (Namespace XML)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>Usando Namespaces XML em literais XML  
 O exemplo a seguir mostra como criar um <xref:System.Xml.Linq.XElement> objeto que usa o namespace global `ns`:  
  
 [!code-vb[VbXMLSamples#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_4.vb)]  
  
 O compilador do Visual Basic converte literais XML que contêm alias de namespace XML em código equivalente que usa a notação XML para namespaces XML, com o `xmlns` atributo. Quando compilado, o código de exemplo da seção anterior produz basicamente o mesmo código executável que o exemplo a seguir:  
  
 [!code-vb[VbXMLSamples#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_5.vb)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>Usando Namespaces XML em Propriedades do eixo XML  
 Namespaces para XML declarados em literais XML não estão disponíveis para uso em Propriedades do eixo XML. No entanto, namespaces globais pode ser usado com as propriedades de eixo XML. Use um vírgula para separar o prefixo de namespace XML do nome de elemento local. Veja um exemplo a seguir:  
  
 [!code-vb[VbXMLSamples#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_6.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [Manipulando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
