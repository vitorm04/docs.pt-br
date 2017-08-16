---
title: "Preservar espaço em branco ao carregar ou analisar XML1 | Microsoft Docs"
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
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1b2ec9b5b1bbc343fde5c9527c1e4f4ad7f14796
ms.lasthandoff: 03/13/2017

---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a>Preservar espaço em branco para carregar ou ao analisar XML
Este tópico descreve como controlar o comportamento de espaço em branco de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
 Um cenário comum é ler o XML recuado, criar uma árvore XML na memória sem nenhum nó de texto de espaço em branco (isto é, não preservar espaço em branco), executar algumas operações no XML e, em seguida, salvar o XML com recuo. Quando você serializa o XML com formatação, somente os espaços em branco significativos na árvore XML são preservados. Este é o comportamento padrão para [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
 Outro cenário comum é ler e modificar XML que já foi recuado intencionalmente. Você pode não querer modificar este recuo de nenhuma forma. Para fazer isso em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], você preserva o espaço em branco quando você carregar ou analisar XML e desativa o formatação quando você serializa XML.  
  
 Este tópico descreve o comportamento de espaço em branco dos métodos que preenchem árvores XML. Para obter informações sobre o controle de espaço em branco ao serializar árvores XML, consulte [Preservar espaço em branco ao serializar](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a>Comportamento dos métodos que preenchem árvores XML  
 Os seguintes métodos, nas classes <xref:System.Xml.Linq.XElement> e <xref:System.Xml.Linq.XDocument>, preenchem uma árvore XML. Você pode preencher uma árvore XML em um arquivo, um <xref:System.IO.TextReader>, um <xref:System.Xml.XmlReader> ou uma cadeia de caracteres:  
  
-   <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>  
  
 Se o método não utilizar o <xref:System.Xml.Linq.LoadOptions> como um argumento, ele não preservará espaço em branco insignificante.  
  
 Na maioria dos casos, se o método utiliza <xref:System.Xml.Linq.LoadOptions> como um argumento, você pode, opcionalmente, preservar o espaço em branco insignificante como nós de texto na árvore XML. No entanto, se o método estiver carregando XML de um <xref:System.Xml.XmlReader>, o <xref:System.Xml.XmlReader> determinará se o espaço em branco será preservado ou não. Configuração <xref:System.Xml.Linq.LoadOptions> não terá nenhum efeito.  
  
 Com esses métodos, se o espaço em branco for preservado, o espaço em branco insignificante será inserido na árvore XML como nós <xref:System.Xml.Linq.XText>. Se o espaço em branco não é preservada, os nós de texto não são inseridos.  
  
 Você pode criar uma árvore XML usando um <xref:System.Xml.XmlWriter>. Os nós que são gravados no <xref:System.Xml.XmlWriter> são preenchidos na árvore. No entanto, quando você cria uma árvore XML usando esse método, todos os nós são mantidos, independentemente se o nó é o espaço em branco ou não, ou se o espaço em branco é significativo ou não.  
  
## <a name="see-also"></a>Consulte também  
 [Analisando XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
