---
title: Como usar o padrão de detalhes mestre com dados XML hierárquicos
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: 0fe42d57fcaf4acee09340fdb3f5df73d7291566
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733419"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a>Como usar o padrão de detalhes mestre com dados XML hierárquicos
Este exemplo mostra como implementar o cenário de detalhes mestre com dados XML.  
  
## <a name="example"></a>Exemplo  
 Este exemplo é a versão de dados XML do exemplo discutido em [usar o padrão de detalhes mestre com dados hierárquicos](how-to-use-the-master-detail-pattern-with-hierarchical-data.md). Neste exemplo, os dados são do arquivo `League.xml`. Observe como o terceiro controle de <xref:System.Windows.Controls.ListBox> controla as alterações de seleção na segunda <xref:System.Windows.Controls.ListBox> por meio da associação à sua propriedade <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>.  
  
 [!code-xaml[MasterDetailXml#HowTo1](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.HierarchicalDataTemplate>
- [Tópicos explicativos](data-binding-how-to-topics.md)
