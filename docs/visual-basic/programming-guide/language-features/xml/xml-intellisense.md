---
title: XML IntelliSense no Visual Basic | Documentos do Microsoft
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
- Visual Basic code, XML
- XML IntelliSense [Visual Basic]
- XML [Visual Basic], IntelliSense
- IntelliSense [Visual Basic], XML
ms.assetid: 59506ce9-d64e-417e-90fc-e9fe19f0a8fa
caps.latest.revision: 27
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8c43db3d2010e4fa92eebeec8a973c50052b1340
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="xml-intellisense-in-visual-basic"></a>XML IntelliSense no Visual Basic
Editor de código do Visual Basic inclui recursos do IntelliSense para XML que fornecem conclusão de palavras para os elementos definidos em um esquema XML. Se você incluir um arquivo de definição de esquema XML (XSD) no seu projeto e importar o namespace de destino do esquema usando o `Imports` instrução, o Editor de códigos irá incluir elementos do esquema XSD na lista do IntelliSense das variáveis de membro válido para <xref:System.Xml.Linq.XElement>e <xref:System.Xml.Linq.XDocument>objetos.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> A ilustração a seguir mostra a lista de membros do IntelliSense para um <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement>  
  
 ![XML IntelliSense no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/media/xml_intellisense.png "XML_Intellisense")  
XML IntelliSense  
  
## <a name="enabling-xml-intellisense-in-visual-basic"></a>Habilitar o IntelliSense XML no Visual Basic  
 Para habilitar o XML IntelliSense no Visual Basic, você deve incluir um arquivo de esquema XSD em seu projeto do Visual Basic. Você também deve importar o namespace de destino para o esquema XSD para seu arquivo de código usando o `Imports` instrução. Como alternativa, você pode adicionar o namespace de destino à lista de namespace de nível de projeto usando o **referências** página do Designer de projeto do Visual Basic. Para obter exemplos, consulte [como: habilitar o XML IntelliSense no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md). Para obter mais informações, consulte [instrução Imports (Namespace XML)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) e [referências de página, Designer de projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).  
  
 Observe que por padrão você não pode ver os arquivos de esquema XSD em projetos do Visual Basic. Você talvez tenha que clicar o **Show All Files** para selecionar um arquivo XSD para incluir em seu projeto.  
  
### <a name="generating-a-schema-file-schema-inference"></a>Gerar um arquivo de esquema (inferência de esquema)  
 Você pode criar um esquema XSD para um arquivo XML existente inferindo o esquema XSD usando as ferramentas de XML do Visual Studio.  
  
-   A partir do SP1, você pode usar o Assistente de XML para esquema para criar um conjunto de esquema XML é inferido de um ou mais documentos XML e incluí-lo em seu projeto. Você pode usar qualquer combinação de documentos XML na forma de arquivos de texto, XML de endereços de HTTP Internet ou XML que é digitado ou colado em XML para Assistente de esquema. Para acessar o Assistente de XML para esquema, clique em **Adicionar Novo Item** no **projeto** menu e adicione um **XML para esquema** modelo do **dados** ou **itens comuns** grupo de modelos. Depois de incluir todas as fontes de documento XML para inferir o conjunto de esquema XML do, clique em **Okey** criar o esquema inferido definido. Para obter mais informações, consulte [XML para Assistente de esquema](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md).  
  
-   Você também pode usar o Editor de XML do Visual Studio para inferir um esquema XSD definido de um arquivo XML. Para criar um esquema XML definido usando o Editor XML, abra um arquivo XML no Designer do Visual Studio XML e, em seguida, clique em **Create Schema** sobre o **XML** menu. Depois de criar o conjunto de esquema XSD, você pode salvar o conjunto de esquema criado para um ou mais arquivos XSD e incluí-los em seu projeto. Para obter mais informações, consulte[como: habilitar o XML IntelliSense no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md).  
  
 Observe que diferentes conjuntos de esquema XSD podem ser inferidos de vários documentos XML que devem ter o mesmo esquema. Isso pode ocorrer quando determinados elementos e atributos são encontrados em um arquivo XML e não no outro, ou quando estiver incluído em uma ordem diferente, por exemplo. Você deve examinar conjuntos de esquema XSD inferidos para a integridade e a precisão quando você usa a inferência de esquema XSD.  
  
## <a name="member-list"></a>Lista de membros  
 Depois de digitar um ponto (.) para delimitar uma instância de um <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>objeto (ou uma instância de `IEnumerable(Of XElement)` ou `IEnumerable(Of XDocument)`), Visual Basic IntelliSense exibe uma lista de possíveis membros do objeto.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> A lista inicial inclui três opções que representam propriedades do eixo XML, conforme descrito na lista a seguir.  
  
