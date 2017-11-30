---
title: Digite suporte nas classes de System.Xml
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 14821ef78f20d1ff303afacb42415e4017a92742
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="type-support-in-the-systemxml-classes"></a>Digite suporte nas classes de System.Xml
No .NET Framework versão 2,0, as classes XML principais foram aprimoradas para incluir recursos de suporte de tipo. <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, e as classes de <xref:System.Xml.XPath.XPathNavigator> incluem recursos de suporte do tipo que incluem a capacidade de conversão entre tipos esquema XML e Common Language Runtime (CLR) tipos.  
  
 No .NET Framework versão 2,0, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, e as classes de <xref:System.Xml.XPath.XPathNavigator> foram aprimorados para incluir recursos de suporte do tipo.  
  
-   O <xref:System.Xml.XmlReader> e <xref:System.Xml.XPath.XPathNavigator> classes cada incluem um **SchemaInfo** propriedade que retorna as informações de esquema em um nó.  
  
-   O **ReadContentAs** e **ReadElementContentAs** e métodos de <xref:System.Xml.XmlReader> classe ler um valor de texto e convertê-lo em um valor CLR em uma única chamada de método.  
  
-   O método de <xref:System.Xml.XmlWriter.WriteValue%2A> na classe de <xref:System.Xml.XmlWriter> converter um tipo de CLR a um tipo de esquema XML para gravar XML.  
  
-   O **ValueAs** e <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> propriedades de <xref:System.Xml.XPath.XPathNavigator> classe retornar um valor de nó e convertê-lo em um valor CLR em uma única chamada de método.  
  
> [!NOTE]
>  Na versão 1,0 do.NET Framework a classe de <xref:System.Xml.XmlConvert> foi necessária para converter entre o esquema XML e os tipos de CLR.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Mapeando tipos de dados XML para tipos CLR](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 Descreve os mapeamentos padrão de tipos de dados XML para tipos de CLR.  
  
 [Notas de implementação de suporte de tipo XML](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 Descreve alguns dos detalhes de implementação de suporte de tipo.  
  
 [Conversão de tipos de dados XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 Descreve como usar a classe de <xref:System.Xml.XmlConvert> para converter entre o esquema XML e os tipos de CLR.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Acessando dados XML usando XPathNavigator fortemente tipados](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
