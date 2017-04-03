---
title: "Conteúdo válido de objetos XElement e XDocument 3 | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
caps.latest.revision: 5
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3db6b15d2b95016db0814f202143ec198425e2ad
ms.lasthandoff: 03/13/2017

---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a>Conteúdo válido de objetos XElement e XDocument
Este tópico descreve os argumentos válidos que podem ser passados para os construtores e os métodos que você usa para adicionar conteúdo a elementos e documentos.  
  
## <a name="valid-content"></a>Conteúdo válido  
 As consultas geralmente avaliam para <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> ou <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XAttribute>. Você pode passar coleções de objetos <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute> para o construtor <xref:System.Xml.Linq.XElement>. Portanto, é conveniente passar os resultados de uma consulta como conteúdo em métodos e os construtores que você usa para popular árvores XML.  
  
 Ao adicionar conteúdo simples, vários tipos podem ser passados para esse método. Os tipos válidos incluem:  
  
-   <xref:System.String>  
  
-   <xref:System.Double>  
  
-   <xref:System.Single>  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Boolean>  
  
-   <xref:System.DateTime>  
  
-   <xref:System.TimeSpan>  
  
-   <xref:System.DateTimeOffset>  
  
-   Qualquer tipo que implemente `Object.ToString`.  
  
-   Qualquer tipo que implementa <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Ao adicionar conteúdo complexo, vários tipos podem ser passados para esse método:  
  
-   <xref:System.Xml.Linq.XObject>  
  
-   <xref:System.Xml.Linq.XNode>  
  
-   <xref:System.Xml.Linq.XAttribute>  
  
-   Qualquer tipo que implementa <xref:System.Collections.Generic.IEnumerable%601>  
  
 Se um objeto implementar <xref:System.Collections.Generic.IEnumerable%601>, a coleção no objeto será enumerada e todos os itens da coleção serão adicionados. Se a coleção contiver objetos <xref:System.Xml.Linq.XNode> ou <xref:System.Xml.Linq.XAttribute>, cada item da coleção será adicionado separadamente. Se a coleção contiver texto (ou objetos que são convertidos em texto), o texto da coleção será concatenado e adicionado como um único nó de texto.  
  
 Se o conteúdo for `null`, nada será adicionado. Ao passar itens de um coleção, a coleção pode ser `null`. Um item `null` na coleção não tem nenhum efeito na árvore.  
  
 Um atributo adicionado deve ter um nome exclusivo dentro do elemento que o contém.  
  
 Ao adicionar objetos <xref:System.Xml.Linq.XNode> ou <xref:System.Xml.Linq.XAttribute>, se o novo conteúdo não tiver pai, os objetos serão simplesmente anexados à árvore XML. Se o novo conteúdo já tiver um pai e fizer parte de outra árvore XML, o novo conteúdo será clonado, e o conteúdo recém-clonado será anexado à árvore XML.  
  
## <a name="valid-content-for-documents"></a>Conteúdo válido para documentos  
 Atributos e conteúdo simples não podem ser adicionados a um documento.  
  
 Não há muitos cenários que exijam a criação de um <xref:System.Xml.Linq.XDocument>. Em vez disso, você normalmente pode criar suas árvores XML com um nó raiz de <xref:System.Xml.Linq.XElement>. A menos que você tenha um requisito específico para criar um documento (por exemplo, porque você precisa criar instruções de processamento e comentários no nível superior ou precisa dar suporte a tipos de documentos), geralmente é mais conveniente usar <xref:System.Xml.Linq.XElement> como o nó raiz.  
  
 O conteúdo válido de um documento inclui o seguinte:  
  
-   Zero ou um objetos <xref:System.Xml.Linq.XDocumentType>. Os tipos de documento devem vir antes do elemento.  
  
-   Zero ou um elemento.  
  
-   Zero ou mais comentários.  
  
-   Zero ou mais instruções de processamento.  
  
-   Zero ou mais nós de texto que contêm somente espaço em branco.  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a>Construtores e funções que permitem adicionar conteúdo  
 Os seguintes métodos permitem que você adicione conteúdo filho a um <xref:System.Xml.Linq.XElement> ou um <xref:System.Xml.Linq.XDocument>:  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|Constrói um <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|Constrói um <xref:System.Xml.Linq.XDocument>.|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Adiciona ao final do conteúdo filho do <xref:System.Xml.Linq.XElement> ou do <xref:System.Xml.Linq.XDocument>.|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Adiciona conteúdo após o <xref:System.Xml.Linq.XNode>.|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Adiciona conteúdo antes do <xref:System.Xml.Linq.XNode>.|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Adiciona conteúdo no início do conteúdo filho do <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|Substitui todo o conteúdo (nós filho e atributos) de um <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|Substitui os atributos de um <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|Substitui os nós filho pelo novo conteúdo.|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|Substitui um nó pelo novo conteúdo.|  
  
## <a name="see-also"></a>Consulte também  
 [Criando árvores XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