|Opção|Descrição|  
|---|---|  
|**\< >**|Selecione esta opção para mostrar uma lista de possíveis filho elementos. Para obter mais informações, consulte [o Literal de elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) e o <xref:System.Xml.Linq.XContainer.Elements%2A>método.</xref:System.Xml.Linq.XContainer.Elements%2A>|  
|**@**|Selecione esta opção para mostrar uma lista de possíveis atributos. Para obter mais informações, consulte [propriedades do eixo XML](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md). Essa opção está disponível somente para objetos do tipo <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement>|  
|**…\< >**|Selecione esta opção para mostrar uma lista de possíveis elementos descendentes. Para obter mais informações, consulte [como: acessar XML descendente elementos](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md) e o <xref:System.Xml.Linq.XContainer.Elements%2A>método.</xref:System.Xml.Linq.XContainer.Elements%2A>|  
  
 Selecione ou começar a digitar qualquer uma das opções da lista XML. A lista de membros, em seguida, exibirá possíveis membros do esquema XML que são específicos para a opção selecionada. Se você tiver namespace XML importados que está associado com um prefixo de namespace XML específico, uma lista de possíveis prefixos de namespace XML está incluída na lista de membros.  
  
 Por exemplo, considere o seguinte esquema XSD.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema attributeFormDefault="unqualified"   
           elementFormDefault="qualified"   
           targetNamespace="http://SamplePurchaseOrder"   
           xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="PurchaseOrders">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="PurchaseOrder">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="Address" />  
              <xs:element name="Items" />  
              <xs:element name="Comment" />  
            </xs:sequence>  
            <xs:attribute name="PurchaseOrderNumber" type="xs:unsignedShort" use="required" />  
            <xs:attribute name="OrderDate" type="xs:string" use="required" />  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 XML válido para o esquema XSD seria semelhante ao seguinte.  
  
```xml  
<?xml version="1.0"?>  
<PurchaseOrders xmlns="http://SamplePurchaseOrder">  
  <PurchaseOrder PurchaseOrderNumber="12345" OrderDate="2000-1-1">  
    <Address />  
    <Items />  
    <Comment />  
  </PurchaseOrder>  
</PurchaseOrders>  
```  
  
 Se você incluir esse arquivo de esquema XSD em um projeto e importa o namespace de destino do esquema XSD para seu arquivo de código ou projeto, o Visual Basic IntelliSense exibe membros do esquema conforme você digita seu código Visual Basic. Se o namespace de destino para o esquema XSD é importado como o namespace padrão e digite o seguinte, o IntelliSense exibe uma lista dos elementos filho possíveis para o `PurchaseOrder` elemento XML.  
  
```  
Dim po = <PurchaseOrder />  
po.<  
```  
  
 A lista consiste nos elementos de endereço, comentário e itens.  
  
### <a name="certainty-levels-for-intellisense-list-items"></a>Níveis de certeza para itens de lista do IntelliSense  
 Determinar o tipo XSD para usar no IntelliSense não é exato. Como resultado, o XML IntelliSense geralmente mostrará uma lista expandida de membros possíveis. Para ajudar você a selecionar um item da lista de membros do IntelliSense, os itens são exibidos com uma indicação do nível de certeza que o XML IntelliSense tem para um determinado membro.  
  
 Às vezes, XML IntelliSense pode identificar um tipo específico do esquema XSD. Nesses casos, ele exibirá possíveis elementos filho, atributos ou elementos descendentes para aquele tipo XSD com um alto grau de certeza. Esses itens são identificados com uma marca de seleção.  
  
 No entanto, às vezes, XML IntelliSense não é capaz de identificar um tipo específico do esquema XSD. Nesses casos, ele exibirá uma lista expandida de possíveis elementos filho, atributos ou elementos descendentes do esquema XSD para o projeto com um baixo grau de certeza. Esses itens são identificados com um ponto de interrogação.  
  
## <a name="see-also"></a>Consulte também  
 [Como: habilitar o XML IntelliSense no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/how-to-enable-xml-intellisense.md)   
 [Assistente de esquema XML](../../../../visual-basic/programming-guide/language-features/xml/xml-to-schema-wizard.md)   
 [Instrução Imports (Namespace XML)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [Literal do elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [Propriedade de eixo de atributo XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)   
 [Propriedade de eixo descendente XML](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)   
 [Página Referências, Designer de Projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)
