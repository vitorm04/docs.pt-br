---
title: XML Document Object Model (DOM)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5e52844-4820-47c0-a61d-de2da33e9f54
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ff91e929876ceec8512e962b88795b6a8a29f3d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-document-object-model-dom"></a>XML Document Object Model (DOM)
A classe do DOM (Document Object Model) XML é uma representação na memória de um documento XML. O DOM permite que você leia, manipule e modifique programaticamente um documento XML. O **XmlReader** classe também lê o XML; no entanto, ele fornece acesso de não armazenado em cache, somente encaminhamento, somente leitura. Isso significa que não há nenhum recursos para editar os valores de um atributo ou conteúdo de um elemento ou a capacidade de inserir e remover nós com o **XmlReader**. A edição é a função primária do DOM. É a maneira comum e estruturada como os dados XML são representados na memória, embora os dados XML reais sejam armazenados de uma forma linear quando em um arquivo ou ao vir de outro objeto. Os seguintes são dados XML.  
  
## <a name="input"></a>Entrada  
  
```xml  
<?xml version="1.0"?>  
  <books>  
    <book>  
        <author>Carson</author>  
        <price format="dollar">31.95</price>  
        <pubdate>05/01/2001</pubdate>  
    </book>  
    <pubinfo>  
        <publisher>MSPress</publisher>  
        <state>WA</state>  
    </pubinfo>  
  </books>   
```  
  
 A ilustração a seguir mostra como a memória é estruturada quando esses dados XML são lidos na estrutura DOM.  
  
 ![Estrutura do documento XML](../../../../docs/standard/data/xml/media/xml-to-domtree.gif "XML_To_DOMTree")  
Estrutura de documento XML  
  
 Dentro da estrutura do documento XML, cada círculo nesta ilustração representa um nó, que é chamado um **XmlNode** objeto. O **XmlNode** objeto é o objeto básico na árvore DOM. O **XmlDocument** classe que estende o **XmlNode**, oferece suporte a métodos para executar operações no documento como um todo (por exemplo, carregá-la na memória ou salvar o XML em um arquivo. Além disso, **XmlDocument** fornece um meio para exibir e manipular os nós no documento XML inteiro. Ambos **XmlNode** e **XmlDocument** tem aprimoramentos de desempenho e usabilidade e ter métodos e propriedades para:  
  
-   Acessar e modificar nós específicos para o DOM, como nós de elemento, nós de referência de entidade e assim por diante.  
  
-   Recuperar nós inteiros, além das informações que o nó contém, como texto em um nó de elemento.  
  
    > [!NOTE]
    >  Se um aplicativo não exigir a estrutura ou editar recursos fornecidos pelo DOM, o **XmlReader** e **XmlWriter** classes fornecem acesso de fluxo não armazenado em cache, somente de encaminhamento para XML. Para obter mais informações, consulte <xref:System.Xml.XmlReader> e <xref:System.Xml.XmlWriter>.  
  
 **Nó** objetos têm um conjunto de métodos e propriedades, assim como características básicas e bem definidas. Algumas dessas características são:  
  
-   Os nós possuem um único nó pai - um nó pai que está um nó diretamente acima deles. Os únicos nós que não possuem um pai são a raiz do documento, pois são os nós de nível superior e contêm o próprio documento e fragmentos do documento.  
  
-   A maioria dos nós pode possuir vários nós filho, que são nós diretamente abaixo deles. A seguir está uma lista de tipos de nós que podem possuir nós filho.  
  
    -   **Documento**  
  
    -   **DocumentFragment**  
  
    -   **EntityReference**  
  
    -   **Elemento**  
  
    -   **Atributo**  
  
     O **XmlDeclaration**, **notação**, **entidade**, **CDATASection**, **texto**,  **Comentário**, **instrução de processamento**, e **DocumentType** nós não tem nós filhos.  
  
-   Nós que estão no mesmo nível, representado no diagrama, o **catálogo** e **pubinfo** nós, são irmãos.  
  
 Uma característica do DOM é como ele lida com atributos. Os atributos não são nós que fazem parte de relações de pai, filho e irmão. Os atributos são considerados uma propriedade do nó do elemento e são compostos de um par nome/valor. Por exemplo, se você tiver dados XML consistindo em `format="dollar` associado ao elemento `price`, a palavra `format` será o nome, e o valor do atributo `format` será `dollar`. Para recuperar o `format="dollar"` atributo do **preço** nó, você chama o **GetAttribute** método quando o cursor está localizado no `price` nó de elemento. Para obter mais informações, consulte [acessando atributos no DOM](../../../../docs/standard/data/xml/accessing-attributes-in-the-dom.md).  
  
 À medida que o XML é lido na memória, os nós são criados. No entanto, nem todos os nós são do mesmo tipo. Um elemento em XML tem regras e sintaxe diferentes de uma instrução de processamento. Portanto, como vários dados são lidos, um tipo é atribuído a cada nó. Esse tipo de nó determina as características e a funcionalidade do nó.  
  
 Para obter mais informações sobre os tipos de nós gerados na memória, consulte [tipos de nós XML](../../../../docs/standard/data/xml/types-of-xml-nodes.md). Para obter mais informações sobre os objetos criados na árvore de nós, consulte [mapeando a hierarquia de objetos para dados XML](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).  
  
 A Microsoft estendeu as APIs que estão disponíveis no Nível 1 e no Nível 2 do DOM do W3C (World Wide Web Consortium) para facilitar o trabalho com um documento XML. Para dar suporte total aos padrões do W3C, as classes, métodos e propriedades adicionais aumentam a funcionalidade além daquilo que pode ser feito com o DOM XML do W3C. As novas classes permitem que você acesse dados relacionais, oferecendo métodos para sincronização com dados ADO.NET, expondo, simultaneamente, os dados como XML. Para obter mais informações, consulte [sincronizando um conjunto de dados com um XmlDataDocument](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).  
  
 O DOM é mais útil para ler dados XML na memória para alterar sua estrutura, para adicionar ou remover nós ou para modificar os dados mantidos por um nó, como no texto contido por um elemento. No entanto, estão disponíveis outras classes que são mais rápidas do que o DOM em outros cenários. Para acesso rápido não armazenado em cache, somente de encaminhamento de fluxo para XML, use o **XmlReader** e **XmlWriter**. Se você precisar de acesso aleatório com um modelo de cursor e **XPath**, use o **XPathNavigator** classe.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de nós XML](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
 [Mapeando a hierarquia de objetos para dados XML](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)
