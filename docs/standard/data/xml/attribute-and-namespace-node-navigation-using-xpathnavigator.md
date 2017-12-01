---
title: "Navegação do nó de atributo e do namespace usando XPathNavigator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23975f88-e0af-4b88-93de-9e20e11880ad
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 45e94954641e935597394b7cf04818c6c78ea675
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="attribute-and-namespace-node-navigation-using-xpathnavigator"></a>Navegação do nó de atributo e do namespace usando XPathNavigator
O <xref:System.Xml.XPath.XPathNavigator> classe fornece dois conjuntos de métodos de navegação, o primeiro conjunto, encontrado na [nó definido navegação usando XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) tópico, são usados para navegar *conjuntos de nó* em um <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> objeto. O segundo conjunto, descrito neste tópico, são usados para navegar *nós de atributo e de namespace* em uma <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> objeto.  
  
## <a name="attribute-node-navigation"></a>Navegação do nó de atributo  
 Os atributos são propriedades de um elemento, não filhos de um elemento. Essa distinção é importante, devido aos métodos da classe <xref:System.Xml.XPath.XPathNavigator> usada para navegar em irmão, o pai, e os nós filho.  
  
 Por exemplo, <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> e métodos de <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> não são usados para navegar de um elemento a um atributo ou entre atributos. Em vez disso, os atributos possuem métodos distintos de navegação.  
  
 Estes são os métodos de navegação de atributo de classe de <xref:System.Xml.XPath.XPathNavigator> .  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>  
  
 Quando o nó atual é um elemento, você pode usar a propriedade de <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A> para ver se houver algum atributo associado com o elemento. Depois que se souber que um elemento tem atributos, há vários métodos para acessar atributos. Para recuperar um único atributo do elemento, use o método de <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A> . Para mover <xref:System.Xml.XPath.XPathNavigator> a um atributo específico, use o método de <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A> . Você também pode iterar sobre cada atributo de um elemento usando o método <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A> , seguido por várias chamadas para o método de <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A> .  
  
> [!NOTE]
>  Quando o objeto de <xref:System.Xml.XPath.XPathNavigator> é posicionado em um nó de atributo ou de namespace, em <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, em <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, em <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, em <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, em <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, em <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> e métodos em <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>sempre de retorno de `false` , e não tem efeito na posição de <xref:System.Xml.XPath.XPathNavigator>. As exceções são <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>, e métodos de <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> .  
  
## <a name="namespace-node-navigation"></a>Navegação do nó de namespace  
 Cada elemento tem um conjunto associado de nós de namespace, um para cada prefixo diferente do namespace que é associado ao URI de namespace no escopo para o elemento (incluindo o prefixo XML limite para o espaço de `http://www.w3.org/XML/1998/namespace` , que é declarada implicitamente em cada documento XML) e um para o namespace padrão se uma estiver no escopo para o elemento. O elemento é o pai de cada um desses nós de namespace; no entanto, um nó de namespace não é um filho de seu elemento pai.  
  
 Como com atributos, <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> e métodos de <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> não são usados para navegar de um elemento a um nó de namespace, ou entre nós de namespace. Em vez disso, os nós de namespace possuem métodos distintos de navegação.  
  
 Estes são os métodos de navegação do namespace da classe de <xref:System.Xml.XPath.XPathNavigator> .  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>  
  
 Há sempre pelo menos um nó de namespace no escopo para qualquer elemento em um documento XML. Este é o nó do namespace com o prefixo `xml` e URI `http://www.w3.org/XML/1998/namespace`de namespace. Para recuperar o URI de namespace no escopo dado um determinado prefixo, use o método de <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A> . Para mover o objeto de <xref:System.Xml.XPath.XPathNavigator> a um nó específico de namespace, use o método de <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A> . Você também pode iterar sobre cada nó do namespace no escopo de um elemento usando o método <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> seguido por várias chamadas para o método de <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> .  
  
> [!NOTE]
>  Quando o objeto de <xref:System.Xml.XPath.XPathNavigator> é posicionado em um nó de atributo ou de namespace, em <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, em <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, em <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, em <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, em <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, em <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> e métodos em <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>sempre de retorno de `false` , e não tem efeito na posição de <xref:System.Xml.XPath.XPathNavigator>. As exceções são <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>, e métodos de <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> .  
  
### <a name="the-xpathnamespacescope-enumeration"></a>A enumeração de XPathNamespaceScope  
 Para navegar em nós de namespace os métodos de <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> e de <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> podem ser chamados com um parâmetro de <xref:System.Xml.XPath.XPathNamespaceScope> . Esses métodos se comportam de maneira diferente que suas contrapartes chamadas sem parâmetros. A enumeração de <xref:System.Xml.XPath.XPathNamespaceScope> tem valores de <xref:System.Xml.XPath.XPathNamespaceScope.All>, de <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>, ou de <xref:System.Xml.XPath.XPathNamespaceScope.Local>.  
  
 Aos exemplos a seguir mostram que namespaces são retornadas pelos métodos de <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> e de <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> em vários escopos em um documento XML.  
  
```xml  
<root>  
    <element1 xmlns="http://www.contoso.com" xmlns:books="http://www.contoso.com/books">  
        <element2 />  
    </element1>  
</root>  
```  
  
 A sequência de namespace (o namespace que <xref:System.Xml.XPath.XPathNavigator> é posicionado na depois de chamar o método de <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> tiver usado por uma série de chamadas para o método de <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> ) é da seguinte maneira.  
  
-   Quando localizado em `element2`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`, e `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
-   Quando localizado em `element1`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`, e `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
-   Quando localizado em `root`: `xmlns:xml="http://www.w3.org/XML/1998/namespace".`  
  
> [!NOTE]
>  Os nós de namespace de retornos de classe de <xref:System.Xml.XPath.XPathNavigator> na ordem inversa do documento. Portanto, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> move essencialmente ao último nó do namespace no escopo atual.  
  
 Aos exemplos a seguir mostram que namespaces são retornadas pelos métodos de <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> e de <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> com a enumeração de <xref:System.Xml.XPath.XPathNamespaceScope> especificada em vários escopos em um documento XML.  
  
```xml  
<root xmlns="http://www.contoso.com" xmlns:a="http://www.contoso.com/a" xmlns:b="http://www.contoso.com/b">  
    <child1 xmlns="" xmlns:a="urn:a">  
        <child2 xmlns:c="urn:c" />  
    </child1>  
</root>  
```  
  
 Quando posicionado em `child2`, a sequência de namespace (o namespace <xref:System.Xml.XPath.XPathNavigator> é posicionado na depois de chamar o método de <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> seguido por uma série de chamadas para o método de <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> ) é da seguinte maneira.  
  
-   <xref:System.Xml.XPath.XPathNamespaceScope.All>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`, `xmlns="http://www.contoso.com"`, e `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.  
  
-   <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`, e `xmlns="http://www.contoso.com"`.  
  
-   <xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.  
  
> [!NOTE]
>  Os nós de namespace de retornos de classe de <xref:System.Xml.XPath.XPathNavigator> na ordem inversa do documento. Portanto, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> move essencialmente ao último nó do namespace no escopo atual.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Processar dados XML usando o modelo de dados XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Navegação do nó usando XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 [Extrair dados XML usando XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
 [Acessando dados XML usando XPathNavigator fortemente tipados](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
