---
title: LINQ para visão geral do XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: 962fddcfec04259425c1094f07adf0e3966dfab0
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48245225"
---
# <a name="linq-to-xml-overview-visual-basic"></a>LINQ para visão geral do XML (Visual Basic)
O XML tem sido amplamente adotado como um modo de formatar dados em muitos contextos. Por exemplo, você pode encontrar XML na Web, em arquivos de configuração, em arquivos do Microsoft Office Word e em bancos de dados.  
  
 O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é uma abordagem atualizada e redesenhada para a programação com XML. Ele oferece os recursos de modificação de documentos na memória do DOM (Document Object Model), bem como o suporte a expressões de consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Embora essas expressões de consulta sejam sintaticamente diferentes de XPath, elas oferecem uma funcionalidade semelhante.  
  
## <a name="linq-to-xml-developers"></a>Desenvolvedores em LINQ to XML  
 O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se destina a uma variedade de desenvolvedores. Para um desenvolvedor médio que deseja apenas ter algo concluído, o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] torna o XML mais simples ao oferecer uma experiência de consulta que é semelhante ao SQL. Com apenas um pouco de estudo, os programadores podem aprender a escrever consultas sucintas e eficientes na linguagem de programação de sua escolha.  
  
 Os desenvolvedores profissionais podem usar o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] para aumentar consideravelmente sua produtividade. Com o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], eles podem escrever um código menor que seja mais expressivo, mais compacto e mais eficiente. Eles podem usar expressões de consulta de vários domínios de dados ao mesmo tempo.  
  
## <a name="what-is-linq-to-xml"></a>O que é o LINQ to XML?  
 O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é uma interface de programação XML na memória e habilitada para LINQ que permite que você trabalhe com XML de dentro das linguagens de programação [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
 O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é como o DOM (Modelo de Objeto do Documento) no sentido de levar o documento XML para a memória. Você pode consultar e modificar o documento e, depois de modificá-lo, pode salvá-lo em um arquivo ou serializá-lo e enviá-lo pela Internet. No entanto, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] difere do DOM: ele fornece um novo modelo de objeto que é mais leve e fácil de trabalhar, e que tira proveito dos recursos de linguagem do Visual Basic.  
  
 A vantagem mais importante do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é sua integração com o [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Essa integração permite que você escreva consultas no documento XML na memória para recuperar coleções de elementos e atributos. O recurso de consulta do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é comparável em funcionalidade (embora não em sintaxe) a XPath e XQuery. A integração do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] no Visual Basic oferece tipagem mais forte, compilação-tempo verificando e melhor suporte de depuração.  
  
 Outra vantagem do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é a capacidade de usar resultados da consulta como parâmetros para construtores de objeto <xref:System.Xml.Linq.XElement> e <xref:System.Xml.Linq.XAttribute>, o que permite uma abordagem eficiente para a criação de árvores XML. Essa abordagem, chamada de *construção funcional*, permite que os desenvolvedores transformem com facilidade árvores XML de uma forma em outra.  
  
 Por exemplo, você pode ter uma ordem de compra em XML típica, conforme descrito em [Arquivo XML de exemplo: ordem de compra típica (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md). Usando o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], você poderia executar a consulta a seguir para obter o valor do atributo de número de peça para cada elemento de item na ordem de compra:  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 Como outro exemplo, você poderia querer uma lista, classificada por número de peça, dos itens com um valor maior que $ 100. Para obter essas informações, você poderia executar a seguinte consulta:  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 Além desses recursos de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] oferece uma interface de programação XML aprimorada. Usando o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], você pode:  
  
-   Carregar XML de arquivos ou fluxos.  
  
-   Serializar o XML em arquivos ou fluxos.  
  
-   Crie XML a partir do zero usando a construção funcional.  
  
-   Consultar o XML usando eixos do tipo XPath.  
  
-   Manipular a árvore XML na memória usando métodos como <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A> e <xref:System.Xml.Linq.XElement.SetValue%2A>.  
  
-   Validar árvores XML usando XSD.  
  
-   Usar uma combinação desses recursos para transformar árvores XML de uma forma em outra.  
  
## <a name="creating-xml-trees"></a>Criando árvores XML  
 Uma das vantagens mais significativas da programação com [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é que é fácil criar árvores XML. Por exemplo, para criar uma árvore XML pequena, você pode escrever código da seguinte maneira:  
  
```vb  
Dim contacts = _  
<Contacts>  
    <Contact>  
        <Name>Patrick Hines</Name>  
        <Phone Type="Home">206-555-0144</Phone>  
        <Phone Type="Work">425-555-0145</Phone>  
        <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
        </Address>  
    </Contact>  
</Contacts>  
```  
  
 O compilador do Visual Basic converte literais XML em [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] chamadas de método.  
  
 Para obter mais informações, consulte [criando árvores XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq>  
- [Introdução (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)  
- [Visão geral do LINQ to XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
