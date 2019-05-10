---
title: Visão geral de LINQ to XML no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: a8695e94797c297154db9597c6e9938ed9aecfef
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063027"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Visão geral de LINQ to XML no Visual Basic
O Visual Basic fornece suporte para [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] por meio de literais XML e propriedades de eixo XML. Isso permite que você use uma sintaxe familiar e conveniente para trabalhar com XML em seu código Visual Basic. *Literais XML* permitem incluir XML diretamente em seu código. *Propriedades do eixo XML* permitem que você acessar os nós filho, nós descendentes e atributos de um literal XML. Para obter mais informações, consulte [visão geral dos literais de XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) e [acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é projetado especificamente para tirar proveito de API de programação XML na memória [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Embora você possa chamar o [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] APIs diretamente, apenas o Visual Basic permite que você declare literais XML e acessar diretamente as propriedades do eixo XML.  
  
> [!NOTE]
>  Não há suporte para literais XML e propriedades de eixo XML no código declarativo em uma página ASP.NET. Para usar os recursos de XML do Visual Basic, coloque o código em uma página code-behind no seu aplicativo ASP.NET.  
  
 [Botão Reproduzir](./media/overview-of-linq-to-xml/play-video-icon-example.gif) para demonstrações em vídeo relacionadas, consulte [fazer como posso começar a usar com o LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) e [como faço para criar planilhas do Excel usando LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).   
  
## <a name="creating-xml"></a>Criar XML  
 Há duas maneiras para criar árvores XML no Visual Basic. Você pode declarar um literal XML diretamente no código, ou você pode usar o [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] APIs para criar a árvore. Os dois processos permitem ao código refletir a estrutura final da árvore XML. Por exemplo, o exemplo de código a seguir cria um elemento XML:  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Para obter mais informações, consulte [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).  
  
## <a name="accessing-and-navigating-xml"></a>Acessar e navegar por XML  
 Visual Basic fornece propriedades de eixo XML para acessar e navegar por estruturas XML. Essas propriedades permitem que você acesse elementos e atributos XML, especificando os nomes dos elementos filho XML. Como alternativa, você pode chamar explicitamente o [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] métodos para navegar e localizar elementos e atributos. Por exemplo, o exemplo de código a seguir usa propriedades de eixo XML para fazer referência a atributos e elementos filho de um elemento XML. O exemplo de código usa um [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] consulta para recuperar elementos filho e retorná-los como elementos XML, efetivamente, executando uma transformação.  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 Para obter mais informações, consulte [acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
## <a name="xml-namespaces"></a>Namespaces XML  
 Visual Basic permite que você especifique um alias para um namespace XML global usando o `Imports` instrução. O exemplo a seguir mostra como usar o `Imports` instrução para importar um namespace de XML:  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 Você pode usar um alias de namespace XML ao acessar propriedades do eixo XML e declarar literais XML para documentos e elementos XML.  
  
 Você pode recuperar um <xref:System.Xml.Linq.XNamespace> objeto para um determinado prefixo de namespace usando o [operador GetXmlNamespace](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).  
  
 Para obter mais informações, consulte [instrução Imports (Namespace de XML)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>Usando Namespaces XML em literais XML  
 O exemplo a seguir mostra como criar uma <xref:System.Xml.Linq.XElement> objeto que usa o namespace global `ns`:  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 O compilador do Visual Basic converte literais XML que contêm o alias de namespace XML em código equivalente que usa a notação de XML para namespaces XML, com o `xmlns` atributo. Quando compilado, o código no exemplo da seção anterior produz basicamente o mesmo código executável que o exemplo a seguir:  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>Usando Namespaces XML em Propriedades do eixo XML  
 Namespaces XML declaradas em literais XML não estão disponíveis para uso em Propriedades do eixo XML. No entanto, os namespaces globais podem ser usados com as propriedades de eixo XML. Use uma vírgula para separar o prefixo de namespace XML do nome do elemento local. Veja um exemplo a seguir:  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a>Consulte também

- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [Manipulando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
