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
ms.openlocfilehash: 9183aecdc47d54aef26d5cdca8ea11d8398be732
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226502"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a><span data-ttu-id="f277b-102">Acrescentar Conteúdo a um Text Box Utilizando Automação de IU</span><span class="sxs-lookup"><span data-stu-id="f277b-102">Add Content to a Text Box Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="f277b-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="f277b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f277b-104">Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="f277b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="f277b-105">Este tópico contém código de exemplo que demonstra como usar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] para inserir texto em uma caixa de texto de linha única.</span><span class="sxs-lookup"><span data-stu-id="f277b-105">This topic contains example code that demonstrates how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to insert text into a single-line text box.</span></span> <span data-ttu-id="f277b-106">Um método alternativo é fornecido para controles de várias linhas e de texto rico onde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] não é aplicável.</span><span class="sxs-lookup"><span data-stu-id="f277b-106">An alternate method is provided for multi-line and rich text controls where [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is not applicable.</span></span> <span data-ttu-id="f277b-107">Para fins de comparação, o exemplo também demonstra como usar os métodos Win32 para obter os mesmos resultados.</span><span class="sxs-lookup"><span data-stu-id="f277b-107">For comparison purposes, the example also demonstrates how to use Win32 methods to accomplish the same results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f277b-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f277b-108">Example</span></span>  
 <span data-ttu-id="f277b-109">As seguintes etapas de exemplo por meio de uma sequência de controles de texto em um aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="f277b-109">The following example steps through a sequence of text controls in a target application.</span></span> <span data-ttu-id="f277b-110">Cada controle de texto é testado para ver se um <xref:System.Windows.Automation.ValuePattern> objeto pode ser obtido usando o <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> método.</span><span class="sxs-lookup"><span data-stu-id="f277b-110">Each text control is tested to see if a <xref:System.Windows.Automation.ValuePattern> object can be obtained from it using the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method.</span></span> <span data-ttu-id="f277b-111">Se o controle de texto der suporte à <xref:System.Windows.Automation.ValuePattern>, o <xref:System.Windows.Automation.ValuePattern.SetValue%2A> método é usado para inserir uma cadeia de caracteres definida pelo usuário no controle de texto.</span><span class="sxs-lookup"><span data-stu-id="f277b-111">If the text control does support <xref:System.Windows.Automation.ValuePattern>, the <xref:System.Windows.Automation.ValuePattern.SetValue%2A> method is used to insert a user-defined string into the text control.</span></span> <span data-ttu-id="f277b-112">Caso contrário, o <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> método é usado.</span><span class="sxs-lookup"><span data-stu-id="f277b-112">Otherwise, the <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> method is used.</span></span>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a><span data-ttu-id="f277b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f277b-113">See also</span></span>

- [<span data-ttu-id="f277b-114">Exemplo de inserção de TextPattern de texto</span><span class="sxs-lookup"><span data-stu-id="f277b-114">TextPattern Insert Text Sample</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))
