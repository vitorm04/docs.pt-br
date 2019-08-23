---
title: Acrescentar Conteúdo a um Text Box Utilizando Automação de IU
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: fdc52d0b94ce500b6560b60419d409f5cbd73b55
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932645"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>Acrescentar Conteúdo a um Text Box Utilizando Automação de IU
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Este tópico contém um código de exemplo que demonstra como [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] usar o para inserir texto em uma caixa de texto de linha única. Um método alternativo é fornecido para controles de linha múltipla e Rich Text, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] onde não é aplicável. Para fins de comparação, o exemplo também demonstra como usar métodos Win32 para realizar os mesmos resultados.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir percorre uma sequência de controles de texto em um aplicativo de destino. Cada controle de texto é testado para ver se <xref:System.Windows.Automation.ValuePattern> um objeto pode ser obtido dele usando o <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> método. Se o controle de texto oferecer <xref:System.Windows.Automation.ValuePattern>suporte, <xref:System.Windows.Automation.ValuePattern.SetValue%2A> o método será usado para inserir uma cadeia de caracteres definida pelo usuário no controle de texto. Caso contrário, <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> o método será usado.  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>Consulte também

- [Amostra de texto de inserção de TextPattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))
