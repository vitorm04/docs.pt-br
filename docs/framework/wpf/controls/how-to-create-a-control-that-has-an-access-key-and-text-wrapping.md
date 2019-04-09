---
title: 'Como: Criar um controle que tenha uma chave de acesso e disposição do texto'
ms.date: 03/30/2017
helpviewer_keywords:
- access keys [WPF], control for
- controls [WPF], text wrapping
- wrapping text [WPF]
- keys [WPF], control for
- controls [WPF], access keys
- text wrapping [WPF]
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
ms.openlocfilehash: 48e439719afa2426b5d8f822c621080cdc32514e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174038"
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a><span data-ttu-id="0fdd9-102">Como: Criar um controle que tenha uma chave de acesso e disposição do texto</span><span class="sxs-lookup"><span data-stu-id="0fdd9-102">How to: Create a Control That Has an Access Key and Text Wrapping</span></span>
<span data-ttu-id="0fdd9-103">Este exemplo mostra como criar um controle que tenha uma tecla de acesso e dê suporte à disposição do texto.</span><span class="sxs-lookup"><span data-stu-id="0fdd9-103">This example shows how to create a control that has an access key and supports text wrapping.</span></span> <span data-ttu-id="0fdd9-104">O exemplo usa um <xref:System.Windows.Controls.Label> controle para ilustrar esses conceitos.</span><span class="sxs-lookup"><span data-stu-id="0fdd9-104">The example uses a <xref:System.Windows.Controls.Label> control to illustrate these concepts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fdd9-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0fdd9-105">Example</span></span>  
 **<span data-ttu-id="0fdd9-106">Adicionar disposição do texto ao seu rótulo</span><span class="sxs-lookup"><span data-stu-id="0fdd9-106">Add Text Wrapping to Your Label</span></span>**  
  
 <span data-ttu-id="0fdd9-107">O <xref:System.Windows.Controls.Label> controle não dá suporte a disposição do texto.</span><span class="sxs-lookup"><span data-stu-id="0fdd9-107">The <xref:System.Windows.Controls.Label> control does not support text wrapping.</span></span> <span data-ttu-id="0fdd9-108">Se for preciso um rótulo que se encaixe em várias linhas, será possível aninhar outro elemento que dá suporte à disposição do texto e colocar o elemento dentro do rótulo.</span><span class="sxs-lookup"><span data-stu-id="0fdd9-108">If you need a label that wraps across multiple lines, you can nest another element that does support text wrapping and put the element inside the label.</span></span> <span data-ttu-id="0fdd9-109">O exemplo a seguir mostra como usar um <xref:System.Windows.Controls.TextBlock> para criar um rótulo que envolve várias linhas de texto.</span><span class="sxs-lookup"><span data-stu-id="0fdd9-109">The following example shows how to use a <xref:System.Windows.Controls.TextBlock> to make a label that wraps several lines of text.</span></span>  
  
 [!code-xaml[LabelSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 **<span data-ttu-id="0fdd9-110">Adicionar uma chave de acesso e disposição do texto ao seu rótulo</span><span class="sxs-lookup"><span data-stu-id="0fdd9-110">Add an Access Key and Text Wrapping to Your Label</span></span>**  
  
 <span data-ttu-id="0fdd9-111">Se precisar de um <xref:System.Windows.Controls.Label> que tem uma chave de acesso (mnemonic), use o <xref:System.Windows.Controls.AccessText> elemento que está dentro do <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="0fdd9-111">If you need a <xref:System.Windows.Controls.Label> that has an access key (mnemonic), use the <xref:System.Windows.Controls.AccessText> element that is inside the <xref:System.Windows.Controls.Label>.</span></span>  
  
 <span data-ttu-id="0fdd9-112">Controles como <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, e <xref:System.Windows.Controls.GroupBox> têm modelos de controle padrão.</span><span class="sxs-lookup"><span data-stu-id="0fdd9-112">Controls such as <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, and <xref:System.Windows.Controls.GroupBox> have default control templates.</span></span> <span data-ttu-id="0fdd9-113">Esses modelos contêm um <xref:System.Windows.Controls.ContentPresenter>.</span><span class="sxs-lookup"><span data-stu-id="0fdd9-113">These templates contain a <xref:System.Windows.Controls.ContentPresenter>.</span></span> <span data-ttu-id="0fdd9-114">Uma das propriedades que podem ser definidos na <xref:System.Windows.Controls.ContentPresenter> é <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>= "true", que pode ser usada para especificar uma chave de acesso para o controle.</span><span class="sxs-lookup"><span data-stu-id="0fdd9-114">One of the properties that you can set on the <xref:System.Windows.Controls.ContentPresenter> is <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>="true", which you can use to specify an access key for the control.</span></span>  
  
 <span data-ttu-id="0fdd9-115">O exemplo a seguir mostra como criar um <xref:System.Windows.Controls.Label> que tem uma chave de acesso e oferece suporte a quebra automática de texto.</span><span class="sxs-lookup"><span data-stu-id="0fdd9-115">The following example shows how to create a <xref:System.Windows.Controls.Label> that has an access key and supports text wrapping.</span></span> <span data-ttu-id="0fdd9-116">Para habilitar a disposição do texto, o exemplo define o <xref:System.Windows.Controls.AccessText.TextWrapping%2A> propriedade e usa um caractere sublinhado para especificar a chave de acesso.</span><span class="sxs-lookup"><span data-stu-id="0fdd9-116">To enable text wrapping, the example sets the <xref:System.Windows.Controls.AccessText.TextWrapping%2A> property and uses an underline character to specify the access key.</span></span> <span data-ttu-id="0fdd9-117">(O caractere que vem imediatamente após o caractere sublinhado é a tecla de acesso.)</span><span class="sxs-lookup"><span data-stu-id="0fdd9-117">(The character that immediately follows the underline character is the access key.)</span></span>  
  
 [!code-xaml[LabelSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="0fdd9-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0fdd9-118">See also</span></span>

- [<span data-ttu-id="0fdd9-119">Como: Defina a propriedade de destino de um rótulo</span><span class="sxs-lookup"><span data-stu-id="0fdd9-119">How to: Set the Target Property of a Label</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752101(v=vs.90))
