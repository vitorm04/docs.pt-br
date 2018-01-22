---
title: "Como criar um controle que tenha uma tecla de acesso e disposição do texto"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- access keys [WPF], control for
- controls [WPF], text wrapping
- wrapping text [WPF]
- keys [WPF], control for
- controls [WPF], access keys
- text wrapping [WPF]
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8ef62b06e97e5db22fde0085e21d7a998bfdf22
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a><span data-ttu-id="04247-102">Como criar um controle que tenha uma tecla de acesso e disposição do texto</span><span class="sxs-lookup"><span data-stu-id="04247-102">How to: Create a Control That Has an Access Key and Text Wrapping</span></span>
<span data-ttu-id="04247-103">Este exemplo mostra como criar um controle que tenha uma tecla de acesso e dê suporte à disposição do texto.</span><span class="sxs-lookup"><span data-stu-id="04247-103">This example shows how to create a control that has an access key and supports text wrapping.</span></span> <span data-ttu-id="04247-104">O exemplo usa um <xref:System.Windows.Controls.Label> controle para ilustrar esses conceitos.</span><span class="sxs-lookup"><span data-stu-id="04247-104">The example uses a <xref:System.Windows.Controls.Label> control to illustrate these concepts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04247-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="04247-105">Example</span></span>  
 <span data-ttu-id="04247-106">**Adicionar disposição do texto ao seu rótulo**</span><span class="sxs-lookup"><span data-stu-id="04247-106">**Add Text Wrapping to Your Label**</span></span>  
  
 <span data-ttu-id="04247-107">O <xref:System.Windows.Controls.Label> controle não oferece suporte a quebra automática de texto.</span><span class="sxs-lookup"><span data-stu-id="04247-107">The <xref:System.Windows.Controls.Label> control does not support text wrapping.</span></span> <span data-ttu-id="04247-108">Se for preciso um rótulo que se encaixe em várias linhas, será possível aninhar outro elemento que dá suporte à disposição do texto e colocar o elemento dentro do rótulo.</span><span class="sxs-lookup"><span data-stu-id="04247-108">If you need a label that wraps across multiple lines, you can nest another element that does support text wrapping and put the element inside the label.</span></span> <span data-ttu-id="04247-109">O exemplo a seguir mostra como usar um <xref:System.Windows.Controls.TextBlock> para criar um rótulo que quebra várias linhas de texto.</span><span class="sxs-lookup"><span data-stu-id="04247-109">The following example shows how to use a <xref:System.Windows.Controls.TextBlock> to make a label that wraps several lines of text.</span></span>  
  
 [!code-xaml[LabelSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 <span data-ttu-id="04247-110">**Adicionar uma tecla de acesso e disposição do texto ao seu rótulo**</span><span class="sxs-lookup"><span data-stu-id="04247-110">**Add an Access Key and Text Wrapping to Your Label**</span></span>  
  
 <span data-ttu-id="04247-111">Se você precisar de um <xref:System.Windows.Controls.Label> que tem uma chave de acesso (mnemônico), use o <xref:System.Windows.Controls.AccessText> elemento que está dentro do <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="04247-111">If you need a <xref:System.Windows.Controls.Label> that has an access key (mnemonic), use the <xref:System.Windows.Controls.AccessText> element that is inside the <xref:System.Windows.Controls.Label>.</span></span>  
  
 <span data-ttu-id="04247-112">Controla como <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, e <xref:System.Windows.Controls.GroupBox> ter modelos de controle padrão.</span><span class="sxs-lookup"><span data-stu-id="04247-112">Controls such as <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, and <xref:System.Windows.Controls.GroupBox> have default control templates.</span></span> <span data-ttu-id="04247-113">Esses modelos contêm um <xref:System.Windows.Controls.ContentPresenter>.</span><span class="sxs-lookup"><span data-stu-id="04247-113">These templates contain a <xref:System.Windows.Controls.ContentPresenter>.</span></span> <span data-ttu-id="04247-114">Uma das propriedades que você pode definir o <xref:System.Windows.Controls.ContentPresenter> é <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>= "true", que pode ser usada para especificar uma chave de acesso para o controle.</span><span class="sxs-lookup"><span data-stu-id="04247-114">One of the properties that you can set on the <xref:System.Windows.Controls.ContentPresenter> is <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>="true", which you can use to specify an access key for the control.</span></span>  
  
 <span data-ttu-id="04247-115">O exemplo a seguir mostra como criar um <xref:System.Windows.Controls.Label> que tem uma chave de acesso e oferece suporte a quebra automática de texto.</span><span class="sxs-lookup"><span data-stu-id="04247-115">The following example shows how to create a <xref:System.Windows.Controls.Label> that has an access key and supports text wrapping.</span></span> <span data-ttu-id="04247-116">Para habilitar a quebra de texto, o exemplo define o <xref:System.Windows.Controls.AccessText.TextWrapping%2A> propriedade e usa um caractere sublinhado para especificar a chave de acesso.</span><span class="sxs-lookup"><span data-stu-id="04247-116">To enable text wrapping, the example sets the <xref:System.Windows.Controls.AccessText.TextWrapping%2A> property and uses an underline character to specify the access key.</span></span> <span data-ttu-id="04247-117">(O caractere que vem imediatamente após o caractere sublinhado é a tecla de acesso.)</span><span class="sxs-lookup"><span data-stu-id="04247-117">(The character that immediately follows the underline character is the access key.)</span></span>  
  
 [!code-xaml[LabelSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="04247-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04247-118">See Also</span></span>  
 [<span data-ttu-id="04247-119">Como Definir a Propriedade de Destino de um Rótulo</span><span class="sxs-lookup"><span data-stu-id="04247-119">How to: Set the Target Property of a Label</span></span>](http://msdn.microsoft.com/library/b24c6977-ebcb-4855-a9bb-3fd4435af8f8)
