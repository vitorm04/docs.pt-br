---
title: Visão Geral de LINQ to XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 0481a140541a7f45c682c5150bc1c3d647de90bd
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266892"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Visão geral de LINQ to XML no Visual Basic
O Visual Basic [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fornece suporte para através de literais XML e propriedades do eixo XML. Isso permite que você use uma sintaxe familiar e conveniente para trabalhar com XML em seu código Visual Basic. *Os literais XML* permitem que você inclua XML diretamente em seu código. *As propriedades do eixo XML* permitem que você acesse os nódulos de criança, os nós descendentes e os atributos de um xml literal. Para obter mais informações, consulte [XML Literals Overview](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) e [Acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]é uma API de programação XML na memória projetada especificamente para tirar proveito da Consulta Integrada ao Idioma (LINQ). Embora você possa chamar diretamente as APIs LINQ, apenas o Visual Basic permite que você declare literais XML e acesse diretamente as propriedades do eixo XML.  
  
> [!NOTE]
> As propriedades do eixo XML e XML não são suportadas em código declarativo em uma página de ASP.NET. Para usar os recursos do Visual Basic XML, coloque seu código em uma página de código atrás em seu aplicativo ASP.NET.  
  
 [Botão de reprodução](./media/overview-of-linq-to-xml/play-video-icon-example.gif) Para demonstrações de vídeo relacionadas, [veja Como eu comecei com linq para XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) e como [crio planilhas de Excel usando LINQ para XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).
  
## <a name="creating-xml"></a>Criar XML  
 Existem duas maneiras de criar árvores XML no Visual Basic. Você pode declarar um XML literal diretamente no código, ou você pode usar as APIs LINQ para criar a árvore. Ambos os processos permitem que o código reflita a estrutura final da árvore XML. Por exemplo, o exemplo de código a seguir cria um elemento XML:  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Para obter mais informações, consulte [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).  
  
## <a name="accessing-and-navigating-xml"></a>Acessando e navegando XML  
 O Visual Basic fornece propriedades de eixo XML para acessar e navegar estruturas XML. Essas propriedades permitem que você acesse elementos e atributos XML especificando os nomes dos elementos de criança XML. Alternativamente, você pode explicitamente chamar os métodos LINQ para navegar e localizar elementos e atributos. Por exemplo, o exemplo de código a seguir usa propriedades do eixo XML para se referir aos atributos e elementos infantis de um elemento XML. O exemplo de código usa uma consulta LINQ para recuperar elementos da criança e despejá-los como elementos XML, efetivamente realizando uma transformação.  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 Para obter mais informações, consulte [Acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
## <a name="xml-namespaces"></a>Espaços de nomes XML  
 O Visual Basic permite especificar um alias para um `Imports` namespace XML global usando a declaração. O exemplo a seguir `Imports` mostra como usar a declaração para importar um namespace XML:  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 Você pode usar um alias de namespace XML quando acessar as propriedades do eixo XML e declarar literais XML para documentos e elementos XML.  
  
 Você pode <xref:System.Xml.Linq.XNamespace> recuperar um objeto para um prefixo de namespace específico usando o [GetXmlNamespace Operator](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).  
  
 Para obter mais informações, consulte [A Declaração de Importações (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>Usando namespaces XML em XML Literals  
 O exemplo a seguir <xref:System.Xml.Linq.XElement> mostra como criar um `ns`objeto que usa o namespace global :  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 O compilador Visual Basic traduz literais XML que contêm alias de namespace XML em código equivalente `xmlns` que usa a notação XML para usar namespaces XML, com o atributo. Quando compilado, o código no exemplo da seção anterior produz essencialmente o mesmo código executável do seguinte exemplo:  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>Usando namespaces XML em propriedades do eixo XML  
 Os namespaces XML declarados em literais XML não estão disponíveis para uso nas propriedades do eixo XML. No entanto, os namespaces globais podem ser usados com as propriedades do eixo XML. Use um cólon para separar o prefixo xml namespace do nome do elemento local. A seguir está um exemplo:  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a>Confira também

- [Xml](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [Manipulando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
