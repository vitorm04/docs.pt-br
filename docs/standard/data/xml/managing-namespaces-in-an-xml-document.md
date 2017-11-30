---
title: Gerenciamento de Namespaces em um documento XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e9761afe8b56e15edba6e0319cce9a02501a6bb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="managing-namespaces-in-an-xml-document"></a>Gerenciamento de Namespaces em um documento XML
Namespaces XML e nomes de elementos e atributos em um documento XML com o URIs personalizado e predefinido. Para criar essas associações, prefixos de namespace URIs de definir e usar os prefixos para qualificar nomes de elemento e atributo nos dados XML. Namespaces evitar colisões de nome de elemento e atributo e habilitar os elementos e atributos do mesmo nome a ser tratada e validados de maneira diferente.  
  
<a name="declare"></a>   
## <a name="declaring-namespaces"></a>Declarando namespaces  
 Para declarar um namespace em um elemento, você deve usar o `xmlns:` atributo:  
  
 `xmlns:<name>=<"uri">`  
  
 onde `<name>` é o prefixo de namespace e `<"uri">` é o URI que identifica o namespace. Depois que você declarar o prefixo, você pode usá-lo para qualificar os elementos e atributos em um documento XML e associá-los com o URI de namespace. Porque o prefixo de namespace é usado em todo um documento, deve ser curto de tamanho.  
  
 Este exemplo define duas `BOOK` elementos. O primeiro elemento do elemento está qualificado pelo prefixo, `mybook`, e o segundo elemento está qualificado pelo prefixo, `bb`. Cada prefixo está associado um URI de namespace diferente:  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines">  
```  
  
 Para indicar que um elemento é uma parte de um namespace específico, adicione o prefixo de namespace para ele. Por exemplo, se um `Author` elemento pertence a `mybook` namespace, ele é declarado como `<mybook:Author>`.  
  
<a name="scope"></a>   
## <a name="declaration-scope"></a>Escopo de declaração  
 É efetivo a partir do seu ponto de declaração até o fim do elemento em que foi declarada um namespace. Neste exemplo, o namespace definido no `BOOK` elemento não se aplica a elementos fora de `BOOK` elemento, como o `Publisher` elemento:  
  
```xml  
<Author>Joe Smith</Author>  
<BOOK xmlns:book="http://www.contoso.com">  
    <title>My Wonderful Day</title>  
      <price>$3.95</price>  
</BOOK>  
<Publisher>  
    <Name>MSPress</Name>  
</Publisher>  
```  
  
 Um namespace deve ser declarado antes que ele pode ser usado, mas não é necessário que aparecem na parte superior do documento XML.  
  
 Quando você usa vários namespaces em um documento XML, você pode definir um espaço para nome como o namespace padrão para criar um documento de limpeza aparência. O namespace padrão é declarado no elemento raiz e se aplica a todos os elementos não qualificados no documento. Namespaces padrão se aplicam a elementos apenas, não para atributos.  
  
 Para usar o namespace padrão, omita o prefixo e os dois-pontos da declaração no elemento:  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
```  
  
## <a name="managing-namespaces"></a>Gerenciamento de namespaces  
 O <xref:System.Xml.XmlNamespaceManager> classe armazena uma coleção de URIs de namespace e seus prefixos e permite que você veja, adicionar e remove namespaces desta coleção. Em determinados contextos, essa classe é necessária para um melhor desempenho de processamento de XML. Por exemplo, o <xref:System.Xml.Xsl.XsltContext> classe usa <xref:System.Xml.XmlNamespaceManager> para suporte ao XPath.  
  
 O Gerenciador de namespace não executa nenhuma validação nos namespaces, mas presume que namespaces e prefixos já foi verificado e estar de acordo com o [Namespaces W3C](http://www.w3.org/TR/REC-xml-names/) especificação.  
  
> [!NOTE]
>  [LINQ para XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) não usa <xref:System.Xml.XmlNamespaceManager> para gerenciar namespaces. Consulte [trabalhando com Namespaces XML](http://msdn.microsoft.com/library/e3003209-3234-45be-a832-47feb7927430) na documentação do LINQ para obter informações sobre como gerenciar namespaces ao usar o LINQ to XML.  
  
 Aqui estão algumas das tarefas de gerenciamento e de pesquisa podem ser executadas com o <xref:System.Xml.XmlNamespaceManager> classe. Para obter mais informações e exemplos, siga os links para a página de referência para cada método ou propriedade.  
  
|Para|Use|  
|--------|---------|  
|Adicione um namespace|Método <xref:System.Xml.XmlNamespaceManager.AddNamespace%2A>|  
|Remover um namespace|Método <xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A>|  
|Localizar o URI do namespace padrão|Propriedade <xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A>|  
|Localizar o URI para um prefixo de namespace|Método <xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A>|  
|Localizar o prefixo para um URI de namespace|Método <xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A>|  
|Obter uma lista de namespaces do nó atual|Método <xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A>|  
|Definir o escopo de um namespace|Métodos <xref:System.Xml.XmlNamespaceManager.PushScope%2A> e <xref:System.Xml.XmlNamespaceManager.PopScope%2A>|  
|Verifique se um prefixo é definido no escopo atual|Método <xref:System.Xml.XmlNamespaceManager.HasNamespace%2A>|  
|Obter a tabela de nome usada para pesquisar URIs e prefixos|Propriedade <xref:System.Xml.XmlNamespaceManager.NameTable%2A>|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.XmlNamespaceManager>  
 [Documentos e dados XML](../../../../docs/standard/data/xml/index.md)
