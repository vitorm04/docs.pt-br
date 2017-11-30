---
title: Como acessar o Document Object Model HTML gerenciado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- HTML DOM [Windows Forms], accessing
- managed HTML DOM [Windows Forms], accessing
ms.assetid: 40fa5cd5-1ed8-42f6-a93f-9ac01608bbeb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 284bd30a0a42f245c6b75d916853b264c7f72e6a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-access-the-managed-html-document-object-model"></a><span data-ttu-id="2d17b-102">Como acessar o Document Object Model HTML gerenciado</span><span class="sxs-lookup"><span data-stu-id="2d17b-102">How to: Access the Managed HTML Document Object Model</span></span>
<span data-ttu-id="2d17b-103">É possível acessar o Document Object Model (DOM) do HTML gerenciado a partir de dois tipos de aplicativos:</span><span class="sxs-lookup"><span data-stu-id="2d17b-103">You can access the managed HTML Document Object Model (DOM) from two types of applications:</span></span>  
  
-   <span data-ttu-id="2d17b-104">Um aplicativo do Windows Forms (.exe) que hospedou o controle <xref:System.Windows.Forms.WebBrowser> gerenciado.</span><span class="sxs-lookup"><span data-stu-id="2d17b-104">A Windows Forms application (.exe) that hosted the managed <xref:System.Windows.Forms.WebBrowser> control.</span></span> <span data-ttu-id="2d17b-105">Essas duas tecnologias se complementam entre si, com o controle <xref:System.Windows.Forms.WebBrowser> exibindo a página para o usuário e o DOM do HTML representando a estrutura lógica do documento.</span><span class="sxs-lookup"><span data-stu-id="2d17b-105">These two technologies complement one another, with the <xref:System.Windows.Forms.WebBrowser> control displaying the page to the user and the HTML DOM representing the document's logical structure.</span></span>  
  
-   <span data-ttu-id="2d17b-106">Um <xref:System.Windows.Forms.UserControl> do Windows Forms hospedado dentro do Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="2d17b-106">A Windows Forms <xref:System.Windows.Forms.UserControl> hosted within Internet Explorer.</span></span> <span data-ttu-id="2d17b-107">É possível acessar o DOM do HTML que representa a página na qual o <xref:System.Windows.Forms.UserControl> está hospedado para alterar a estrutura do documento ou abrir caixas de diálogo restritas, entre muitas outras possibilidades.</span><span class="sxs-lookup"><span data-stu-id="2d17b-107">You can access the HTML DOM representing the page on which your <xref:System.Windows.Forms.UserControl> is hosted in order to change the document's structure or open modal dialog boxes, among many other possibilities.</span></span>  
  
### <a name="to-access-dom-from-a-windows-forms-application"></a><span data-ttu-id="2d17b-108">Para acessar o DOM a partir de um aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2d17b-108">To access DOM from a Windows Forms application</span></span>  
  
