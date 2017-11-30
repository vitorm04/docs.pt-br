---
title: "Como obter propriedades do objeto do sistema de impressão sem reflexão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2f6015d25ee8868fe9b4c6dcf3bf145d413521e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a>Como obter propriedades do objeto do sistema de impressão sem reflexão
Usando a reflexão para relacionar as propriedades (e os tipos dessas propriedades) em um objeto pode diminuir o desempenho do aplicativo. O <xref:System.Printing.IndexedProperties> namespace fornece um meio para obter essas informações com o uso de reflexão.  
  
## <a name="example"></a>Exemplo  
 As etapas para fazer isso são da seguinte maneira.  
  
1.  Crie uma instância do tipo. No exemplo a seguir, o tipo é o <xref:System.Printing.PrintQueue> que é fornecido com [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], mas código quase idêntico deve funcionar para tipos que derivam de <xref:System.Printing.PrintSystemObject>.  
  
2.  Criar um <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> do tipo de <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>. O <xref:System.Collections.DictionaryEntry.Value%2A> propriedade de cada entrada neste dicionário é um objeto de um tipo derivado de <xref:System.Printing.IndexedProperties.PrintProperty>.  
  
3.  Enumere os membros do dicionário. Para cada um deles, faça o seguinte:  
  
4.  Cast o valor de cada entrada para <xref:System.Printing.IndexedProperties.PrintProperty> e usá-lo para criar um <xref:System.Printing.IndexedProperties.PrintProperty> objeto.  
  
5.  Obtenha o tipo do <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> de cada uma da <xref:System.Printing.IndexedProperties.PrintProperty> objeto.  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Printing.IndexedProperties.PrintProperty>  
 <xref:System.Printing.PrintSystemObject>  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [Documentos no WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Visão Geral da Impressão](../../../../docs/framework/wpf/advanced/printing-overview.md)
