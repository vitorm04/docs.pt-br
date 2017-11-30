---
title: "Instruções passo a passo: copiando e colando um controle ElementHost nos Windows Forms separados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 65882925c6fbe3e9b393b139a937bc9a1f95ed04
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-copying-and-pasting-an-elementhost-control-into-separate-windows-forms"></a><span data-ttu-id="056ce-102">Instruções passo a passo: copiando e colando um controle ElementHost nos Windows Forms separados</span><span class="sxs-lookup"><span data-stu-id="056ce-102">Walkthrough: Copying and Pasting an ElementHost Control into Separate Windows Forms</span></span>
<span data-ttu-id="056ce-103">Este passo a passo mostra como copiar um controle WPF (Windows Presentation Foundation) de um formulário do Windows para outro.</span><span class="sxs-lookup"><span data-stu-id="056ce-103">This walkthrough shows you how to copy a Windows Presentation Foundation (WPF) control from one Windows Form to another.</span></span>  
  
 <span data-ttu-id="056ce-104">Nesta instrução passo a passo, as seguintes tarefas serão executadas:</span><span class="sxs-lookup"><span data-stu-id="056ce-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="056ce-105">Crie o projeto.</span><span class="sxs-lookup"><span data-stu-id="056ce-105">Create the project.</span></span>  
  
-   <span data-ttu-id="056ce-106">Copie um controle WPF.</span><span class="sxs-lookup"><span data-stu-id="056ce-106">Copy a WPF Control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="056ce-107">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="056ce-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="056ce-108">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="056ce-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="056ce-109">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="056ce-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="056ce-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="056ce-110">Prerequisites</span></span>  
 <span data-ttu-id="056ce-111">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="056ce-111">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="056ce-112">.</span><span class="sxs-lookup"><span data-stu-id="056ce-112">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="056ce-113">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="056ce-113">Creating the Project</span></span>  
 <span data-ttu-id="056ce-114">A primeira etapa é criar o projeto dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="056ce-114">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="056ce-115">Ao hospedar conteúdo do WPF, haverá suporte apenas para projetos em C# e Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="056ce-115">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="056ce-116">Para criar o projeto</span><span class="sxs-lookup"><span data-stu-id="056ce-116">To create the project</span></span>  
  
-   <span data-ttu-id="056ce-117">Crie um novo projeto de Aplicativo dos Windows Forms no Visual Basic ou Visual C# chamado `CopyElementHost`.</span><span class="sxs-lookup"><span data-stu-id="056ce-117">Create a new Windows Forms Application project in Visual Basic or Visual C# named `CopyElementHost`.</span></span>  
  
## <a name="copying-a-wpf-control"></a><span data-ttu-id="056ce-118">Copiando um controle WPF</span><span class="sxs-lookup"><span data-stu-id="056ce-118">Copying a WPF Control</span></span>  
 <span data-ttu-id="056ce-119">Depois de adicionar um controle WPF ao projeto, você pode copiar para outros formulários no projeto.</span><span class="sxs-lookup"><span data-stu-id="056ce-119">After you add a WPF control to the project, you can copy it to other forms in the project.</span></span>  
  
#### <a name="to-copy-a-wpf-control"></a><span data-ttu-id="056ce-120">Para copiar um controle WPF</span><span class="sxs-lookup"><span data-stu-id="056ce-120">To copy a WPF control</span></span>  
  
1.  <span data-ttu-id="056ce-121">Adicione um novo WPF <xref:System.Windows.Controls.UserControl> projeto à solução.</span><span class="sxs-lookup"><span data-stu-id="056ce-121">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="056ce-122">Use o nome padrão do tipo de controle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="056ce-122">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="056ce-123">Para obter mais informações, consulte [Instruções passo a passo: como criar novo conteúdo WPF nos Windows Forms em tempo de design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="056ce-123">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="056ce-124">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="056ce-124">Build the project.</span></span>  
  
3.  <span data-ttu-id="056ce-125">Abra `Form1` no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="056ce-125">Open `Form1` in the Windows Forms Designer.</span></span>  
  
4.  <span data-ttu-id="056ce-126">Da **Caixa de Ferramentas**, arraste uma instância de `UserControl1` para o formulário.</span><span class="sxs-lookup"><span data-stu-id="056ce-126">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>  
  
     <span data-ttu-id="056ce-127">Uma instância de `UserControl1` está hospedada em um novo <xref:System.Windows.Forms.Integration.ElementHost> controle chamado `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="056ce-127">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
5.  <span data-ttu-id="056ce-128">Com `elementHost1` selecionado, pressione CTRL+C para copiá-lo para a área de transferência.</span><span class="sxs-lookup"><span data-stu-id="056ce-128">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>  
  
6.  <span data-ttu-id="056ce-129">Adicione um novo formulário do Windows ao projeto.</span><span class="sxs-lookup"><span data-stu-id="056ce-129">Add a new Windows Form to the project.</span></span> <span data-ttu-id="056ce-130">Use o nome padrão do tipo de formulário, `Form2`.</span><span class="sxs-lookup"><span data-stu-id="056ce-130">Use the default name for the form type, `Form2`.</span></span>  
  
7.  <span data-ttu-id="056ce-131">Com `Form2` aberto no Designer de Formulários do Windows, pressione CTRL+V para colar uma cópia do `elementHost1` no formulário.</span><span class="sxs-lookup"><span data-stu-id="056ce-131">With `Form2` open in the Windows Forms Designer, press CTRL+V to paste a copy of `elementHost1` onto the form.</span></span>  
  
     <span data-ttu-id="056ce-132">O controle copiado também é chamado `elementHost1`, porque ele é um campo particular da classe `Form2`.</span><span class="sxs-lookup"><span data-stu-id="056ce-132">The copied control is also named `elementHost1`, because it is a private field of the `Form2` class.</span></span> <span data-ttu-id="056ce-133">Não há nenhuma colisão de nome com o `elementHost1` na classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="056ce-133">There is no name collision with the `elementHost1` in the `Form1` class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="056ce-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="056ce-134">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="056ce-135">Migração e interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="056ce-135">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="056ce-136">Usando Controles do WPF</span><span class="sxs-lookup"><span data-stu-id="056ce-136">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="056ce-137">Designer do WPF</span><span class="sxs-lookup"><span data-stu-id="056ce-137">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