1.  <span data-ttu-id="2d17b-109">Hospede um controle <xref:System.Windows.Forms.WebBrowser> dentro do aplicativo do Windows Forms e monitore pelo evento <xref:System.Windows.Forms.WebBrowser.DocumentCompleted>.</span><span class="sxs-lookup"><span data-stu-id="2d17b-109">Host a <xref:System.Windows.Forms.WebBrowser> control within your Windows Forms application and monitor for the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="2d17b-110">Para obter detalhes sobre controles de host e monitoramento de eventos, consulte [Eventos](../../../../docs/standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="2d17b-110">For details on hosting controls and monitoring for events, see [Events](../../../../docs/standard/events/index.md).</span></span>  
  
2.  <span data-ttu-id="2d17b-111">Recupere o <xref:System.Windows.Forms.HtmlDocument> da página atual acessando a propriedade <xref:System.Windows.Forms.WebBrowser.Document%2A> do controle <xref:System.Windows.Forms.WebBrowser>.</span><span class="sxs-lookup"><span data-stu-id="2d17b-111">Retrieve the <xref:System.Windows.Forms.HtmlDocument> for the current page by accessing the <xref:System.Windows.Forms.WebBrowser.Document%2A> property of the <xref:System.Windows.Forms.WebBrowser> control.</span></span>  

### <a name="to-access-dom-from-a-usercontrol-hosted-in-internet-explorer"></a><span data-ttu-id="2d17b-112">Para acessar o DOM a partir de um UserControl hospedado no Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="2d17b-112">To access DOM from a UserControl hosted in Internet Explorer</span></span>  
  
1.  <span data-ttu-id="2d17b-113">Crie sua própria classe derivada personalizada da classe <xref:System.Windows.Forms.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="2d17b-113">Create your own custom derived class of the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="2d17b-114">Para mais informações, consulte [Como criar controles compostos](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md).</span><span class="sxs-lookup"><span data-stu-id="2d17b-114">For more information, see [How to: Author Composite Controls](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md).</span></span>  
  
2.  <span data-ttu-id="2d17b-115">Coloque o seguinte código dentro do manipulador de eventos Carregar do <xref:System.Windows.Forms.UserControl>:</span><span class="sxs-lookup"><span data-stu-id="2d17b-115">Place the following code inside of your Load event handler for your <xref:System.Windows.Forms.UserControl>:</span></span>  
  
 [!code-csharp[AccessHTMLDOMControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/AccessHTMLDOMControl/cs/UserControl1.cs#1)]
 [!code-vb[AccessHTMLDOMControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/AccessHTMLDOMControl/vb/UserControl1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="2d17b-116">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="2d17b-116">Robust Programming</span></span>  
  
1.  <span data-ttu-id="2d17b-117">Ao usar o DOM através do controle <xref:System.Windows.Forms.WebBrowser>, é sempre necessário esperar até o evento <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> ocorrer antes de tentar acessar a propriedade <xref:System.Windows.Forms.WebBrowser.Document%2A> do controle <xref:System.Windows.Forms.WebBrowser>.</span><span class="sxs-lookup"><span data-stu-id="2d17b-117">When using the DOM through the <xref:System.Windows.Forms.WebBrowser> control, you should always wait until the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event occurs before attempting to access the <xref:System.Windows.Forms.WebBrowser.Document%2A> property of the <xref:System.Windows.Forms.WebBrowser> control.</span></span> <span data-ttu-id="2d17b-118">O evento <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> é elevado após o documento inteiro ser carregado, se o DOM for usado antes disso, haverá o risco de causar uma exceção de tempo de execução no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d17b-118">The <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event is raised after the entire document has loaded; if you use the DOM before then, you risk causing a run-time exception in your application.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2d17b-119">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2d17b-119">.NET Framework Security</span></span>  
  
1.  <span data-ttu-id="2d17b-120">O aplicativo ou o <xref:System.Windows.Forms.UserControl> exigirá confiança total para acessar o DOM do HTML gerenciado.</span><span class="sxs-lookup"><span data-stu-id="2d17b-120">Your application or <xref:System.Windows.Forms.UserControl> will require full trust in order to access the managed HTML DOM.</span></span> <span data-ttu-id="2d17b-121">Ao implantar um aplicativo do Windows Forms usando [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], é possível solicitar confiança total usando Implantação de Aplicativo Confiável ou Elevação de Permissões; consulte [Protegendo Aplicativos ClickOnce](/visualstudio/deployment/securing-clickonce-applications) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="2d17b-121">If you are deploying a Windows Forms application using [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], you can request full trust using either Permission Elevation or Trusted Application Deployment; see [Securing ClickOnce Applications](/visualstudio/deployment/securing-clickonce-applications) for details.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d17b-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d17b-122">See Also</span></span>  
 [<span data-ttu-id="2d17b-123">Usando o Modelo de Objeto do Documento HTML gerenciado</span><span class="sxs-lookup"><span data-stu-id="2d17b-123">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
