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
ms.openlocfilehash: 71385690c01d261b4ff1b495674bab377232e81d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447253"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a><span data-ttu-id="a61ad-102">Acrescentar Conteúdo a um Text Box Utilizando Automação de IU</span><span class="sxs-lookup"><span data-stu-id="a61ad-102">Add Content to a Text Box Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="a61ad-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="a61ad-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a61ad-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="a61ad-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="a61ad-105">Este tópico contém um código de exemplo que demonstra como usar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] para inserir texto em uma caixa de texto de linha única.</span><span class="sxs-lookup"><span data-stu-id="a61ad-105">This topic contains example code that demonstrates how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to insert text into a single-line text box.</span></span> <span data-ttu-id="a61ad-106">Um método alternativo é fornecido para controles de várias linhas e de Rich Text em que [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] não é aplicável.</span><span class="sxs-lookup"><span data-stu-id="a61ad-106">An alternate method is provided for multi-line and rich text controls where [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is not applicable.</span></span> <span data-ttu-id="a61ad-107">Para fins de comparação, o exemplo também demonstra como usar métodos Win32 para realizar os mesmos resultados.</span><span class="sxs-lookup"><span data-stu-id="a61ad-107">For comparison purposes, the example also demonstrates how to use Win32 methods to accomplish the same results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a61ad-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a61ad-108">Example</span></span>  
 <span data-ttu-id="a61ad-109">O exemplo a seguir percorre uma sequência de controles de texto em um aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="a61ad-109">The following example steps through a sequence of text controls in a target application.</span></span> <span data-ttu-id="a61ad-110">Cada controle de texto é testado para ver se um objeto <xref:System.Windows.Automation.ValuePattern> pode ser obtido usando o método <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>.</span><span class="sxs-lookup"><span data-stu-id="a61ad-110">Each text control is tested to see if a <xref:System.Windows.Automation.ValuePattern> object can be obtained from it using the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method.</span></span> <span data-ttu-id="a61ad-111">Se o controle de texto oferecer suporte a <xref:System.Windows.Automation.ValuePattern>, o método <xref:System.Windows.Automation.ValuePattern.SetValue%2A> será usado para inserir uma cadeia de caracteres definida pelo usuário no controle de texto.</span><span class="sxs-lookup"><span data-stu-id="a61ad-111">If the text control does support <xref:System.Windows.Automation.ValuePattern>, the <xref:System.Windows.Automation.ValuePattern.SetValue%2A> method is used to insert a user-defined string into the text control.</span></span> <span data-ttu-id="a61ad-112">Caso contrário, o método <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> será usado.</span><span class="sxs-lookup"><span data-stu-id="a61ad-112">Otherwise, the <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> method is used.</span></span>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a><span data-ttu-id="a61ad-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a61ad-113">See also</span></span>

- <span data-ttu-id="a61ad-114">[Amostra de texto de inserção de TextPattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a61ad-114">[TextPattern Insert Text Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span></span>
